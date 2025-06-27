# Mac M1에서 mysqlclient 설치오류 해결법

```bash
ERROR: Could not build wheels for mysqlclient, which is required to install pyproject.toml-based projects
```

## 1. 원인: Mac m1 환경에서 mysqlclient패키지를 설치할 때 발생하였던 오류

## 2.해결: pymysql를 설치한 후 settings.py에 아래의 코드를 추가한다.

```python
import pymysql
pymysql.install_as_MySQLdb()
```
