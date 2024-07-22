# Firebase Cloud Messaging Template

This Flutter project provides a streamlined setup for integrating Firebase Cloud Messaging (FCM) into your mobile application.

## Getting started

### 1. Project Setup

Run with your org to generate platform specific code

```bash
fvm flutter create . --org com.example.app
```

Then bootstrap project with melos

```bash
melos bs
```

### 2. iOS Setup

iOS requires some extra work to get things going.

#### 2.1 XCode

From XCode, add the following capabilities:

- Push Notifications

- Background Modes (Background fetch, Remote notifications)

Then check that you app has your organisation Bundle Identifier

#### 2.2 Apple Developer

If you don't have one, you will need to generate a key (.p8) that enables the Apple Push Notifications service (APNs)

### 3. Setup Flutter/Firebase project

#### 3.1 Authentication

Go to [Firebase console](https://console.firebase.google.com/) and create new project.

Then Enable Authentication via Email/Password and the Google provider.

#### 3.2 Install firebase CLI (first time only)

```bash
pnpm install -g firebase-tools
```

#### 3.3 Login to firebase (first time only)

```bash
firebase login
```

#### 3.4 Install FlutterFire CLI (first time only)

```bash
dart pub global activate flutterfire_cli
```

#### 3.5 Run flutterfire cli

```bash
flutterfire configure
```

- Select your project

- Select the supported platforms

- Set package name

#### 3.6 Android certificate

Now go into Firebase's android app settings (from the project's overview) and set the digital fingerprints.

```bash
keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
```

(you can set both SHA-1 and SHA-256)

#### 3.7 iOS APNs key

From the project's settings (top left), go into the Cloud Messaging Tab.

Upload the APNs key by providing the previously generated .p8 key, the key ID and the team ID.
