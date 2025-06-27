# React Native iOS 빌드 오류 해결

## 오류 메시지

```bash
PhaseScriptExecution [CP] Check Pods Manifest.lock /Users/jeonghosang/.../Script-C38B50BA6285516D6DCD4F65.sh (in target 'helperitSimbureum' from project 'helperitSimbureum')
(1 failure)
```

## 원인

macOS 14.0 및 Xcode 15 환경에서 **React Native 0.71.6** 버전을 빌드하려 할 때, 해당 React Native 버전이 Xcode 15을 지원하지 않아 발생하는 오류입니다.

## 해결 방법

React Native를 **최신 버전**으로 업데이트하여 빌드 환경과 호환되도록 하면 문제가 해결됩니다:

```bash
npm install -g react-native-cli
react-native upgrade
```
