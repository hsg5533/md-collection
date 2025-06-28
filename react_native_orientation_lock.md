# React Native 세로 모드 고정 (가로 모드 방지)

React Native 앱에서 가로 모드를 막고 세로 모드만 지원하도록 설정하는 방법입니다.

## 1. Android

`android/app/src/main/AndroidManifest.xml` 파일을 열고, `<activity>` 태그에 다음 속성을 추가합니다:

```xml
<activity
    android:name=".MainActivity"
    android:screenOrientation="portrait"
    ... >
    ...
</activity>
```

이 설정을 추가하면 해당 액티비티가 세로(Portrait) 모드로만 동작합니다.

## 2. iOS

프로젝트의 `Info.plist` 파일에서 기존 `UISupportedInterfaceOrientations` 섹션을 다음과 같이 수정합니다:

```xml
<key>UISupportedInterfaceOrientations</key>
<array>
    <string>UIInterfaceOrientationPortrait</string>
    <!-- 아래 두 줄을 제거하여 가로 모드를 비활성화 -->
    <!-- <string>UIInterfaceOrientationLandscapeLeft</string> -->
    <!-- <string>UIInterfaceOrientationLandscapeRight</string> -->
</array>
```

이제 iOS에서는 세로 모드만 지원되고, 가로 모드는 사용이 불가능해집니다.
