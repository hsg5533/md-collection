# ADB 명령어 인식 오류 해결

아래 오류는 맥에서 Android Studio는 설치되어 있지만, ADB(Android Debug Bridge) 환경변수가 설정되어 있지 않아 발생합니다:

```shell
zsh: command not found: adb
```

## 해결 방법

1. `~/.zshrc` 파일을 편집 모드로 열기 위해 터미널에서 다음 명령어를 입력합니다:

```shell
vi ~/.zshrc
```

파일이 열리면 `i` 키를 눌러 **입력 모드**로 진입합니다.

2. 아래 구문을 파일 끝에 추가한 후, `ESC`를 누르고 `:wq`를 입력하여 저장(`write`)하고 종료(`quit`)합니다:

```shell
export ANDROID_HOME=/Users/jeonghosang/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/build-tools/33.0.2
```

3. 변경 사항을 적용하기 위해 터미널을 재시작하거나 다음 명령어를 실행합니다:

```shell
source ~/.zshrc
```

이제 터미널에서 `adb` 명령어를 사용할 수 있습니다.
