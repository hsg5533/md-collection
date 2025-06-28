# Kotlin 메타데이터 버전 불일치 오류 해결

React Native Android 빌드 또는 Gradle 플러그인 컴파일 시 다음과 같은 오류가 발생할 수 있습니다:

```
Execution failed for task ':react-native-gradle-plugin:compileKotlin'.

/Users/jeonghosang/.gradle/caches/8.0.1/generated-gradle-jars/gradle-api-8.0.1.jar!/META-INF/configuration-cache.kotlin_module: 
Module was compiled with an incompatible version of Kotlin. The binary version of its metadata is 1.8.0, expected version is 1.6.0.
```

## 1. 원인
- 프로젝트에서 사용하는 Kotlin 버전 간의 호환성 문제입니다.
- Kotlin 모듈이 **1.8.0** 버전으로 컴파일되어 있지만, 현재 설정된 빌드가 **1.6.0** 버전 메타데이터를 기대하고 있는 경우 발생합니다.

## 2. 해결 방법
1. Gradle 래퍼 설정 파일을 엽니다:  
   ```
   android/gradle/wrapper/gradle-wrapper.properties
   ```
2. `distributionUrl` 속성에서 Gradle 버전을 호환 가능한 버전으로 업데이트합니다.  
   예: Gradle 7.0.2 사용 시:
   ```
   distributionUrl=https\://services.gradle.org/distributions/gradle-7.0.2-all.zip
   ```
3. 변경 후, 프로젝트 루트에서 Gradle 캐시 정리 및 빌드를 다시 실행합니다:
   ```bash
   cd android
   ./gradlew clean
   cd ..
   npx react-native run-android
   ```

Gradle 및 Kotlin 버전 호환성이 맞춰지면 컴파일 오류가 해결됩니다.
