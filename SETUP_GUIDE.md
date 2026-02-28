# CourtVoice - Complete Setup Guide

Welcome to CourtVoice! This guide will help you set up all features including Firebase, Google Sign-In, Gemini AI, and Google Maps.

---

## 📋 Table of Contents

1. [Firebase Setup](#firebase-setup)
2. [Google Sign-In Setup](#google-sign-in-setup)
3. [Gemini AI Setup](#gemini-ai-setup)
4. [Google Maps Setup](#google-maps-setup)
5. [Testing the App](#testing-the-app)
6. [Troubleshooting](#troubleshooting)

---

## 🔥 Firebase Setup

### Step 1: Firebase is Already Connected!

Your app is already configured with:
- ✅ `lib/firebase_options.dart` - Firebase configuration
- ✅ `android/app/google-services.json` - Android config
- ✅ Firebase initialized in `lib/main.dart`
- ✅ Project ID: `courtvoice-kitahack`

### Step 2: Enable Firestore Database

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select project: **courtvoice-kitahack**
3. Click **"Firestore Database"** → **"Create database"**
4. Choose **"Test mode"** (for development)
5. Select region: **asia-southeast1** (or nearest)
6. Click **"Enable"**

### Step 3: Add Sample Data

Your app has **7 Firebase collections**:

#### 1. **legal_cases** - Legal case information
- Go to "Legal Search" screen
- Click ➕ button to add 3 sample cases

#### 2. **laws** - Malaysian law database
- Go to "Law Search" screen (new menu item!)
- Click ➕ button to add sample laws (Road Transport Act, Penal Code,  etc.)

#### 3. **fines** - Traffic fine calculator data
- Go to "Fine Calculator" screen
- Click ➕ button to add Malaysia traffic fines

#### 4. **procedures** - Court procedure guides
- Automatically populated when you use "Court Guide" screen

#### 5. **ai-chat** - AI chat session history
- Automatically created when you chat with AI
- Stores conversation history per user

#### 6. **users** - User profiles
- Automatically created when signing in with Google
- Stores: email, displayName, photoURL, language, createdAt

#### 7. **traffic** - Traffic offence data
- Reserved for future expansion

---

## 🔐 Google Sign-In Setup

### Step 1: Get SHA-1 Fingerprint

**For Debug Build:**
```powershell
cd android
.\gradlew signingReport
```

Look for `SHA1:` in the output (e.g., `SHA1: 1A:2B:3C:...`)

**Quick Method:**
```powershell
keytool -list -v -keystore "$env:USERPROFILE\.android\debug.keystore" -alias androiddebugkey -storepass android -keypass android
```

### Step 2: Add SHA-1 to Firebase
1. Firebase Console → Project Settings
2. Under "Your apps" → Android app
3. Click "Add fingerprint"
4. Paste your SHA-1
5. Click "Save"
6. **Download** the new `google-services.json`
7. Replace `android/app/google-services.json` with the new file

### Step 3: Test Sign-In

1. Run your app
2. Go to **Profile** screen
3. Click **"Sign In with Google"**
4. Select your Google account
5. You should see your profile picture and name!

**Current Feature:**
- ✅ Profile screen shows sign-in status
- ✅ User data saved to Firestore `users` collection
- ✅ Proper navigation - returns to profile after sign-in
- ✅ Sign-out functionality

---

## 🤖 Gemini AI Setup

### Your API Key is Already Added!

File: `lib/services/gemini_service.dart`
```dart
static const String _apiKey = 'AlzaSyCUshub3zpHYilsy4ONLvbgSgHyIgslprg';
```

### How It Works:
- ✅ **Gemini 1.5 Pro** model
- ✅ Specialized for Malaysian legal assistance
- ✅ **Chat sessions** saved to Firebase Firebase (`ai-chat` collection)
- ✅ Conversation history preserved
- ✅ Reset chat functionality
- ✅ Auto-scroll to latest message

### Test AI Chat:
1. Run app → Click **"AI Assistant"**
2. Ask: *"What is the penalty for speeding in Malaysia?"*
3. AI will respond with legal information
4. All messages saved to Firebase for history

**If you need a new API key:**
1. Go to [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Click "Create API Key"
3. Copy the key
4. Replace `_apiKey` in `lib/services/gemini_service.dart`

---

## 🗺️ Google Maps Setup

### Step 1: Get Google Maps API Key

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Select project `courtvoice-kitahack`
3. **APIs & Services** → **Credentials**
4. **+ CREATE CREDENTIALS** → **API Key**
5. Copy the API key

### Step 2: Enable Maps API

**APIs & Services** → **Library**, enable:
- ✅ Maps SDK for Android
- ✅ Places API (optional)

### Step 3: Add API Key to Android

Edit: `android/app/src/main/AndroidManifest.xml`

Add inside `<application>` tag:

```xml
<application>
    <!-- Google Maps API Key -->
    <meta-data
        android:name="com.google.android.geo.API_KEY"
        android:value="YOUR_GOOGLE_MAPS_API_KEY_HERE"/>
    
    <!-- Existing code... -->
</application>
```

**Replace `YOUR_GOOGLE_MAPS_API_KEY_HERE` with your actual key!**

### Step 4: Rebuild & Test

```powershell
flutter clean
flutter pub get
flutter run
```

**Map Features:**
- ✅ Shows your current location (blue marker)
- ✅ Shows 6 major Malaysian courts (red markers)
- ✅ Court list at bottom (tap to zoom)
- ✅ My Location button
- ✅ Interactive map with zoom/pan

**See `GOOGLE_MAPS_SETUP.md` for detailed instructions.**

---

## 🚀 Testing the App

### 1. Complete App Flow:

**Start Screen → Home → Features**

1. **Launch app** - You'll see splash screen with CourtVoice logo
2. Click **"🚀 Enter"** button (no auto-navigation)
3. **Home screen** shows 7 menu options:
   - 🔍 Legal Search
   - 📖 Law Search (NEW!)
   - 🤖 AI Assistant
   - 💰 Fine Calculator
   - 📘 Court Guide
   - 🗺️ Map
   - 👤 Profile

### 2. Test Each Feature:

#### Legal Search 🔍
- Search by keyword
- Filter by category (Traffic, Family, Criminal)
- Click + to add 3 sample cases
- Tap case to view details

#### Law Search 📖 (NEW!)
- Browse Malaysian laws (Road Transport Act, Penal Code, etc.)
- Search by keyword
- Filter by category (Traffic, Criminal, Civil, Constitutional, etc.)
- Click + to add sample laws
- Tap law to see full details, Act number, penalties

####  AI Chat 🤖
- Chat with Gemini AI about legal matters
- Sessions automatically saved to Firebase
- Reset chat button (🔄) to start new session
- Auto-scroll to latest messages

#### Fine Calculator 💰
- Select traffic offence from dropdown
- Toggle First/Repeat offence
- Adjust speed over limit (for speeding)
- **Auto-calculates** using Malaysia Road Transport Act 1987 logic
- Shows RM fine amount, legal range, Act reference
- Click + to save fines to Firebase

#### Court Guide 📘
- View Malaysian court procedures
- Multi-language support

#### Map 🗺️
- See your location and nearby courts
- 6 major Malaysian courts marked
- Tap court name to zoom to location
- My Location button to center map

#### Profile 👤
- Sign in with Google
- View profile photo and name
- Chat history, saved cases, statistics
- Sign out button

### 3. Test Multi-Language:

Go to **Settings** (⚙️ icon) → Choose language:
- 🇬🇧 English
- 🇲🇾 Bahasa Melayu
- 🇨🇳 中文 (Chinese)
- 🇮🇳 தமிழ் (Tamil)

**ALL screens translate**, including menus, buttons, content!

---

## 🛠️ Troubleshooting

### Firebase Issues

**Problem:** "No results found" in Legal Search
- Solution: Enable Firestore Database in Firebase Console
- Click + button in app to add sample data

**Problem:** AI Chat says "error occurred"
- Check Gemini API key in `lib/services/gemini_service.dart`
- Make sure API key is valid

**Problem:** Sign-in not working
- Add SHA-1 fingerprint to Firebase Console
- Download new `google-services.json`
- Rebuild app: `flutter clean` → `flutter pub get` → `flutter run`

### Google Maps Issues

**Problem:** Map shows gray screen
- Add API key to `android/app/src/main/AndroidManifest.xml`
- Enable "Maps SDK for Android" in Google Cloud Console
- Rebuild: `flutter clean` → `flutter run`

**Problem:** "Authorization failure"
- Check API key is correct
- Set API restrictions to "None" (for testing)
- Or add package name + SHA-1

**Problem:** Location not showing
- Grant location permissions when prompted
- Enable location services on device

### General Issues

**Problem:** FlutterFire CLI not recognized
- PATH is already set permanently
- Restart your terminal
- Or run: `$env:PATH += ";C:\Users\yh\AppData\Local\Pub\Cache\bin"`

**Problem:** Build errors after changes
```powershell
flutter clean
flutter pub get
flutter run
```

**Problem:** App crashes on specific screen
- Check console for error messages
- Make sure all dependencies are installed
- Verify Firebase collections are enabled

---

## ✅ Feature Checklist

### Completed Features:
- ✅ Firebase Core connected
- ✅ Cloud Firestore with 7 collections
- ✅ Google Sign-In with profile display
- ✅ Gemini AI chat with Firebase session storage
- ✅ Google Maps with Malaysian courts
- ✅ Fine calculator with Malaysia traffic law logic
- ✅ Law Search screen with Malaysian laws database
- ✅ Multi-language support (4 languages)
- ✅ Search functionality with keyword filtering
- ✅ Splash screen with Enter button (no auto-navigate)
- ✅ Profile screen with proper sign-in flow
- ✅ All screens have emoji back buttons
- ✅ Clean UI with no dropdown underlines

### Database Collections:
1. ✅ `legal_cases` - Legal search cases
2. ✅ `laws` - Malaysian law database
3. ✅ `fines` - Traffic fine data
4. ✅ `procedures` - Court procedures
5. ✅ `ai-chat` - AI chat sessions
6. ✅ `users` - User profiles
7. ✅ `traffic` - Traffic data (future)

---

## 📊 Architecture Overview

```
CourtVoice App
│
├── Screens (lib/screens/)
│   ├── splash_screen.dart - Entry point with Enter button
│   ├── home_screen.dart - Main menu (7 options)
│   ├── legal_search_screen.dart - Search legal cases
│   ├── law_search_screen.dart - Search Malaysian laws (NEW!)
│   ├── ai_chat_screen.dart - Gemini AI chat
│   ├── fine_calculator_screen.dart - Calculate Malaysia traffic fines
│   ├── court_guide_screen.dart - Court procedures
│   ├── map_screen.dart - Google Maps with courts
│   ├── profile_screen.dart - User profile & auth
│   ├── settings_screen.dart - Language settings
│   └── sign_in_screen.dart - Google Sign-In
│
├── Services (lib/services/)
│   ├── firestore_service.dart - 7 Firestore collections
│   ├── gemini_service.dart - AI chat with Gemini
│   └── auth_service.dart - Google authentication
│
├── Utils (lib/utils/)
│   └── translations.dart - 4 languages, 50+ keys
│
└── Firebase
    ├── firebase_options.dart - Auto-generated config
    ├── android/app/google-services.json
    └── Firestore Collections (7 total)
```

---

## 🎯 Key Improvements Made

1. **No Auto-Navigation** - Splash screen stays until user clicks Enter
2. **Law Search Menu** - New screen for browsing Malaysian laws
3. **Profile Sign-In Flow** - Properly updates after Google Sign-In
4. **AI Chat Sessions** - Conversations saved to Firebase `ai-chat` collection
5. **Fine Calculator Logic** - Auto-calculates using Malaysia Road Transport Act:
   - Speeding: RM300-1000 based on speed over limit
   - Repeat offences have higher fines
   - Shows Act reference and legal range
6. **Google Maps Integration** - Live map with 6 Malaysian courts
7. **Complete Firestore Integration** - All data from Firebase (no dummy data!)
8. **Multi-Language** - All 7 screens fully translated

---

## 📞 Need Help?

- **Firebase Console**: https://console.firebase.google.com/
- **Google Cloud Console**: https://console.cloud.google.com/
- **Gemini AI Studio**: https://makersuite.google.com/
- **Flutter Docs**: https://docs.flutter.dev/

**For Google Maps detailed setup, see `GOOGLE_MAPS_SETUP.md`**

---

🎉 **Your app is now fully functional with all 7 screens and Firebase integration!**
