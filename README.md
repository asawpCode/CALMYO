# CALMYO

A Flutter mindfulness app focused on meditation, sleep, and daily mental wellness. Built for Android and iOS with a Firebase backend.

The UI is in Romanian.

---

## What it does

**Meditation** — browse relaxation sounds and guided meditations pulled from Firebase Storage. Pick a sound, set a timer anywhere from 1 to 120 minutes, and start. Breathing exercises are available separately.

**Sleep** — ambient sounds to fall asleep to, plus guided sleep meditations. You set a wake-up time and the app fires a local alarm notification when the time comes.

**Progress tracking** — every meditation session earns points based on duration. Points roll up into a level system (Beginner → Intermediate → Advanced → PRO) with a streak counter for consecutive days.

**Friends** — add other users by username, send/receive friend requests, and see their streak and level. A small social layer to keep each other accountable.

---

## Tech

- **Flutter** (Dart, SDK ≥ 3.1.5)
- **Firebase** — Auth (email + Google Sign-In), Firestore, Storage, Cloud Messaging
- **Lottie** — animated backgrounds and UI elements
- **just_audio** — audio playback for meditations and sleep sounds
- **flutter_local_notifications** — wake-up alarm
- **percent_indicator** — progress/level ring

---

## Setup

You need Flutter installed and a Firebase project configured before running this.

### 1. Install Flutter

Follow the official guide for your OS: https://docs.flutter.dev/get-started/install

### 2. Clone the repo

```bash
git clone https://github.com/asawpCode/CALMYO.git
cd CALMYO
```

### 3. Firebase setup

This project uses Firebase. You'll need your own Firebase project with:
- Authentication (Email/Password + Google Sign-In enabled)
- Firestore Database
- Firebase Storage (audio files organized under `audio/meditatie/` and `audio/somn/`)
- Firebase Cloud Messaging

Replace the existing config files with your own:
- `android/app/google-services.json`
- `ios/Runner/GoogleService-Info.plist`
- `lib/firebase_options.dart` (generate with `flutterfire configure`)

### 4. Install dependencies and run

```bash
flutter pub get
flutter run
```

---

## Firestore structure

The app expects these collections:

| Collection | Purpose |
|---|---|
| `meditationMetadata` | Guided meditations and breathing exercises |
| `relaxMeditationMetadata` | Relaxation sounds |
| `sleepMetadata` | Guided sleep meditations |
| `users` | User profiles, points, streaks |
| `friend_requests` | Pending/accepted friend requests |

Audio files live in Firebase Storage under `audio/meditatie/ghidata/`, `audio/meditatie/exercitii/`, `audio/meditatie/relaxare/`, and `audio/somn/`.

---

## Notes

- The app was built and tested on Android. iOS should work but hasn't been as thoroughly tested.
- Audio content and Firestore data are not included in this repo — you'll need to populate your own Firebase project.
