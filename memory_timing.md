# 메모리 타이밍 주요 용어 정리

## tCL (CAS Latency)

- CAS: Column Address Strobe / Select
- 메모리에서 **읽기/쓰기 요청 후 첫 데이터가 출력될 때까지의 클럭 수**
- 램 타이밍의 대표적인 값
- **낮을수록 좋음**

## tRCD (RAS to CAS Delay)

- RAS: Row Address Strobe
- 행(RAS)을 선택한 후 열(CAS)을 선택하기까지 걸리는 클럭 수
- **낮을수록 좋음**, 성능에 **약 1%** 영향

## tRP (RAS Precharge)

- 다음 접근 전, 현재의 행을 **닫고** 새로운 행을 준비하는 데 걸리는 시간
- 충전 시간에 해당
- 낮을수록 좋으나 **tCL, tRCD와 조화 필요**
- 너무 낮으면 **안정성 문제**

## tRAS (Row Active Time)

- RAS가 활성화된 후 프리차지까지의 시간
- 모든 메모리 명령의 시작점
- 보통: `tRAS ≈ tCL + tRCD + α`
- **낮을수록 좋음**

## SPD (Serial Presence Detect)

- 메모리 모듈 내에 저장된 정보 칩
- **JEDEC 표준**
- 메모리 타이밍 자동 감지에 사용됨

## XMP (Extreme Memory Profile)

- **인텔의 오버클럭 메모리 프로파일**
- JEDEC 비표준, BIOS에 고급 타이밍 정보 제공
- 고급 메모리 모듈에서 지원

## CR (Command Rate)

- 메모리 컨트롤러 → 메모리까지 명령이 도달하는 시간
- 일반적으로 **1T 또는 2T**
- **낮을수록 성능↑**, 2T는 안정성을 위한 설정

## tRC (Row Cycle Time)

- RAS에서 데이터를 읽기까지 걸리는 전체 사이클
- 계산식: `tRC = tRAS + tRP + α`
- **낮을수록 좋음**

## tRFC (Row Refresh Cycle Time)

- 뱅크의 RAS를 리프레시하는 데 걸리는 클럭 수
- 낮을수록 좋지만, **안정성에 직접적인 영향**

## tREF (Refresh Time)

- 주기적인 리프레시 수행 시간 (단위: μs)
- 낮을수록 좋지만 안정성과 트레이드 오프 있음
