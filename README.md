# Flutter Firebase Template

A production-ready Flutter template featuring Firebase Authentication with Google Sign-In and Riverpod state management. This template provides a solid foundation for building Flutter applications with Firebase backend services.

## Features

- **Firebase Authentication** with Google Sign-In
- **Riverpod** for state management
- **Clean Architecture** with separation of concerns (services/providers/screens)
- **Environment-based Configuration** using .env files
- **Auto-dispose Providers** for efficient memory management
- **Error Handling** and loading states
- **Material Design 3** UI

## Project Structure

```
lib/
├── services/         # External services (Firebase, APIs)
│   └── auth_service.dart
├── providers/        # Riverpod state management
│   └── auth_provider.dart
├── screens/          # UI screens
│   ├── login_screen.dart
│   └── home_screen.dart
├── firebase_options.dart  # Firebase configuration
└── main.dart              # App entry point
```

## Prerequisites

- Flutter SDK (3.9.2 or higher)
- Dart SDK
- iOS: Xcode and CocoaPods
- Android: Android Studio
- A Firebase account

## Quick Start

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd flutter-template
flutter pub get
```

### 2. Firebase Project Setup

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project
3. Enable **Google Sign-In** in Authentication > Sign-in method

### 3. Download Firebase Configuration Files

#### For iOS:
1. In Firebase Console, add an iOS app
2. Enter your iOS bundle ID (e.g., `com.yourcompany.yourapp`)
3. Download `GoogleService-Info.plist`
4. Place it in `ios/Runner/` directory

#### For Android (optional):
1. In Firebase Console, add an Android app
2. Enter your Android package name
3. Download `google-services.json`
4. Place it in `android/app/` directory

### 4. Configure Environment Variables

#### Create .env File

```bash
cp .env.example .env
```

#### Fill in Your Firebase Credentials

Open `.env` and replace the placeholder values with your actual Firebase credentials from the Firebase Console.

**Where to find these values:**

- **Project Settings** > **General**:
  - `FIREBASE_PROJECT_ID`
  - `FIREBASE_STORAGE_BUCKET`

- **Project Settings** > **Your apps** > **iOS app**:
  - `FIREBASE_IOS_APP_ID`
  - `FIREBASE_IOS_API_KEY`
  - `FIREBASE_IOS_BUNDLE_ID`

- From your `GoogleService-Info.plist`:
  - `GOOGLE_CLIENT_ID_IOS` (CLIENT_ID)
  - `GOOGLE_REVERSED_CLIENT_ID` (REVERSED_CLIENT_ID)

### 5. Update iOS Configuration

#### Add Reversed Client ID

Open `ios/Runner/Info.plist` and find the `CFBundleURLSchemes` section. Add your reversed client ID:

```xml
<key>CFBundleURLSchemes</key>
<array>
  <string>com.googleusercontent.apps.YOUR-CLIENT-ID</string>
</array>
```

#### Update Bundle Identifier

1. Open `ios/Runner.xcodeproj` in Xcode
2. Select the **Runner** target
3. Under **Signing & Capabilities**, select your team
4. Change **Bundle Identifier** to match your Firebase iOS app
5. Update the same Bundle Identifier in your `.env` file (`FIREBASE_IOS_BUNDLE_ID`)

### 6. Customize Your App

#### Update App Name

- `pubspec.yaml`: Change the `name` field
- `ios/Runner/Info.plist`: Update `CFBundleDisplayName`
- `web/manifest.json`: Update `name` and `short_name`
- `web/index.html`: Update `<title>` tag

### 7. Run the App

```bash
flutter run
```

## Architecture

### Services Layer

Services handle external dependencies and business logic:

```dart
// lib/services/auth_service.dart
class AuthService {
  Future<UserCredential?> signInWithGoogle() async { ... }
  Future<void> signOut() async { ... }
}
```

### Providers Layer

Providers manage application state with Riverpod:

```dart
// lib/providers/auth_provider.dart
final authStateProvider = StreamProvider<User?>(...);
final authProvider = StateNotifierProvider<AuthNotifier, AuthState>(...);
```

### Screens Layer

Screens consume providers and display UI:

```dart
// lib/screens/login_screen.dart
class LoginScreen extends ConsumerWidget {
  Widget build(BuildContext context, WidgetRef ref) {
    final authState = ref.watch(authStateProvider);
    // ...
  }
}
```

## Development

### Adding New Features

1. **Create a Service** in `lib/services/` for business logic
2. **Create Providers** in `lib/providers/` for state management
3. **Create Screens** in `lib/screens/` to consume the providers

### State Management with Riverpod

This template uses Riverpod for reactive state management. Key providers:

- `authStateProvider`: Stream of Firebase auth state changes
- `currentUserProvider`: Current authenticated user
- `authProvider`: StateNotifier for sign-in/sign-out actions

## Building for Production

### iOS

```bash
flutter build ios --release
```

### Android

```bash
flutter build apk --release
# or for Play Store
flutter build appbundle --release
```

### Web

```bash
flutter build web --release
```

## Troubleshooting

### "Missing environment variables" error

- Ensure you've created a `.env` file from `.env.example`
- Fill in all required Firebase credentials
- Run `flutter pub get` after creating `.env`

### Google Sign-In not working on iOS

1. Verify `GoogleService-Info.plist` is in `ios/Runner/`
2. Check `CFBundleURLSchemes` in `Info.plist` contains your reversed client ID
3. Ensure Bundle ID matches across:
   - Xcode project settings
   - Firebase Console
   - `.env` file

### Firebase initialization error

- Double-check all environment variables in `.env`
- Ensure Firebase project ID and app IDs are correct
- Verify `GoogleService-Info.plist` matches your Firebase project

### Build errors after changing bundle ID

```bash
flutter clean
cd ios && pod install && cd ..
flutter run
```

## Security Notes

- **Never commit** `.env` file to version control
- **Never commit** `GoogleService-Info.plist` or `google-services.json` to public repositories
- Keep Firebase API keys secure
- Configure Firebase security rules appropriately

## Testing

Write your tests in the `test/` directory:

```bash
flutter test
```

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This template is free to use under the MIT License. See [LICENSE](LICENSE) for details.

## Additional Resources

- [Flutter Documentation](https://docs.flutter.dev/)
- [Firebase Documentation](https://firebase.google.com/docs)
- [Riverpod Documentation](https://riverpod.dev/)
- [Detailed Setup Guide](SETUP.md)

## Support

For issues specific to this template, please file an issue on GitHub.

For Flutter questions, visit [Flutter Community](https://flutter.dev/community).
For Firebase questions, visit [Firebase Support](https://firebase.google.com/support).
