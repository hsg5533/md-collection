# pycharm에서 venv 활성화 방법

1. 다음의 명령어로 pyenv를 설치할 수 있다.

```bash
brew install pyenv
```

2. 설치가 완료되면 pyenv로 사용할 버전의 파이썬을 설치한다.

```bash
pyenv install [사용할 파이썬 버전]
```

3. pycharm으로 프로젝트를 실행 후 터미널을 열어 다음의 명령어로 파이썬 가상환경을 생성한다.

```bash
pyenv virtualenv [사용할 이름]
```

4. 다음의 명령어로 해당 프로젝트에만 가상환경을 사용할 것이 가능하다.

```bash
pyenv local [생성한 가상환경 이름]
```

5. 모든 프로젝트 전역에서 사용할려면 다음의 명령어를 실행하면 된다.

```bash
pyenv global [생성한 가상환경 이름]
```
