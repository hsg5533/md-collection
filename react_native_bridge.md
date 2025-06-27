# React Native 개요 및 Bridge 구조

## 1. React Native란?

- JavaScript로 iOS 및 Android 네이티브 앱을 개발할 수 있는 **오픈 소스 프레임워크**
- **네이티브 UI 컴포넌트**를 사용하여 플랫폼별 사용자 경험 제공
- 비즈니스 로직 및 UI 로직은 **JavaScript 코드**로 작성

## 2. 앱 동작 구조

1. JavaScript 번들 파일 로드 (앱의 로직 포함)
2. **Bridge**를 통해 JS ↔ 네이티브 간 통신 수행
3. 각 플랫폼별 UI 컴포넌트에 맞춰 네이티브 컴포넌트로 변환

## 3. View 구성요소 예시

- React Native의 `<View />`
  - iOS: `UIView`
  - Android: `android.view.View`

## 4. Bridge 구조

- **Bridge**: JS ↔ 네이티브 간 통신 인터페이스
- **비동기 방식**으로 작동 → UI 렌더링 및 성능 저하 없음

### 주요 기능

- JavaScript에서 네이티브 기능 호출
- 네이티브 결과를 JavaScript로 반환

## 5. 네이티브 모듈

- 네이티브 기능을 JavaScript에서 사용할 수 있게 래핑
- 보통:
  - iOS: Objective-C
  - Android: Java
- 예: `CameraRoll`
  - iOS: `UIImagePickerController`
  - Android: `android.provider.MediaStore`

## 6. Bridge 성능

- React Native의 성능은 Bridge에 크게 의존
- 최신 버전에서 **성능 최적화** 지속 중

## 7. pod이란?

- **CocoaPods**: iOS용 패키지 및 의존성 관리자
- `podfile`: iOS 앱의 네이티브 라이브러리와 의존성 정의

### 역할

- iOS용 네이티브 라이브러리 자동 설치
- Xcode 프로젝트 실행 시 podfile 기반으로 CocoaPods 의존성 설치
- **iOS 빌드 및 실행에 필수**
