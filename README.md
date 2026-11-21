🚌 Bus Route Finder

A Flutter mobile app that helps commuters in Kathmandu find bus routes between two places, see every stop along the way, and locate the nearest stop from their current position. Route data is stored in Cloud Firestore and shown on Google Maps.

✨ Features
Email/password authentication – sign up, log in and reset a forgotten password (Firebase Auth)
Route search – pick a starting point and destination from searchable dropdowns
Route on the map – the route is drawn as a polyline with start/end markers and a marker for every bus stop
Bus name – shows which bus service (e.g. Mahanagar Yatayat) runs the selected route
My Location – centres the map on your current position
Nearest Stop – finds the closest bus stop to where you are
Live directions – turn-by-turn style path between two points using the Google Directions API
Splash screen and Material 3 teal theme
🛠 Tech Stack
Area	Technology
Framework	Flutter (Dart, SDK >=2.18.0 <4.0.0)
Auth	Firebase Authentication
Database	Cloud Firestore
Maps	google_maps_flutter, Google Directions API, flutter_polyline_points
Location	geolocator, location, permission_handler
Other	dropdown_search, url_launcher, http, Firebase Storage & Messaging
📁 Project Structure
lib/
├── main.dart                 # App entry point, Firebase init
├── splash_screen.dart        # Splash screen
├── login_page.dart           # Login
├── signup_page.dart          # Registration
├── forgot_password_page.dart # Password reset
├── dashboard1.dart           # Main screen: search, map, nearest stop
├── live_directions_page.dart # Directions via Google Directions API
├── route_utils.dart          # Load/save routes in Firestore, build polylines & markers
├── route_uploader.dart       # One-off seed data (Kalanki → Gongabu route)
└── firebase_options.dart     # Generated Firebase config
assets/                       # Bus icons and images
android/ ios/ web/ linux/ macos/ windows/   # Platform folders
🗄 Firestore Data Model

Routes live in the route collection:

json
{
  "start": "Kalanki",
  "end": "Gongabu New Bus Station Parking, Kathmandu 44600",
  "bus": "Mahanagar Yatayat",
  "coordinates": [ { "Lat": 27.693148, "Lng": 85.280928 } ],
  "stops": [ { "Lat": 27.704174, "Lng": 85.282102, "title": "Soaltee Dobato Chowk" } ]
}
🚀 Getting Started
Prerequisites
Flutter SDK (stable) and Android Studio or VS Code
A Firebase project with Authentication (Email/Password) and Cloud Firestore enabled
A Google Cloud API key with Maps SDK for Android and Directions API enabled
Installation
bash
git clone https://github.com/jibachyadav/bus-route-finder.git
cd bus-route-finder
flutter pub get
Configure your keys
Run flutterfire configure to generate your own lib/firebase_options.dart and android/app/google-services.json.
Put your Google Maps key in android/app/src/main/AndroidManifest.xml (com.google.android.geo.API_KEY).
Put your Directions API key in lib/live_directions_page.dart.

⚠️ Never commit real API keys to a public repository. Restrict your keys in Google Cloud Console (by app package name / API) and keep secrets out of source control.

Run
bash
flutter run

Build a release APK with flutter build apk --release.

🧪 Tests
bash
flutter test
🗺 Roadmap
Add more Kathmandu bus routes and operators
Real-time bus tracking
Route fares and timings
Favourite routes and search history
📄 License

Distributed under the terms of the LICENSE file.
