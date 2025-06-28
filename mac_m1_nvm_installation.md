# Mac M1에서 NVM(Node Version Manager) 설치 방법

Apple Silicon(M1/M2) 기반 Mac에서 NVM을 설치하고 설정하는 단계별 가이드입니다.

---

## 1. Homebrew 설치

Homebrew가 설치되어 있지 않다면, 먼저 Homebrew를 설치합니다:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 2. NVM 설치

터미널에서 Homebrew를 이용해 NVM을 설치합니다:
```bash
brew install nvm
```

## 3. 쉘 프로필 설정

`~/.zshrc` 파일을 텍스트 에디터(예: `vi`, `vim`, `nano`)로 열고 아래 내용을 추가합니다:

```bash
export NVM_DIR="$HOME/.nvm"
source "$(brew --prefix nvm)/nvm.sh"
```

- `export NVM_DIR="$HOME/.nvm"`: NVM의 설치 디렉터리를 지정합니다.  
- `source "$(brew --prefix nvm)/nvm.sh"`: NVM 스크립트를 로드하여 현재 터미널 세션에서 사용할 수 있도록 합니다.

## 4. 변경 사항 적용

쉘 프로필을 다시 로드하여 설정을 적용합니다:
```bash
source ~/.zshrc
```

## 5. 설치 확인 및 사용

정상적으로 설치되었는지 확인합니다:
```bash
nvm --version
```

이제 다음과 같이 원하는 Node.js 버전을 설치하고 전환할 수 있습니다:

```bash
nvm install 18       # Node.js v18 설치
nvm use 18           # v18 사용
nvm install --lts    # 최신 LTS 버전 설치
nvm ls               # 설치된 버전 목록 확인
```
