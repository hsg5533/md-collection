# 파이썬(Python) 기초 개요

## 🐍 파이썬이란?

- **1991년 귀도 반 로섬(Guido van Rossum)**이 발표한 고급 프로그래밍 언어.
- **인터프리터 + 컴파일러**를 지원하는 **객체지향 언어**.
- 문법이 쉬워 **교육용**으로 적합하며, 다양한 **라이브러리**를 통해 전문가도 폭넓게 사용.
- 특히 **인공지능 분야**에서는 필수 언어로 간주됨.

## 🖥️ 인터프리터와 컴파일러

- **인터프리터**: 소스코드를 한 줄씩 읽고 바로 실행.
- **컴파일러**: 전체 코드를 분석 후 실행 가능한 바이너리로 변환.
- **파이썬은 둘 다 지원**:
  - `.py` 파일 → 바이트코드(.pyc)로 컴파일 → 인터프리터가 실행

## 💾 비트(bit)와 바이트(byte)

| 항목 | 설명 |
| | - |
| 비트(bit) | 데이터 표현의 최소 단위 (0 또는 1) |
| 바이트(byte) | 데이터 저장의 최소 단위 (1 byte = 8 bit) |

## 🔢 진법

- 수의 표현 방식 (기수법)
- **10진법**: 일상에서 사용
- **2진법 / 16진법**: 컴퓨터 내부에서 주로 사용

## 📦 자료형(Data Types)

### 1. 숫자형

- **정수**: `int`
- **실수**: `float`
- **복소수**: `complex`

### 2. 시퀀스형

- 순서 있는 자료형: `list`, `tuple`, `range`

### 3. 텍스트 시퀀스형

- 문자열: `str`

### 4. 바이너리 시퀀스형

- 바이트 시퀀스: `bytes`, `bytearray`

### 5. 집합형

- 순서 없음: `set`

### 6. 매핑형

- 키-값 쌍: `dict`

## 🔁 제어문(Control Flow)

### 1. `if` 문

```python
if 조건:
    실행문
elif 조건:
    실행문
else:
    실행문
```

- 중첩 가능
- 조건에 따라 실행 흐름 분기

### 2. `while` 문

```python
while 조건:
    실행문
```

- 조건이 참인 동안 반복
- `break`로 종료, `continue`로 다음 반복

### 3. `for` 문

```python
for 변수 in 시퀀스:
    실행문
```

- **이터레이션(iteration)** 수행
- `range()` 사용 가능
- `break`, `continue`, `else` 지원

## 📌 튜플(Tuple)

- **불변 시퀀스**
- 읽기 전용 리스트

```python
my_tuple = (1, 2, 3)
```

### 주요 함수

- `max(tuple)`, `min(tuple)`, `sum(tuple)`
- `tuple(list)` → 리스트를 튜플로 변환

## 📋 리스트(List)

- **가변 시퀀스**

```python
my_list = [1, 2, 3]
```

### 주요 함수

```python
list.append(x)
list.extend(iterable)
list.insert(i, x)
list.remove(x)
list.pop([i])
list.clear()
list.index(x)
list.count(x)
list.sort()
list.reverse()
list.copy()
```

## 🗂️ 딕셔너리(Dictionary)

- **매핑형 가변 객체**

```python
my_dict = {'key': 'value'}
```

### 주요 함수

```python
len(dict)
'key' in dict
dict.pop(key)
list(dict)  # key 목록
dict.copy()
dict.values()
```

## 📝 문자열(String)

- 순서 있는 **텍스트 시퀀스형**

```python
s1 = 'Hello'
s2 = "Python"
s3 = '''여러 줄'''
```

### 특수 문자

| 이스케이프 | 의미        |
| ---------- | ----------- |
| `\\`       | 역슬래시    |
| `\'`       | 작은 따옴표 |
| `\"`       | 큰 따옴표   |
| `\b`       | 백스페이스  |
| `\n`       | 줄 바꿈     |
| `\r`       | 캐리지 리턴 |
| `\t`       | 탭          |
