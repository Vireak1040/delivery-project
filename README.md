# delivery_app (Flutter) -> connects to delivery_api (Dart Frog)

## Setup
1. `flutter create delivery_app`
2. Replace its `pubspec.yaml` and `lib/` folder with the ones in this zip.
3. `flutter pub get`
4. Android only: edit `android/app/src/main/AndroidManifest.xml`
   - add `<uses-permission android:name="android.permission.INTERNET"/>` above `<application>`
   - add `android:usesCleartextTraffic="true"` inside the `<application ...>` tag
     (needed because the dev API uses http, not https)
5. Start the API (`dart_frog dev` in delivery_api), then `flutter run`.

## API address
- Android emulator: automatic (http://10.0.2.2:8080)
- iOS simulator: automatic (http://localhost:8080)
- Real phone on same Wi-Fi:
  `flutter run --dart-define=API_URL=http://<PC-IP>:8080`

## Screens <-> endpoints
Login / Register / Forgot Password (3 steps) -> /auth/*
Home (vehicles + active deliveries) -> /pricing, /bookings?status=pick_up
Book Delivery + Review Order -> /locations/provinces, /payment_methods, POST /bookings
History + Delivery Details -> /bookings
Tracking -> /tracking/<code>, /companies
Account + Add Cards -> /account, /payment_methods, /auth/logout

Main color: change `AppColors.primary` in lib/core/widgets.dart.
