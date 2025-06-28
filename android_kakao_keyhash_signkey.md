# Android 카카오 로그인 키해시 및 서명키 관련 오류 해결

## 1. 카카오 로그인 키해시 오류 해결

### 1.1. 구글 플레이 콘솔의 앱 서명 인증키로 키해시 값 추출하기

- Google Play Console에서 해당 앱의 **설정 → 앱 서명** 메뉴로 이동합니다.
- **앱 서명 인증키** 하단의 **SHA-1 인증서 지문**을 복사합니다.
- 복사한 SHA-1 인증서 지문을 사용하여 터미널에서 다음 명령어를 실행해 키해시 값을 추출합니다:

```bash
echo [SHA-1 인증서 지문] | xxd -r -p | openssl base64
```

### 1.2. 로컬 서명키(키스토어)로 키해시 값 추출하기

- Android Studio에서 AAB 파일 빌드 시 사용하는 키스토어 파일(예: `keystore.jks`)이 있는 경로를 확인합니다.
- 다음 명령어를 실행하여 키해시 값을 추출합니다:

```bash
keytool -exportcert -alias [별칭] -keystore [경로] -storepass [store 비밀번호] -keypass [key 비밀번호] | openssl sha1 -binary | openssl base64
```

- **주의**: 잘못된 alias, 경로, `storepass` 또는 `keypass`를 입력해도 오류가 발생하지 않고 잘못된 키해시가 출력될 수 있습니다.

## 2. 서명키 불일치로 인한 다른 앱 설치 오류 해결

### 2.1. 오류 상황

- Google Play Store에서 설치된 앱이 있을 때, 동일한 패키지명으로 디버그 빌드를 설치하려고 하면 다음과 같은 에러가 발생합니다:

```sh
java.util.concurrent.ExecutionException: com.android.builder.testing.api.DeviceException: com.android.ddmlib.InstallException: INSTALL_FAILED_UPDATE_INCOMPATIBLE: Existing package kr.co.helperits.android signatures do not match newer version; ignoring!
```

### 2.2. 해결 방법

- 기존에 Google Play Store에서 설치된 앱을 기기에서 완전히 삭제한 후, 디버그 빌드를 다시 설치합니다.
