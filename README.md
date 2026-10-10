# Centella Mobile App

The mobile app of **Centella Homes HOA Management**, a homeowners association (HOA) management system. Homeowners use it to reserve subdivision facilities, check live facility schedules, pay for reservations, and stay up to date with community announcements. Built with **React Native** and **Expo**, it shares a **Supabase** backend with the Centella web app and the Centella admin desktop app.

## The Centella Platform

Centella is split into three apps that work against the same Supabase backend:

| App | Description | Stack | Repository |
| --- | --- | --- | --- |
| **Mobile App** (this repo) | Mobile client | React Native, Expo | [Centella-Mobile-App](https://github.com/xien-ica/Centella-Mobile-App) |
| **Web App** | Browser-based client | React, Vite | [Centella-Web-App](https://github.com/xien-ica/Centella-Web-App) |
| **Admin App** | Desktop app for HOA administrators | Electron, React | [Centella-Admin-App](https://github.com/xien-ica/Centella-Admin-App) |

## Features

- **Facility reservations:** homeowners can reserve subdivision facilities directly from the app
- **Realtime facility schedule:** view up-to-date availability and bookings for each facility
- **Realtime announcements, updates, and alerts:** delivered in the app and as push notifications
- **Payments:** pay for reservations online or choose physical (on-site) payment

> **Note:** Online payment is a **mock-up only**, simulated through [PayMongo](https://www.paymongo.com/). No real transactions are processed.

## Tech Stack

| Area | Technology |
| --- | --- |
| Framework | React Native 0.81 with React 19.1 |
| Tooling | Expo SDK 54 (New Architecture enabled) |
| Navigation | React Navigation 7 (bottom tabs, native stack, stack) |
| Backend | Supabase (`@supabase/supabase-js`), shared with the web and admin apps |
| Payments | PayMongo (mock-up / simulated) |
| Notifications | `expo-notifications`, OneSignal (`react-native-onesignal`) |
| Storage | AsyncStorage, `expo-secure-store` |
| Media | `expo-camera`, `expo-av`, `expo-audio`, `expo-video`, `expo-media-library` |
| UI | `lucide-react-native`, `@expo/vector-icons`, `react-native-reanimated`, `react-native-svg`, `expo-linear-gradient`, `expo-blur` |
| Build and delivery | Expo Application Services (EAS) |

## Project Structure

```
Centella-Mobile-App/
├── assets/          # Images, icons, splash screen, and other static files
├── navigation/      # Navigators and routing setup
├── screens/         # App screens
├── services/        # API and backend service logic
├── utils/           # Shared helper functions
├── App.js           # App root
├── index.js         # Entry point
├── app.json         # Expo app configuration
├── eas.json         # EAS build profiles
├── babel.config.js  # Babel configuration
└── package.json
```

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (LTS recommended)
- npm
- [Expo Go](https://expo.dev/go) on a physical device, or an Android emulator / iOS simulator
- For native builds: Android Studio (Android) or Xcode on macOS (iOS)

### Installation

```bash
git clone https://github.com/xien-ica/Centella-Mobile-App.git
cd Centella-Mobile-App
npm install
```

### Environment Variables

The project uses `dotenv` / `react-native-dotenv`, so create a `.env` file in the project root. Use the same Supabase project as the web and admin apps.

```env
VITE_SUPABASE_URL=<your-supabase-project-url>
VITE_SUPABASE_PUBLISHABLE_KEY=<your-supabase-publishable-key>
ONESIGNAL_APP_ID=your-onesignal-app-id
```

Never commit your `.env` file or any secret keys.

### Firebase / Push Notifications (Android)

`app.json` references a `google-services.json` file for Android. Download it from your Firebase project and place it in the project root. Without it, Android builds that use push notifications will fail.

### Running the App

```bash
npm start            # Start the Expo dev server
npm run android      # Run on Android
npm run ios          # Run on iOS (macOS only)
npm run web          # Run in the browser
```

Some native modules (such as OneSignal) do not work in Expo Go. Use a development build (`npm run android` / `npm run ios`, or an EAS development build) to test them.

## Building with EAS

Build profiles are defined in `eas.json`.

```bash
npm install -g eas-cli
eas login
eas build --platform android --profile preview
```

## App Configuration

| Setting | Value |
| --- | --- |
| App name | Centella App |
| Version | 1.0.0 |
| Orientation | Portrait |
| Android package | `com.centella.app` |
| iOS bundle identifier | `com.centella.app` |

## Scripts

| Command | Description |
| --- | --- |
| `npm start` | Start the Expo development server |
| `npm run android` | Build and run on Android |
| `npm run ios` | Build and run on iOS |
| `npm run web` | Start the web version |

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m "Add your feature"`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a pull request

## Author

Built by [xien-ica](https://github.com/xien-ica) for Centella Homes.
