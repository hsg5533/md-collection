```bash
django.core.exceptions.ImproperlyConfigured: Could not find the GDAL library (tried "gdal", "GDAL", "gdal3.4.0", "gdal3.3.0", "gdal3.2.0", "gdal3.1.0", "gdal3.0.0", "gdal2.4.0", "gdal2.3.0", "gdal2.2.0"). Is GDAL installed? If it is, try setting GDAL_LIBRARY_PATH in your settings.
```

## 1. 원인: gdal 설치가 되지 않아서 나타나는 오류이다.

## 2. 해결: Mac환경에서 brew를 사용하여 설치할 수 있다.

```bash
brew install gdal
```

## 3. Mac M1에서 gdal 설치법

- brew로 gdal를 설치하여도 경로 문제때문에 gdal를 읽지 못하는 경우가 발생한다.
- 그러한 경우에는 settings.py에 직접 gdal이 설치된 경로를 명시해야 한다.
- 아래의 명령어로 해당 파일을 찾는다.

```bash
find /opt -name "libgdal.dylib" -print 2>/dev/null
find /opt -name "libgeos_c.dylib" -print 2>/dev/null
```

## 4. django 프로젝트의 settings.py파일에서 아래처럼 gdal과 geos의 설치경로를 명시해주면 된다.

```python
GDAL_LIBRARY_PATH="/opt/homebrew/Cellar/gdal/3.6.2/lib/libgdal.dylib"
GEOS_LIBRARY_PATH="/opt/homebrew/Cellar/geos/3.11.1/lib/libgeos_c.dylib"
```
