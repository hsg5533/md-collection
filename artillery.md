# 1. 설치

```bash
npm install -g artillery
```

## 2. 사용

- 아래의 명령어로 간단하게 테스트를 진행할 수 있다

```bash
artillery quick -c 100 -n 500 -o report.json http://localhost:3030
# -c: 가상의 사용자 수
# -n: 요청 횟수
# -o: 결과파일 생성
```

- 단위는 ms(millisecond)이며 총 요청 수, 평균 응답 시간, HTTP STATUS별 응답 수 등을 표시해준다

```bash
http.codes.200 : 200번으로 응답이 온 요청 수
http.requests : 총 요청 수
http.response_time : 응답 시간
min : 최소 응답 시간
max : 최대 응답 시간
median : 평균 응답 시간
p50: 전체 HTTP transanction 중 가장 빠른 것 부터 50% 까지
p95: 전체 HTTP transanction 중 가장 빠른 것 부터 95% 까지
p99: 전체 HTTP transanction 중 가장 빠른 것 부터 99%
```

- 아래의 명령어로 json파일을 html파일로 변환하여 그래프로 볼 수 있다.

```bash
artillery report report3.json
```
