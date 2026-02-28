# 🏛️ CourtVoice (KitaHack 2026)

> **Empowering Malaysians with Free Legal Guidance in Their Language**

CourtVoice is a multilingual mobile app that helps Malaysians understand their legal rights in a simple and clear way. In Malaysia, many people face legal problems such as unfair dismissal, landlord refusing to return deposits, traffic fines, domestic violence, and consumer complaints. However, lawyers are expensive and legal documents are difficult to understand. CourtVoice helps solve this by providing free legal guidance through a smartphone app.

## What CourtVoice Does

CourtVoice allows users to:
- 💬 **Ask legal questions** using an AI Legal Assistant powered by Gemini
- 📚 **Search laws** and legal information in simple language
- 💰 **Check fine amounts** using a Fine Calculator
- 📋 **Read step-by-step court guides** for common legal situations
- 🗺️ **Find nearby courts** or legal aid centres using Google Maps

The app supports **four languages: English, Bahasa Malaysia, Mandarin, and Tamil**, so more Malaysians can use it comfortably.

---

## 📑 Table of Contents

- [Real-World Problem](#-real-world-problem)
- [SDG Alignment](#-sdg-alignment)
- [Key Features](#-key-features)
- [Technologies Used](#-technologies-used)
- [Solution Architecture](#️-solution-architecture-high-level)
- [Innovation](#-innovation)
- [Challenges Faced](#-challenges-faced)
- [User Validation](#-user-validation)
- [For End Users: How to Use CourtVoice](#-for-end-users-how-to-use-courtvoice)
- [For Developers: Setup Guide](#-for-developers-setup-guide)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌍 Real-World Problem

Many Malaysians do not understand their legal rights due to expensive legal services and difficult legal language. This affects low-income families, students, migrant workers, and underserved communities. Without clear legal knowledge, people may lose their rights or make wrong decisions. 

**Justice should be accessible to everyone—not only people who can afford a lawyer.**

### Who Benefits?
- 👨‍👩‍👧 **Low-income families** facing housing disputes or unfair treatment
- 👩‍🎓 **Students** dealing with consumer complaints or contract issues
- 🚗 **Motorists** unsure about traffic fines and penalties
- 🌏 **Migrant workers** who need legal guidance in their language
- 👴 **Elderly citizens** who find legal documents confusing

---

## 🎯 SDG Alignment

CourtVoice supports the United Nations Sustainable Development Goals (SDGs):

### SDG 16 – Peace, Justice and Strong Institutions
- Supports **Target 16.3: Equal access to justice for all.**
- CourtVoice improves access to justice by giving free, simple legal guidance.

### SDG 10 – Reduced Inequalities
- Helps reduce inequality by supporting communities that cannot afford legal help.
- Provides legal information in multiple languages, making it more inclusive.

---

## ✨ Key Features

### 1) AI Legal Assistant (Gemini)
Users type legal questions and the AI returns simple explanations based on Malaysian laws. The assistant is guided to:
- Respond in the same language as the user
- Keep explanations simple and easy to understand
- Reference Malaysian laws (Act number + Section)
- Suggest consulting a real lawyer for serious criminal cases

### 2) Legal Search
Users can search legal topics and read simplified legal information.

### 3) Fine Calculator
Users can check fine amounts and understand next steps.

### 4) Court Guide (Step-by-step)
Users can follow structured guidance on what to do in legal situations.

### 5) Court & Legal Aid Map (Google Maps)
Users can locate nearby courts and legal aid centres and view distances.

---

## 🧰 Technologies Used

### Google Developer Technologies
- **Flutter** — used to build a single app that runs on Android and iPhone.
- **Firebase Authentication** — user login and registration, keeping accounts secure. [1](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/learn/model-versions)
- **Cloud Firestore** — stores legal info, fine data, court procedures, and chat history securely in the cloud. [1](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/learn/model-versions)
- **Firebase Analytics + Google Analytics** — tracks app usage and feature engagement (active users, most-used features, language preferences).
- **Google Maps API** — shows nearby courts and legal aid centres.

### Google AI Technology
- **Gemini (Google AI Studio)** — powers the AI Legal Assistant for legal Q&A. [2](https://github.com/invertase/flutterfire_cli)[3](https://codewithandrea.com/articles/flutter-firebase-multiple-flavors-flutterfire-cli/)

---

## 🏗️ Solution Architecture (High-Level)

CourtVoice has three main parts:

1. **Flutter Frontend**
   - Screens include AI chat, legal search, fine calculator, court guides, maps, and login.

2. **Firebase Backend**
   - Authentication for user accounts
   - Firestore to store legal content, fine information, and user chat history

3. **Gemini AI Service**
   - User question → Gemini generates response → app displays answer in chat

Google Maps integrates location display for courts and legal aid centres.

---

## 🧠 Implementation Overview (How It Works)

- The app is built in Flutter to support Android and iPhone using a single codebase.
- Firebase Authentication handles user login and registration securely. [1](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/learn/model-versions)
- Firestore stores:
  - legal information
  - fine details
  - court guides
  - user chat history [1](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/learn/model-versions)
- Gemini powers the AI assistant:
  - The app sends a user’s legal question to Gemini
  - Gemini returns a simplified answer referencing Malaysian laws
  - For serious cases, the AI reminds users to consult a lawyer
- Google Maps displays nearby courts/legal aid centres and distances.

---

## 💡 Innovation

CourtVoice’s main innovation is combining:
- **AI-based legal explanation**
with
- **real Malaysian legal information**
inside one mobile app.

Instead of reading long and difficult legal documents, users can get clear answers quickly and then continue with practical tools like Fine Calculator, Court Guides, and Court Map.

---

## 🧗 Challenges Faced

During development, we faced several challenges:

1. **AI answers were too long**
   - We refined instructions to make responses shorter and simpler.

2. **Users did not understand legal terms**
   - We added simple explanations for terms like “Act” and “Section.”

3. **Simplifying complex laws without changing meaning**
   - We carefully adjusted wording for clarity while keeping accuracy.

4. **API key handling and security**
   - We needed to manage API keys safely and avoid exposing them in public repositories. The Google AI SDK warns that calling Gemini directly from a client app is recommended for prototyping only because API keys can be exposed. [4](https://linuxcommandlibrary.com/man/flutterfire)

5. **Internet connection issues**
   - We improved error handling for unstable network conditions.

---

## ✅ User Validation

We tested CourtVoice with 3 real users who were not in our team (students and working adults). They tested:
- searching legal issues
- asking the AI
- checking a fine
- finding court locations

### Three key insights from feedback
1. Some users felt the AI answers were too long.
2. Some users did not understand legal terms like “Section” or “Act.”
3. Users found the Fine Calculator and Court Map most useful.

### Three changes we made
1. Made AI answers shorter and simpler.
2. Added simple explanations for legal terms.
3. Made buttons bigger and clearer for easier use.

---

## 📈 Measuring Success

We measure success by:
- Whether users can find clear legal information within **2 minutes**
- User satisfaction (easy and helpful)
- Number of legal questions asked
- Fine Calculator usage frequency
- Court location searches

---

## 📊 Analytics (Google Technologies)

We use Firebase Analytics to track:
- number of active users
- most-used features
- preferred languages

We also use Google Analytics to measure engagement and user behaviour.

---

## 🧩 Build Steps (Development Timeline / Modules)

We built CourtVoice in modules:
1. Authentication (Firebase Auth)
2. AI Legal Assistant (Gemini integration)
3. Legal Search (Firestore legal content)
4. Fine Calculator (Firestore fine data + logic)
5. Court Guide (Firestore structured steps)
6. Court Map (Google Maps API)
7. Multi-language support (English/BM/Mandarin/Tamil)

---

## 👥 For End Users: How to Use CourtVoice

### Installation
1. Download **CourtVoice** from Google Play Store (Android) or App Store (iOS)
2. Install the app on your smartphone
3. Open the app - you'll see a splash screen followed by onboarding screens

### First Time Setup
1. **Choose Your Language**
   - On the onboarding screen, select your preferred language
   - Options: English (EN), Bahasa Malaysia (BM), 中文 (Mandarin), தமிழ் (Tamil)
   - You can change this later in Settings

2. **Enable Location (Optional)**
   - Allow location access if you want to use the Court Map feature
   - This helps you find nearby courts and legal aid centres

3. **Sign In (Optional)**
   - You can use most features without signing in
   - To save your chat history with the AI, tap "Sign In" and use Google Sign-In
   - Your legal questions will be saved privately in your account

### Using the App

#### 🤖 AI Legal Assistant
1. Tap the **"💬 AI Chat"** button from the home screen
2. Type your legal question in your preferred language
3. Examples:
   - "My landlord won't return my deposit. What can I do?"
   - "Saya kena saman, apa perlu saya buat?"
   - "交通罚单可以上诉吗？"
4. Get instant answers based on Malaysian laws
5. The AI will reference specific Acts and Sections where relevant
6. **Important**: For serious criminal cases, consult a real lawyer

#### 📚 Legal Search
1. Tap **"📚 Legal Search"** from the home screen
2. Search for legal topics like:
   - Employment law
   - Tenancy agreements
   - Consumer rights
   - Traffic offences
3. Read simplified explanations of Malaysian laws

#### 💰 Fine Calculator
1. Tap **"💰 Fine Calculator"** from the home screen
2. Select the type of offence (e.g., traffic violation, parking)
3. View the fine amount and payment options
4. Read next steps for appealing or paying the fine

#### 📋 Court Guide
1. Tap **"🏛️ Court Guide"** from the home screen
2. Choose your situation (e.g., Small Claims, Magistrate Court)
3. Follow step-by-step instructions on:
   - Documents needed
   - Where to go
   - What to expect
   - Estimated costs

#### 🗺️ Court & Legal Aid Map
1. Tap **"🗺️ Map"** from the home screen
2. Allow location access when prompted
3. View your location (blue marker) and nearby courts (red markers)
4. Tap any court marker to see its name and address
5. Scroll the list at the bottom to see all courts
6. Tap a court in the list to zoom to its location
7. Use your preferred map app to get directions

### Tips for Best Results
- ✅ Ask specific questions (include details about your situation)
- ✅ Be clear about the type of legal issue (employment, tenant, consumer, etc.)
- ✅ Mention if it's urgent or a criminal matter
- ✅ Take screenshots of important AI responses for reference
- ⚠️ Always consult a real lawyer for serious legal matters

---

## 👨‍💻 For Developers: Setup Guide

> This section is for developers who want to run CourtVoice locally or contribute to the project.

### System Requirements

Before you begin, ensure you have the following installed:

**Required Software:**
- **Operating System**: Windows 10/11, macOS 10.14+, or Linux
- **Flutter SDK**: Version 3.11.0 or higher
- **Dart SDK**: Included with Flutter
- **Android Studio** (for Android development) or **Xcode** (for iOS development)
- **Git**: For version control
- **Java JDK**: Version 17 or higher (for Android)
- **Google Chrome** (for web testing)

**Recommended:**
- **Visual Studio Code** with Flutter and Dart extensions
- **Android SDK Tools** (automatically installed with Android Studio)
- **Physical Android device** or **Android Emulator** for testing

### Prerequisites Installation

#### 1. Install Flutter SDK

**Windows:**
```powershell
# Download Flutter from https://flutter.dev/docs/get-started/install/windows
# Extract the zip file to C:\flutter
# Add to Path: C:\flutter\bin

# Verify installation
flutter doctor
```

**macOS/Linux:**
```bash
# Download Flutter from https://flutter.dev/docs/get-started/install
# Extract and add to PATH in ~/.bashrc or ~/.zshrc
export PATH="$PATH:/path/to/flutter/bin"

# Verify installation
flutter doctor
```

#### 2. Install Android Studio

1. Download from [https://developer.android.com/studio](https://developer.android.com/studio)
2. Install Android Studio
3. Open Android Studio → Settings → Plugins → Install "Flutter" plugin
4. Install "Dart" plugin
5. Go to SDK Manager and install:
   - Android SDK Platform (API 33 or higher)
   - Android SDK Build-Tools
   - Android Emulator

#### 3. Setup Android Emulator or Physical Device

**For Emulator:**
1. Open Android Studio → Device Manager
2. Click "Create Device"
3. Choose a device (e.g., Pixel 6)
4. Download a system image (API 33 recommended)
5. Create and start the emulator

**For Physical Device:**
1. Enable Developer Options on your Android phone:
   - Go to Settings → About Phone
   - Tap "Build Number" 7 times
2. Enable USB Debugging in Developer Options
3. Connect your phone to your computer via USB
4. Accept USB debugging permission on your phone

#### 4. Verify Flutter Setup

Run this command to check if everything is configured correctly:
```bash
flutter doctor -v
```

Fix any issues shown (marked with ❌). A successful setup looks like:
```
[✓] Flutter (Channel stable, 3.11.0)
[✓] Android toolchain - develop for Android devices
[✓] Chrome - develop for the web
[✓] Android Studio (version 2023.1)
[✓] VS Code (version 1.85)
[✓] Connected device (2 available)
```

---

### Project Setup

#### Step 1: Clone the Repository

```bash
git clone https://github.com/HiewYiHwa/CourtVoiceMalaysia.git
cd flutter_courtvoice
```

#### Step 2: Install Dependencies

```bash
flutter pub get
```

This will install all required packages listed in `pubspec.yaml`.

---

### Firebase Setup

CourtVoice uses Firebase for authentication and data storage. Follow these steps:

#### 1. Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click **"Add project"** or select existing project
3. Enter project name: **"CourtVoice"** (or your preferred name)
4. Disable Google Analytics (optional) or enable it
5. Click **"Create project"**

#### 2. Enable Firebase Services

**Enable Authentication:**
1. In Firebase Console, go to **Build** → **Authentication**
2. Click **"Get started"**
3. Go to **"Sign-in method"** tab
4. Enable **"Google"** sign-in provider
5. Enter support email
6. Click **"Save"**

**Enable Cloud Firestore:**
1. Go to **Build** → **Firestore Database**
2. Click **"Create database"**
3. Select **"Start in test mode"** (for development)
4. Choose a location (e.g., asia-southeast1)
5. Click **"Enable"**

**Security Rules (Important):**
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
    match /legal_content/{document=**} {
      allow read: if true;
      allow write: if false;
    }
  }
}
```

#### 3. Add Android App to Firebase

1. In Firebase Console, click the **Android icon** (⚙️ Settings → Project settings)
2. Click **"Add app"** → **Android**
3. **Android package name**: `com.apu.courtvoice`
4. **App nickname**: CourtVoice (optional)
5. **Debug signing certificate SHA-1**: 
   ```bash
   # Get your SHA-1 fingerprint
   cd android
   ./gradlew signingReport
   # Copy the SHA1 from the debug variant
   ```
   Example: `4B:BB:5D:17:82:7A:23:75:D0:3F:6E:2E:E1:0A:52:DA:F2:9B:19:CB`
6. Click **"Register app"**
7. Download `google-services.json`
8. Place it in: `android/app/google-services.json`
9. Click **"Next"** and **"Continue to console"**

#### 4. Add iOS App to Firebase (Optional)

1. Click the **iOS icon** in Firebase Console
2. **iOS bundle ID**: `com.apu.courtvoice`
3. Download `GoogleService-Info.plist`
4. Place it in: `ios/Runner/GoogleService-Info.plist`

---

### API Keys Setup

#### 1. Get Gemini API Key

1. Go to [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Click **"Create API Key"**
3. Select or create a Google Cloud project
4. Copy the API key (e.g., `AIzaSyXXXXXXXXXXXXXXXXXXXXXXXX`)

**Add to the App:**
1. Open `lib/services/gemini_service.dart`
2. Find line ~8:
   ```dart
   static const String apiKey = 'YOUR_GEMINI_API_KEY';
   ```
3. Replace `YOUR_GEMINI_API_KEY` with your actual key

**⚠️ Security Warning:**
- Never commit API keys to public repositories
- For production, use environment variables or secure key management
- The current implementation is for prototyping only

#### 2. Get Google Maps API Key

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Click **"APIs & Services"** → **"Credentials"**
3. Click **"+ CREATE CREDENTIALS"** → **"API Key"**
4. Copy the API key

**Enable Required APIs:**
1. Go to **"APIs & Services"** → **"Library"**
2. Search and enable:
   - **Maps SDK for Android**
   - **Maps SDK for iOS** (if using iOS)

**Add to Android:**
1. Open `android/app/src/main/AndroidManifest.xml`
2. Find line ~14:
   ```xml
   android:value="YOUR_GOOGLE_MAPS_API_KEY_HERE"/>
   ```
3. Replace `YOUR_GOOGLE_MAPS_API_KEY_HERE` with your actual key

**Add to iOS (Optional):**
1. Open `ios/Runner/AppDelegate.swift`
2. Add at the top:
   ```swift
   import GoogleMaps
   ```
3. Add in the `application` function:
   ```swift
   GMSServices.provideAPIKey("YOUR_GOOGLE_MAPS_API_KEY")
   ```

---

### Running the App

#### 1. Start an Emulator or Connect Device

**Check connected devices:**
```bash
flutter devices
```

You should see your emulator or physical device listed.

#### 2. Run the App

**Run on connected device/emulator:**
```bash
flutter run
```

**Run on specific device:**
```bash
flutter run -d <device-id>
```

**Run in release mode:**
```bash
flutter run --release
```

#### 3. Hot Reload

While the app is running:
- Press `r` for hot reload (fast refresh)
- Press `R` for hot restart (full restart)
- Press `q` to quit

---

### Building the App

#### Build APK (Android)

```bash
# Debug APK
flutter build apk --debug

# Release APK
flutter build apk --release

# APK location: build/app/outputs/flutter-apk/app-release.apk
```

#### Build App Bundle (Android - for Play Store)

```bash
flutter build appbundle --release

# Bundle location: build/app/outputs/bundle/release/app-release.aab
```

#### Build iOS App

```bash
flutter build ios --release
```

---

### Project Structure

```
flutter_courtvoice/
├── android/              # Android-specific code
│   └── app/
│       ├── src/main/AndroidManifest.xml
│       └── google-services.json
├── ios/                  # iOS-specific code
│   └── Runner/
│       └── GoogleService-Info.plist
├── lib/                  # Main Flutter code
│   ├── main.dart        # App entry point
│   ├── screens/         # UI screens
│   │   ├── splash_screen.dart
│   │   ├── onboarding_screen.dart
│   │   ├── home_screen.dart
│   │   ├── sign_in_screen.dart
│   │   ├── ai_chat_screen.dart
│   │   ├── legal_search_screen.dart
│   │   ├── fine_calculator_screen.dart
│   │   ├── court_guide_screen.dart
│   │   ├── map_screen.dart
│   │   ├── profile_screen.dart
│   │   └── settings_screen.dart
│   ├── services/        # Business logic
│   │   ├── auth_service.dart
│   │   ├── firestore_service.dart
│   │   └── gemini_service.dart
│   └── utils/           # Utilities
│       └── translations.dart
├── test/                # Unit tests
├── pubspec.yaml         # Dependencies
├── README.md           # This file
├── SETUP_GUIDE.md      # Additional setup instructions
└── GOOGLE_MAPS_SETUP.md # Google Maps specific setup
```

---

## 🔧 Troubleshooting

### Common Issues for End Users

#### 1. Google Sign-In Not Working
**Problem**: Button doesn't respond or shows error

**Solutions:**
- Make sure you have a Google account
- Check your internet connection
- Try signing out and signing in again
- Clear app cache: Settings → Apps → CourtVoice → Clear Cache

#### 2. Map Not Showing / Gray Screen
**Problem**: Map screen is blank or gray

**Solutions:**
- Enable location services on your device
- Grant location permission to CourtVoice
- Check internet connection
- Restart the app

#### 3. AI Not Responding
**Problem**: Chat doesn't send messages or shows error

**Solutions:**
- Check your internet connection
- Try asking a shorter question
- Restart the app
- Make sure the question is legal-related

#### 4. Language Not Changing
**Problem**: App doesn't switch language

**Solutions:**
- Go to Settings → Select language → Restart app
- Make sure you tapped "Save" or confirmed the change

#### 5. App Crashes or Freezes
**Solutions:**
- Restart your phone
- Update the app to the latest version
- Clear app data: Settings → Apps → CourtVoice → Clear Data
- Reinstall the app

---

### Common Issues for Developers

#### 1. `flutter doctor` Shows Errors

**Android toolchain not found:**
```bash
# Install Android SDK through Android Studio
# Or download command line tools from:
# https://developer.android.com/studio#command-tools
```

**Android licenses not accepted:**
```bash
flutter doctor --android-licenses
# Accept all licenses by typing 'y'
```

**Xcode not found (macOS):**
```bash
# Install Xcode from App Store
sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
sudo xcodebuild -runFirstLaunch
```

#### 2. Build Fails with "Plugin not found"

```bash
# Clean and rebuild
flutter clean
flutter pub get
flutter run
```

#### 3. Firebase Not Working

**Error: "Firebase app not initialized"**
- Make sure `google-services.json` (Android) is in `android/app/`
- Make sure `GoogleService-Info.plist` (iOS) is in `ios/Runner/`
- Run `flutter clean` and rebuild

**Error: "Failed to get document"**
- Check Firestore security rules
- Make sure user is signed in
- Check internet connection

#### 4. Google Maps Shows Blank/Gray Screen

**Missing API Key:**
- Check `AndroidManifest.xml` has the API key
- Verify the key is correct (no extra spaces)

**API not enabled:**
- Go to Google Cloud Console
- Enable "Maps SDK for Android"
- Wait a few minutes for it to activate

**Wrong package name:**
- Verify in Firebase: `com.apu.courtvoice`
- Check in `android/app/build.gradle.kts`

#### 5. Google Sign-In Not Working

**No SHA-1 fingerprint in Firebase:**
```bash
# Get your SHA-1
cd android
./gradlew signingReport
# Copy the SHA1 value
# Add it to Firebase console → Project Settings → Your Android app
```

**Wrong package name:**
- Package must be `com.apu.courtvoice`
- Check Firebase console and `build.gradle.kts`

**Google Sign-In not enabled:**
- Go to Firebase Console → Authentication → Sign-in method
- Enable "Google" provider

#### 6. Gemini API Errors

**Error: "API key not valid"**
- Check the API key in `lib/services/gemini_service.dart`
- Make sure there are no extra spaces or quotes
- Verify the key in Google AI Studio

**Error: "403 Forbidden"**
- API key may be restricted
- Check quota in Google Cloud Console
- Enable Gemini API in API Library

**Error: "Too many requests"**
- You've hit the free tier limit
- Wait a few minutes
- Consider upgrading your plan

#### 7. "Gradle build failed" Error

```bash
# Clear Gradle cache
cd android
./gradlew clean

# Or delete build folders
cd ..
flutter clean
rm -rf build/
rm -rf android/.gradle/

# Rebuild
flutter pub get
flutter run
```

#### 8. Hot Reload Not Working

```bash
# Use hot restart instead
# Press 'R' in terminal

# Or restart the app completely
flutter run
```

#### 9. Emulator Not Detected

```bash
# List available devices
flutter devices

# Start emulator manually
flutter emulators
flutter emulators --launch <emulator-id>

# Or start from Android Studio → Device Manager
```

#### 10. iOS Build Fails (macOS only)

```bash
# Update pods
cd ios
pod install --repo-update
cd ..

# Clean and rebuild
flutter clean
flutter pub get
flutter run
```

---

### Getting Help

If you're still having issues:

**For End Users:**
- Contact support: courtvoice@support.com
- Report a bug on our website
- Check FAQ section in the app

**For Developers:**
- Check [Flutter Documentation](https://docs.flutter.dev/)
- Check [Firebase Documentation](https://firebase.google.com/docs)
- Open an issue on GitHub
- Join our developer Discord/Slack

---

## 🤝 Contributing

We welcome contributions to CourtVoice! Here's how you can help:

### Ways to Contribute

1. **Report Bugs**
   - Open an issue describing the bug
   - Include steps to reproduce
   - Add screenshots if possible

2. **Suggest Features**
   - Open an issue with your idea
   - Explain the use case
   - Discuss implementation approach

3. **Improve Documentation**
   - Fix typos or unclear sections
   - Add examples
   - Translate documentation

4. **Submit Code**
   - Fork the repository
   - Create a feature branch
   - Make your changes
   - Submit a pull request

### Development Guidelines

- Follow Flutter style guide
- Write clear commit messages
- Add tests for new features
- Update documentation
- Keep code simple and maintainable

---

## 📝 License

This project was developed for **KitaHack 2026** hackathon.

**License:** MIT License (or specify your license)

```
Copyright (c) 2026 CourtVoice Team

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software...
```

---

## 📞 Contact & Support

- **Email**: company.ecovents@gmail.com
- **GitHub**: https://github.com/HiewYiHwa/CourtVoiceMalaysia
- **Hackathon**: KitaHack 2026

---

## 🙏 Acknowledgments

- **Google** for Flutter, Firebase, Gemini AI, and Google Maps
- **KitaHack 2026** organizers
- Malaysian legal resources and documentation
- Our beta testers and user feedback
- Open source community

---

## 📈 Project Status

- ✅ Core features implemented
- ✅ Multi-language support (EN, BM, CH, TA)
- ✅ Firebase integration complete
- ✅ Google Maps working
- ✅ AI assistant functional
- 🚧 Advanced legal search (in progress)
- 🚧 Push notifications (planned)
- 🚧 Offline mode (planned)

---

**Made with ❤️ for Malaysians by the CourtVoice Team**

**#KitaHack2026 #JusticeForAll #LegalTech**
