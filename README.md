# super_image_selector

A lightweight Flutter package to pick images from camera/gallery and pick multiple images.

## Features
- Pick single image from gallery
- Pick single image from camera
- Pick multiple images (gallery)
- Simple API and example app

## Platform Permissions

### Android
Add the following in `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

FileProvider entry (inside `<application>`):

```xml
<provider
    android:name="androidx.core.content.FileProvider"
    android:authorities="${applicationId}.fileprovider"
    android:exported="false"
    android:grantUriPermissions="true">
    <meta-data
        android:name="android.support.FILE_PROVIDER_PATHS"
        android:resource="@xml/provider_paths" />
</provider>
```

Create `android/app/src/main/res/xml/provider_paths.xml`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<paths>
    <external-files-path name="images" path="Pictures" />
</paths>
```

### iOS
Add this in `Info.plist`:

```xml
<key>NSCameraUsageDescription</key>
<string>This app requires camera access to capture photos.</string>
<key>NSPhotoLibraryUsageDescription</key>
<string>This app requires photo library access to select images.</string>
<key>NSPhotoLibraryAddUsageDescription</key>
<string>This app needs permission to save selected images.</string>
```

## Usage

```dart
import 'package:super_image_selector/super_image_selector.dart';

final file = await SuperImageSelector.pickFromGallery();
```

See the `example/` folder for a full example.
