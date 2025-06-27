# iOS 빌드 시 Cocoapods 오류 해결

## 오류 메시지

```bash
error: Unable to load contents of file list: '/Target Support Files/Pods-helperit/Pods-helperit-frameworks-Debug-input-files.xcfilelist' (in target 'helperit' from project 'helperit')
error: Unable to load contents of file list: '/Target Support Files/Pods-helperit/Pods-helperit-frameworks-Debug-output-files.xcfilelist' (in target 'helperit' from project 'helperit')
error: Unable to load contents of file list: '/Target Support Files/Pods-helperit/Pods-helperit-resources-Debug-input-files.xcfilelist' (in target 'helperit' from project 'helperit')
error: Unable to load contents of file list: '/Target Support Files/Pods-helperit/Pods-helperit-resources-Debug-output-files.xcfilelist' (in target 'helperit' from project 'helperit')
```

## 원인

Mac에서 iOS로 빌드할 경우, **CocoaPods가 설치되어 있지 않으면** 위와 같은 오류가 발생할 수 있습니다. 이는 Xcode가 의존성 관련 `.xcfilelist` 파일을 찾지 못해 생기는 문제입니다.

## 해결 방법

`brew`를 사용하여 `cocoapods`를 설치하면 문제를 해결할 수 있습니다.

```bash
brew install cocoapods
```

설치 후 다음 명령어로 의존성 설치를 완료하세요:

```bash
pod install
```

그리고 Xcode에서 `.xcworkspace` 파일을 열어 빌드를 다시 시도하십시오.
