# React Native Firebase 적용 가이드

React Native 프로젝트에 Firebase를 연동하는 방법을 정리합니다.

## 1. Android 설정

1. Firebase 콘솔에서 새 프로젝트를 생성합니다.
2. 프로젝트에 Android 앱을 등록하고, **패키지 이름**(예: `com.example.app`)을 입력합니다.
3. 생성된 `google-services.json` 파일을 다운로드하여 `android/app` 폴더에 저장합니다.
4. `android/app/build.gradle` 파일 상단에 다음을 추가합니다:

```gradle
apply plugin: 'com.google.gms.google-services'
```

5. `android/build.gradle` 파일의 `dependencies` 섹션에 Google 서비스 클래스패스를 추가합니다:

```gradle
buildscript {
   dependencies {
      classpath 'com.google.gms:google-services:4.3.15'
   }
}
```

6. Android 프로젝트를 동기화(Build → Sync Project)를 실행합니다.

## 2. iOS 설정

1. Xcode에서 `.xcworkspace` 파일을 열고, 프로젝트 내에 **GoogleService-Info.plist** 파일을 추가합니다.
2. `AppDelegate.h` 파일 상단에 Firebase 헤더를 추가합니다:

```objc
#import <Firebase.h>
```

3. `AppDelegate.m` 또는 `AppDelegate.mm` 파일에서 `didFinishLaunchingWithOptions` 메서드를 수정하여 Firebase를 초기화합니다:

```objc
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
   self.moduleName = @"YourModuleName";  // React Native 모듈명
   self.initialProps = @{};

   [FIRApp configure];  // Firebase 초기화

   return [super application:application didFinishLaunchingWithOptions:launchOptions];
}
```

4. CocoaPods 설치 및 업데이트:
   ```shell
   cd ios
   pod install
   cd ..
   ```
5. Xcode에서 Clean Build Folder 후 빌드합니다.

이제 React Native 앱에서 Firebase 기능(인증, 데이터베이스, 스토리지 등)을 사용할 수 있습니다.
