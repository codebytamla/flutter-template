# Detailed Setup Guide

This guide provides step-by-step instructions for setting up this Flutter Firebase template for your own project.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Firebase Project Creation](#firebase-project-creation)
3. [Enable Google Sign-In](#enable-google-sign-in)
4. [Add iOS App to Firebase](#add-ios-app-to-firebase)
5. [Configure Environment Variables](#configure-environment-variables)
6. [Update iOS Configuration](#update-ios-configuration)
7. [Customize Your App](#customize-your-app)
8. [Verification](#verification)
9. [Troubleshooting](#troubleshooting)

## Prerequisites

Before you begin, ensure you have:

- [Flutter SDK](https://docs.flutter.dev/get-started/install) installed (version 3.9.2 or higher)
- [Xcode](https://developer.apple.com/xcode/) (for iOS development)
- [CocoaPods](https://cocoapods.org/) installed
- A Google account for Firebase
- Basic knowledge of Flutter and Firebase

Check your Flutter installation:

```bash
flutter doctor
```

## Firebase Project Creation

### Step 1: Create a New Firebase Project

1. Visit [Firebase Console](https://console.firebase.google.com/)
2. Click **Add project** or **Create a project**
3. Enter your project name (e.g., "My App")
4. Click **Continue**
5. (Optional) Disable Google Analytics or configure it
6. Click **Create project**
7. Wait for the project to be created
8. Click **Continue** when ready

## Enable Google Sign-In

### Step 2: Enable Authentication

1. In your Firebase Console, select your project
2. Click **Build** in the left sidebar
3. Click **Authentication**
4. Click **Get started**
5. Click on the **Sign-in method** tab
6. Find **Google** in the list of providers
7. Click on **Google**
8. Toggle **Enable** to ON
9. Select a **Project support email** from the dropdown
10. Click **Save**

## Add iOS App to Firebase

### Step 3: Register Your iOS App

1. In Firebase Console, click the **Project Overview** (house icon)
2. Click the **iOS** icon to add an iOS app
3. **iOS bundle ID**: Enter your app's bundle ID
   - Format: `com.yourcompany.yourapp`
   - Example: `com.mycompany.myflutterapp`
   - **Important**: Remember this, you'll need it later
4. **App nickname** (optional): Give it a friendly name
5. **App Store ID** (optional): Leave blank for now
6. Click **Register app**

### Step 4: Download Configuration File

1. Click **Download GoogleService-Info.plist**
2. Save the file somewhere safe
3. **Move** the file to your project:
   ```bash
   mv ~/Downloads/GoogleService-Info.plist /path/to/your/project/ios/Runner/
   ```
4. Click **Next** and **Continue to console**

## Configure Environment Variables

### Step 5: Create Your .env File

1. In your project root, copy the example file:
   ```bash
   cp .env.example .env
   ```

2. Open `.env` in your text editor

### Step 6: Fill in Firebase Credentials

You need to gather values from Firebase Console and your `GoogleService-Info.plist` file.

#### From Firebase Console - Project Settings

1. In Firebase Console, click the gear icon (⚙️) next to **Project Overview**
2. Click **Project settings**
3. In the **General** tab, scroll to **Your apps** section
4. Find your iOS app

**Fill in these values in your .env file:**

```bash
# From General tab
FIREBASE_PROJECT_ID=your-project-id
FIREBASE_STORAGE_BUCKET=your-project-id.firebasestorage.app
FIREBASE_MESSAGING_SENDER_ID=your-messaging-sender-id

# From your iOS app section
FIREBASE_IOS_APP_ID=1:123456789:ios:abcdef123456
FIREBASE_IOS_API_KEY=AIza...your-api-key
FIREBASE_IOS_BUNDLE_ID=com.yourcompany.yourapp
```

#### From GoogleService-Info.plist

Open your `GoogleService-Info.plist` in a text editor and find these values:

```xml
<key>CLIENT_ID</key>
<string>123456-abcdef.apps.googleusercontent.com</string>

<key>REVERSED_CLIENT_ID</key>
<string>com.googleusercontent.apps.123456-abcdef</string>
```

**Add to your .env file:**

```bash
GOOGLE_CLIENT_ID_IOS=123456-abcdef.apps.googleusercontent.com
GOOGLE_REVERSED_CLIENT_ID=com.googleusercontent.apps.123456-abcdef
```

#### Example .env File

Here's what a complete `.env` file looks like (with fake values):

```bash
# Firebase Configuration
FIREBASE_PROJECT_ID=my-flutter-app-12345
FIREBASE_MESSAGING_SENDER_ID=123456789012
FIREBASE_STORAGE_BUCKET=my-flutter-app-12345.firebasestorage.app

# Web Configuration (if needed)
FIREBASE_WEB_API_KEY=AIzaSyA1234567890abcdefGHIJKLMNOP
FIREBASE_WEB_APP_ID=1:123456789012:web:abcdef1234567890
FIREBASE_AUTH_DOMAIN=my-flutter-app-12345.firebaseapp.com

# Android Configuration (if needed)
FIREBASE_ANDROID_API_KEY=AIzaSyA1234567890abcdefGHIJKLMNOP
FIREBASE_ANDROID_APP_ID=1:123456789012:android:abcdef1234567890

# iOS Configuration
FIREBASE_IOS_API_KEY=AIzaSyB9876543210zyxwvuTSRQPONMLK
FIREBASE_IOS_APP_ID=1:123456789012:ios:fedcba0987654321
FIREBASE_IOS_BUNDLE_ID=com.mycompany.myflutterapp

# macOS Configuration (if needed)
FIREBASE_MACOS_API_KEY=AIzaSyC1234567890abcdefGHIJKLMNOP
FIREBASE_MACOS_APP_ID=1:123456789012:macos:1234567890abcdef
FIREBASE_MACOS_BUNDLE_ID=com.mycompany.myflutterapp

# Google Sign-In
GOOGLE_CLIENT_ID_IOS=123456789012-abcdefghijklmnop.apps.googleusercontent.com
GOOGLE_REVERSED_CLIENT_ID=com.googleusercontent.apps.123456789012-abcdefghijklmnop
```

## Update iOS Configuration

### Step 7: Add Reversed Client ID to Info.plist

1. Open `ios/Runner/Info.plist` in a text editor
2. Find the `CFBundleURLSchemes` section
3. It should look like this:

```xml
<key>CFBundleURLSchemes</key>
<array>
  <!-- Add your reversed client ID here -->
  <!-- Example: <string>com.googleusercontent.apps.YOUR-CLIENT-ID</string> -->
  <!-- Get this from your GoogleService-Info.plist REVERSED_CLIENT_ID -->
</array>
```

4. Replace the comments with your actual reversed client ID:

```xml
<key>CFBundleURLSchemes</key>
<array>
  <string>com.googleusercontent.apps.123456789012-abcdefghijklmnop</string>
</array>
```

### Step 8: Update Bundle Identifier in Xcode

1. Open the iOS project in Xcode:
   ```bash
   open ios/Runner.xcodeproj
   ```

2. In Xcode:
   - Click on **Runner** in the project navigator (left sidebar)
   - Select the **Runner** target
   - Go to the **Signing & Capabilities** tab
   - Under **Signing**, select your **Team**
   - Under **Bundle Identifier**, change it from `com.example.fluttertemplate` to your bundle ID
   - Example: `com.mycompany.myflutterapp`
   - **This must match** the bundle ID you used in Firebase

3. Make sure the bundle ID matches in three places:
   - Xcode (what you just changed)
   - Firebase Console (what you registered)
   - `.env` file (`FIREBASE_IOS_BUNDLE_ID`)

## Customize Your App

### Step 9: Update App Name

Change the app name in multiple files:

#### pubspec.yaml
```yaml
name: my_flutter_app  # Use snake_case
description: "My awesome Flutter app."
```

#### ios/Runner/Info.plist
```xml
<key>CFBundleDisplayName</key>
<string>My App</string>

<key>CFBundleName</key>
<string>my_flutter_app</string>
```

#### web/manifest.json
```json
{
    "name": "my_flutter_app",
    "short_name": "My App",
    "description": "My awesome Flutter app."
}
```

#### web/index.html
```html
<title>My Flutter App</title>
<meta name="apple-mobile-web-app-title" content="my_flutter_app">
<meta name="description" content="My awesome Flutter app.">
```

### Step 10: Install Dependencies

```bash
flutter pub get
```

If you're using iOS, also update pods:

```bash
cd ios
pod install
cd ..
```

## Verification

### Step 11: Verification Checklist

Before running your app, verify:

- [ ] `.env` file exists and is filled with your Firebase credentials
- [ ] `GoogleService-Info.plist` is in `ios/Runner/` directory
- [ ] Reversed client ID is added to `ios/Runner/Info.plist`
- [ ] Bundle ID matches in:
  - Xcode project
  - Firebase Console
  - `.env` file
- [ ] Google Sign-In is enabled in Firebase Console
- [ ] Dependencies installed with `flutter pub get`

### Step 12: Run the App

```bash
flutter run
```

If everything is set up correctly:
1. The app should launch without errors
2. You should see a login screen
3. Clicking "Sign in with Google" should open the Google sign-in flow
4. After signing in, you should see the home screen with your email

## Troubleshooting

### Error: "Missing .env file"

**Solution:**
```bash
cp .env.example .env
# Then fill in your Firebase credentials
```

### Error: "No such file or directory: GoogleService-Info.plist"

**Solution:**
- Download `GoogleService-Info.plist` from Firebase Console
- Move it to `ios/Runner/` directory
- Verify the path: `ios/Runner/GoogleService-Info.plist`

### Google Sign-In doesn't work

**Common causes:**

1. **Reversed Client ID not added to Info.plist**
   - Check `ios/Runner/Info.plist` has `CFBundleURLSchemes` with your reversed client ID

2. **Bundle ID mismatch**
   - Xcode bundle ID must match Firebase Console and `.env` file
   - Check all three locations

3. **Google Sign-In not enabled in Firebase**
   - Go to Firebase Console > Authentication > Sign-in method
   - Make sure Google is enabled

4. **Outdated pods**
   ```bash
   cd ios
   pod install
   cd ..
   flutter clean
   flutter pub get
   flutter run
   ```

### Build errors

**Solution:**
```bash
flutter clean
cd ios && pod install && cd ..
flutter pub get
flutter run
```

### Firebase initialization error

**Solution:**
- Double-check all values in `.env` file
- Make sure project ID, app IDs, and API keys are correct
- Verify they match what's in Firebase Console

## Next Steps

Now that your app is set up:

1. **Test the authentication flow**
   - Sign in with Google
   - Sign out
   - Test error handling

2. **Customize the UI**
   - Modify `lib/screens/login_screen.dart`
   - Update `lib/screens/home_screen.dart`
   - Change colors and branding

3. **Add more features**
   - Add more Firebase services (Firestore, Storage, etc.)
   - Implement additional authentication providers
   - Build your app's features

4. **Set up Firebase Security Rules**
   - Configure Firestore rules
   - Set up Storage rules
   - Review Authentication settings

## Need Help?

- **Template issues**: File an issue on GitHub
- **Flutter questions**: [Flutter Documentation](https://docs.flutter.dev/)
- **Firebase questions**: [Firebase Documentation](https://firebase.google.com/docs)
- **Riverpod questions**: [Riverpod Documentation](https://riverpod.dev/)

Happy coding!
