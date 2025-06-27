# Xcode error code 65 iOS 빌드 오류 해결

## 오류 메시지

```bash
error Failed to build iOS project. We ran "xcodebuild" command but it exited with error code 65.
```

## 원인

캐시된 Pod 파일과 현재 프로젝트에서 사용하는 Pod 파일이 불일치하여 발생하는 문제입니다.

## 해결 방법

1. **Xcode Derived Data 삭제**

   - Xcode 실행 후 아무 프로젝트를 열고,
   - 메뉴 `Xcode` > `Preferences...` > `Locations` 탭에서 **Derived Data** 경로 확인
   - 해당 폴더를 Finder 또는 터미널에서 완전히 삭제

2. **워크스페이스 파일 삭제**

```bash
rm -rf ios/*.xcworkspace
```

3. **Podfile.lock 삭제**

```bash
rm ios/Podfile.lock
```

4. **CocoaPods 재설치**

```bash
cd ios
pod install
```

5. **Xcode에서 다시 빌드**
   - `.xcworkspace` 파일로 Xcode를 열고 빌드 시도
