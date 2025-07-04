# 신호와 신호처리 개념 정리

## 1. 신호와 신호처리

- **신호**: 시/공간적으로 변화하는 물리량 (아날로그, 디지털)
- **신호처리**: 목적에 맞게 신호를 가공하는 과정

## 2. 신호의 종류

### 스칼라 신호

- 1차원, 하나의 소스로 표현
- 예: 음성, 심전도, 뇌전도
- 수학적 표현: f(t)

### 벡터 신호

- 다차원, 복수 소스
- 예: 자연영상, 초음파 영상
- 수학적 표현: f(x, y, z, ...)

## 3. 음성 및 해상도

- **음성주파수**: 100Hz ~ 3400Hz
- **가청주파수**: 20Hz ~ 20KHz
- **해상도**: 640×480, 24bit = 2^24 색상

## 4. 아날로그 신호의 디지털화

- 장점: 에러 복원, 압축 가능, 잡음 강함
- 과정: 샘플링 → 양자화
- **양자화 방식**: 반올림 / 버림 (오차 발생)

## 5. 이산신호 시간 천이

- y[n] = x[n - N]: 시간 이동
- y[n] = A·x[n]: 증폭 시스템

## 6. 시스템 분류

- **선형 / 비선형**
- **시불변 / 시가변**
- **인과 / 비인과**
- **가역 / 비가역**
- **안정 / 비안정**

## 7. 푸리에 정리 및 변환

### 푸리에 정의

- 모든 주기신호 = DC + 정현파의 합 (고조파 포함)

### 푸리에 급수

- 계수 구함 = 푸리에 급수 완성

### 푸리에 변환

- 시간 → 주파수 변환
- **스펙트럼**: 주파수 영역에서의 파형
- **디리클레 조건** 만족 시 사용 가능

| 시간영역 | 주파수영역 |
|-||
| 임펄스 | 상수 |
| 사각파 | 싱크함수 |

## 8. 라플라스 변환

- 발산 신호도 주파수 영역으로 표현
- 디리클레 조건 미적용 가능

## 9. 샘플링 및 나이퀴스트 이론

- **A/D 과정**: 아날로그 → 디지털
- **샘플링 주파수** ≥ 원 신호 최고 주파수 × 2
- **앨리어싱 현상**: 샘플링 부족 → 왜곡 발생

## 10. 복원 필터

- 이상적 복원 필터 구현 어려움 → 나이퀴스트 주파수 초과 필요
- **계단 현상**: 0차 홀드 보간 시 발생

## 11. 구분구적법

정적분의 근사 계산:

```math
\lim_{n \to \infty} \sum_{k=1}^{n} f(x_k) \Delta x
```

## 12. 틸드와 헷 표기

- `x~`: x tilde
- `x^`: x hat

## 13. Z 변환

- 이산신호에서의 라플라스 변환 대응
- ROC 표현: 실선 (포함), 점선 (미포함)
- 임펄스 변환 시 상수 1 (전체 구간 의미)
- **유한 이산신호**: 폴 존재, 제로는 인수분해 시 가능
