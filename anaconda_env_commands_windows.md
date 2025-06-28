# Windows에서 Anaconda 가상환경 사용 명령어

Anaconda에서 가상환경을 생성하고 관리하는 기본 명령어입니다.

1. **가상환경 생성**

```bash
conda create -n <환경명> python=<버전>
```

2. **가상환경 리스트 확인**

```bash
conda env list
```

3. **가상환경 활성화**

```bash
conda activate <환경명>
```

4. **가상환경 비활성화**

```bash
conda deactivate
```

5. **가상환경에 패키지 설치**

```bash
conda install <패키지이름>
```

6. **가상환경 삭제**

```bash
conda remove -n <환경명> --all
```

> _삭제 시 현재 base 환경에 있는지 확인하세요._
