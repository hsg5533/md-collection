# React Native 캐시 삭제 가이드

React Native 프로젝트에서 다양한 캐시를 선택적으로 삭제할 수 있는 방법입니다.

## 1. 캐시 삭제 명령어 실행

```bash
npx react-native clean
```

## 2. 캐시 종류 선택하기

명령어 실행 후 다음과 같은 인터랙티브 메뉴가 표시됩니다:

```bash
? Select all caches to clean ›
Instructions:
    ↑/↓: Highlight option
    ←/→/[space]: Toggle selection
    a: Toggle all
    enter/return: Complete answer
◉   android     (Android build caches, e.g. Gradle)
◉   cocoapods   (CocoaPods cache)
◉   metro       (Metro, haste-map caches)
◉   npm         (`node_modules` folder and optionally verify npm cache)
◯   bun         (Bun cache)
◯   watchman    (Stop Watchman and delete its cache)
◯   yarn        (Yarn cache)
```

- **↑/↓**: 항목 이동
- **←/→** 또는 **[space]**: 항목 선택/해제
- **a**: 전체 선택/해제
- **Enter**: 선택 완료

선택한 캐시만 삭제되며, 불필요한 캐시를 정리하여 빌드 오류 해결 및 용량을 확보할 수 있습니다.
