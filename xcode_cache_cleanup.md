# Xcode 캐시 삭제 가이드

Xcode 관련 불필요한 캐시를 정리하는 방법입니다.

## 1. 기본 DerivedData 삭제

```bash
rm -rf ~/Library/Developer/Xcode/DerivedData
```

## 2. 추가 캐시 삭제 및 클린업

위 명령어만으로 해결되지 않을 경우, 아래 명령을 순차적으로 실행하여 남아 있는 캐시를 모두 삭제합니다:

```bash
# Xcode 프로세스 종료
killall Xcode

# Xcode 유틸리티 초기화
xcrun -k

# 모든 타겟 클린 빌드
xcodebuild -alltargets clean

# LLVM 모듈 캐시 삭제
rm -rf "$(getconf DARWIN_USER_CACHE_DIR)/org.llvm.clang/ModuleCache"
rm -rf "$(getconf DARWIN_USER_CACHE_DIR)/org.llvm.clang.$(whoami)/ModuleCache"

# DerivedData 완전 삭제 (가장 안전)
rm -rf ~/Library/Developer/Xcode/DerivedData/*

# Xcode 관련 캐시 삭제
rm -rf ~/Library/Caches/com.apple.dt.Xcode/*

# Xcode 재실행
open /Applications/Xcode.app
```

위 단계들을 실행한 후 Xcode를 재시작하면 캐시가 초기화되어 빌드 오류나 성능 이슈가 개선될 수 있습니다.
