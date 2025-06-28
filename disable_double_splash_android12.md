# Android 12 이상: 이중 스플래시 화면 비활성화

Android 12 이상에서는 시스템 기본 스플래시 화면이 자동으로 적용됩니다.  
앱 내에서 별도의 커스텀 스플래시 화면을 구현한 경우, 앱 실행 시 이중 스플래시 화면이 표시되는 현상이 발생할 수 있습니다.

## 해결 방법

1. Android 프로젝트의 `android/app/src/main/res/values/styles.xml` 파일을 엽니다.

2. `<style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">` 등 앱 기본 테마 정의 안에 아래 항목을 추가하거나 수정합니다:

```xml
<item name="android:windowIsTranslucent">true</item>
```

예시:

```xml
<resources>
  <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
    <!-- 기존 설정... -->
    <item name="android:windowIsTranslucent">true</item>
  </style>
</resources>
```

3. 변경 사항을 저장한 뒤, 프로젝트를 Clean & Rebuild 합니다:

```shell
cd android
./gradlew clean
cd ..
npx react-native run-android
```

이제 Android 12 이상 기기에서도 커스텀 스플래시 화면만 표시되어, 이중 스플래시가 해제됩니다.
