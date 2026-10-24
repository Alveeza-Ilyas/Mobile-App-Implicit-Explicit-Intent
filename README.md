# Mobile-App-Implicit-Explicit-Intent

A small Android app (Java) that demonstrates the difference between **explicit** and **implicit** intents in Android.

The main screen has two buttons:

| Button | Intent type | What it does |
|--------|-------------|--------------|
| **Explicit** | Explicit Intent | Opens `CallSecondActivity` inside the same app and shows a toast message |
| **Implicit** | Implicit Intent | Opens Google Maps (`https://www.google.com/maps`) in a browser or maps app chosen by the system |

## Concepts Demonstrated

- **Explicit Intent**: names the exact target component (the class) to start.
  ```java
  Intent intent = new Intent(ImplicitExplicit.this, CallSecondActivity.class);
  startActivity(intent);
  ```
- **Implicit Intent**: declares an action and data, and lets Android pick an app that can handle it.
  ```java
  Intent intent = new Intent(Intent.ACTION_VIEW);
  intent.setData(Uri.parse("https://www.google.com/maps"));
  startActivity(intent);
  ```
- Using `Toast` to show a short message when the second activity opens.
- Edge-to-edge layout with `EdgeToEdge.enable()` and window insets handling.

## Project Structure

```
java/
    ├── ImplicitExplicit.java      # Main screen with the two buttons
    └── CallSecondActivity.java    # Target activity of the explicit intent
layout/
    ├── activity_implicit_explicit.xml   # Layout with `explicit` and `implicit` buttons
    └── activity_call_second.xml         # Layout of the second activity
```

## Preview


<img width="702" height="1600" alt="image" src="https://github.com/user-attachments/assets/67721315-8188-4195-b4b7-dc6340d5a473" />

## After Clicking on Explicit Intent Button:

<img width="702" height="1600" alt="image" src="https://github.com/user-attachments/assets/1bf7acbd-f4b6-413a-a318-fc07caedacc5" />

## After Clicking on Implicit Intent Button:

<img width="702" height="1600" alt="image" src="https://github.com/user-attachments/assets/5718ba98-df0a-4dbc-81ff-3d17f559a607" />



---


## How It Works

1. `ImplicitExplicit` loads `activity_implicit_explicit.xml` and finds the two buttons (`R.id.explicit`, `R.id.implicit`).
2. Tapping **Explicit** starts `CallSecondActivity`, which displays the toast *"We are moved to second activity"*.
3. Tapping **Implicit** fires an `ACTION_VIEW` intent with a Google Maps URL; Android launches whichever app can open it.

## Requirements

- Android Studio (Koala or newer recommended)
- Android SDK with a device or emulator running API 21+ (adjust to your `minSdk`)
- Java 8+
- Dependencies: `androidx.appcompat`, `androidx.activity`, `androidx.core`

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/Alveeza-Ilyas/Mobile-App-Implicit-Explicit-Intent
   ```
2. Open the project in **Android Studio**.
3. Let Gradle sync finish.
4. Run on an emulator or a physical device.

## Manifest Setup

Both activities must be declared in `AndroidManifest.xml`:

```xml
<activity android:name=".ImplicitExplicit" android:exported="true">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>

<activity android:name=".CallSecondActivity" />
```

If you target Android 11+ (API 30+) and want to query for handlers of the implicit intent, you may also need a `<queries>` entry.

## Notes

- The implicit intent requires an app that can open web links (e.g. a browser) on the device.
- Package name: `com.alveezailyas.myhomework`

## Author

**Alveeza Ilyas**
