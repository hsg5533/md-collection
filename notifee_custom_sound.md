# Notifee를 이용한 커스텀 푸쉬 알림음 적용 가이드

React Native 앱에서 Notifee를 사용하여 Android 및 iOS에서 커스텀 알림음을 설정하는 방법입니다.

## 1. Android

Android에서는 알림 채널별로 알림음을 지정할 수 있습니다.

1. **알림음 파일(`.mp3`) 준비**  
   프로젝트 내 `android/app/src/main/res/raw/` 폴더에 `.mp3` 파일을 위치시킵니다.  
   예를 들어:

```
android/app/src/main/res/raw/custom_sound.mp3
```

2. **채널 생성 시 사운드 지정**  
   Notifee의 `createChannel` 메서드에서 `sound` 속성에 파일 이름(확장자 제외)을 전달합니다:

```javascript
import notifee from "@notifee/react-native";

async function createNotificationChannel() {
  await notifee.createChannel({
    id: "background",
    name: "Background Notifications",
    sound: "custom_sound", // MP3 파일 이름(확장자 제외)
  });
}
```

## 2. iOS

iOS에서는 로컬 리소스 형태로 알림음을 지정할 수 있습니다.

1. **알림음 파일(`.wav`, `.aiff`, `.caf`) 준비**  
   프로젝트 내 `ios` 폴더에 원하는 알림음 파일을 복사합니다.

2. **Xcode에 리소스 추가**

   - Xcode에서 `.xcworkspace` 파일을 열고, 프로젝트 루트에 복사한 오디오 파일을 **Drag & Drop** 합니다.
   - “Copy items if needed” 옵션을 체크하여 프로젝트에 포함시킵니다.

3. **알림 표시 시 사운드 지정**  
   `displayNotification` 호출 시 `ios.sound` 옵션에 파일 이름(확장자 포함)을 설정합니다:

```javascript
import notifee from "@notifee/react-native";

async function displayCustomNotification(title, body) {
  await notifee.displayNotification({
    title: title,
    body: body,
    ios: {
      sound: "custom_sound.wav", // 파일 이름과 확장자 포함
    },
  });
}
```

이제 Android & iOS 양쪽에서 Notifee를 통해 커스텀 알림음을 사용할 수 있습니다.
