# React Native iOS 빌드 실패 해결

React Native 프로젝트에서 iOS 빌드가 실패할 때의 원인 및 해결 방법을 정리합니다.

## 1. 문제 상황

- 터미널에서 `npm start` 실행 후 `i` 키를 눌러도 iOS 시뮬레이터/디바이스에 앱이 빌드되지 않음.
- `npx react-native run-ios` 명령을 사용하여 직접 빌드 시도 시 다음 오류 발생:

```bash
Failed to install the app on the device because we couldn't execute the "ios-deploy" command. Please install it by running "brew install ios-deploy" and try again.
```

## 2. 원인

- `npx react-native run-ios` 과정에서 네이티브 디바이스에 앱을 설치하기 위해 `ios-deploy` 툴을 호출하지만, 시스템에 해당 명령어가 설치되어 있지 않아 실패합니다.

## 3. 해결 방법

1. Homebrew가 설치되어 있지 않으면 설치합니다:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. `ios-deploy` 패키지를 설치합니다:

```bash
brew install ios-deploy
```

3. 설치가 완료되면 다시 iOS 빌드를 실행합니다:

```bash
npx react-native run-ios
```

이제 iOS 디바이스나 시뮬레이터에 앱이 정상적으로 설치되고 실행됩니다.
