# Google Maps API Setup Guide for Flutter CourtVoice

## Step 1: Get Google Maps API Key

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Select your project `courtvoice-kitahack` (or create new project)
3. Click **"APIs & Services"** → **"Credentials"**
4. Click **"+ CREATE CREDENTIALS"** → **"API Key"**
5. Copy the API key (e.g., `AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`)

## Step 2: Enable Required APIs

In Google Cloud Console, go to **"APIs & Services"** → **"Library"**:

1. Search and enable: **"Maps SDK for Android"**
2. Search and enable: **"Maps SDK for iOS"** (if testing on iOS)
3. Search and enable: **"Places API"** (optional, for future features)

## Step 3: Configure Android

### Add API Key to Android Manifest

Edit: `android/app/src/main/AndroidManifest.xml`

Add this inside the `<application>` tag:

```xml
<application>
    <!-- Add Google Maps API Key -->
    <meta-data
        android:name="com.google.android.geo.API_KEY"
        android:value="YOUR_GOOGLE_MAPS_API_KEY_HERE"/>
    
    <!-- Existing code... -->
</application>
```

**Replace `YOUR_GOOGLE_MAPS_API_KEY_HERE` with your actual API key!**

### Full AndroidManifest.xml Example:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android">
    <!-- Permissions -->
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>

    <application
        android:label="flutter_courtvoice"
        android:name="${applicationName}"
        android:icon="@mipmap/ic_launcher">
        
        <!-- Google Maps API Key -->
        <meta-data
            android:name="com.google.android.geo.API_KEY"
            android:value="YOUR_API_KEY_HERE"/>
        
        <activity
            android:name=".MainActivity"
            ...>
        </activity>
    </application>
</manifest>
```

## Step 4: Configure iOS (Optional - for iOS testing)

Edit: `ios/Runner/AppDelegate.swift`

Add at the top:
```swift
import GoogleMaps
```

Add in `application(_ :didFinishLaunchingWithOptions:)`:
```swift
GMSServices.provideAPIKey("YOUR_GOOGLE_MAPS_API_KEY_HERE")
```

## Step 5: Location Permissions

### Android

Already configured in your `AndroidManifest.xml`:
- `ACCESS_FINE_LOCATION`
- `ACCESS_COARSE_LOCATION`

### iOS

If testing on iOS, edit `ios/Runner/Info.plist`:

```xml
<key>NSLocationWhenInUseUsageDescription</key>
<string>This app needs your location to show nearby courts</string>
<key>NSLocationAlwaysUsageDescription</key>
<string>This app needs your location to show nearby courts</string>
```

## Step 6: Test the Map

1. **Add your API key** to `android/app/src/main/AndroidManifest.xml`
2. **Rebuild the app**:
   ```bash
   flutter clean
   flutter pub get
   flutter run
   ```
3. **Navigate** to the Map screen in your app
4. **Grant location permissions** when prompted
5. You should see:
   - Google Map with your location (blue marker)
   - Malaysian courts marked in red
   - Court list at the bottom

## Troubleshooting

### Map shows gray screen
- Check if API key is correct in AndroidManifest.xml
- Make sure "Maps SDK for Android" is enabled in Google Cloud Console
- Rebuild the app after adding API key

### "Authorization failure" error
- Your API key might be restricted
- Go to Google Cloud Console → Credentials
- Edit your API key → Set "Application restrictions" to "None" (for testing)
- Or add your app's package name and SHA-1 fingerprint

### Location not working
- Make sure location services are enabled on your device
- Grant location permissions when app requests them
- Check if `ACCESS_FINE_LOCATION` permission is in AndroidManifest.xml

###  Court locations not showing
- Courts are automatically added when map loads
- Check console for any errors
- Make sure markers array is populated in code

## Current Features

✅ **Shows your current location** (blue marker)
✅ **Shows 6 major Malaysian courts** (red markers):
   - Federal Court of Malaysia, Putrajaya
   - High Court Kuala Lumpur
   - Shah Alam High Court 
   - Ipoh High Court
   - Penang High Court
   - Johor Bahru High Court

✅ **Interactive court list** at bottom (tap to zoom to court)
✅ **My Location button** to center map on your position
✅ **Zoom and pan** controls

## API Key Security (Production)

For production apps, restrict your API key:

1. Go to Google Cloud Console → Credentials
2. Edit your API key
3. Under "Application restrictions":
   - Select "Android apps"
   - Add your package name: `com.example.flutter_courtvoice`
   - Add your SHA-1 fingerprint (get with `keytool -list -v -keystore ~/.android/debug.keystore`)

## Cost Information

- Google Maps SDK for Android: **FREE** up to 25,000 map loads per day
- Your usage should be well within the free tier
- Monitor usage at: https://console.cloud.google.com/apis/dashboard

---

**Need Help?**  
Check the [official Flutter Google Maps documentation](https://pub.dev/packages/google_maps_flutter)
