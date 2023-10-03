# 목차 
[1. 병렬처리](#병렬처리) <br>
[2. 병렬처리의 단위](#병렬처리의-단위) <br>
[3. 병렬컴퓨터의 분류](#병렬-컴퓨터의-분류) <br><br>

## 병렬처리
다수의 프로세서들이 여러 개의 프로그램들, 한 프로그램의 분할된 부분들을 분단하여 `동시에 처리`하는 기술 <br>

- 선결 조건 <br>
1. 작고 저렴하며 고속인 프로세서들의 사용이 가능해야 함 <br>
2. 한 프로그램을 여러 개의 작은 부분들로 분할하는 것이 가능해야 함(분할 부분들 병렬처리 결과 = 순차 처리 결과 같아야 함 ) <br>

## 병렬처리의 단위
작업 단위 병렬성 (Job-level paralleslism) <br>
- 독립적인 작업 프로그램 단위로 병렬처리 (ex. 성적관리 프로그램, 실험 데이터 처리 프로그램) <br><br>

테스크 단위 병렬성 (Task-level parallelism) <br>
- 하나의 큰 작업을 기능에 따라 분할한 작은 프로그램(Task) 단위로 병렬처리 (ex. 로봇 제어 프로그램) <br>
- 프로세서들간의 정보 교환 필요 <br><br>

스레드 단위 병렬성 (Thread-level paralleliesm) <br>
- 동시에 처리될 수 있는 가장 작은 크기의 독립적인 단위 = 스레드 <br>
- 스레드 단위 병렬처리 <br><br>

명령어 단위 병렬처리 (Instruction-level parallelism) <br>
- 데이터 의존성 존재하지 않는 여러 명령어들을 동시에 수행하는 병렬처리 <br><br>

## 병렬 컴퓨터의 분류
Flynn의 분류 (구조적 특징에 따른 분류) <br>
- 명령어 스트림 <br>
  프로세서에 의해 실행되기 위하여 순서대로 나열된 명령어 코드들의 집합 <br>
- 데이터 스트림 <br>
  그 명령어들을 실행하는데 필요한 순서대로 나열한 데이터들의 집합 <br><br>

프로세서들이 처리하는 명령어와 데이터 스트림의 수에 따른 분류 <br>
- SISD(Simple Instruction, Single Data) <br>
  한번에 한 개씩 명령어와 데이터를 순서대로 처리하는 단일 프로세서 시스템(파이프 라이닝, 슈퍼 스칼라 구조를 이용)
  `단일 명령어로 단일 데이터 처리` <br>
  실제로는 1:1 처리기 때문에 병렬처리의 개념이 아니다. <br>
  (순차적 폰 노이만 컴퓨터) <br>

- SIMD(Single Instruction, Multi Data) <br>
  `단일 명령어로 복수 데이터 처리` (대량 데이터 처리에 응용) <br>
  배열 프로세서 <br>
  
- MISD(Multi Instruction, Single Data) <br>
  `복수 명령어로 단일 데이터 처리` <br>
  N개의 프로세서들이 서로 다른 명령어들을 실행 하지만 실제 데이터는 한가지만 처리함 -> 비현실적 <br>

- MIMD(Multi Instruction, Multi Data) <br>
  `복수 명령어로 복수 데이터 처리` (병렬 처리 컴퓨터의 궁극적인 목표) <br>
  N개의 프로세서들이 서로 다른 명령어들과 데이터들을 처리 <br>
  - 밀결함 시스템 <br>
    - 공유 기억장치 구조 <br>
    - 다중 프로세서 시스템 <br>
  
  - 소결함 시스템 <br>
    - 지역 기억장치를 가진 독립적인 컴퓨터 모듈로 구성 <br>
    - 프로세서간 통신은 메시지 전송 방식을 이용 <br>
    - 다중 컴퓨터 시스템 <br><br>

기억장치 엑세스 모델에 따른 분류 <br>
- 균일 기억장치 엑세스(UMA, Uniform Memory Access) <br>
  모든 프로세서들이 상호 연결망에 의해 주기억장치를 공유 <br>
  프로세서들은 주기억장치의 어느 영역이든 엑세스 가능, 걸리는 시간도 동이 <br>
  
  하드웨어 간단, 프로그래밍 용이 <br>
  시스템 크기에 한계 <br><br>

- 불균일 기억장치 엑세스(NUMA, Non-Uniform Memory Access) <br>
  다수의 UMA 모델이 상호연결망에 의해 접속 <br>
  분산 공유 기억장치 구조 <br>
  기억 장치 엑세스 시간은 기억장치의 위치에 따라 달라짐 <br>
  더 큰 규모 시스템 <br><br>

- 무 원격 기억장치 엑세스(NORMA, NO-Remote Memory Access) <br>
  프로세서가 원격 기억장치는 직접 엑세스 못하는 시스템 <br><br>

시스템 구성 방법에 따른 분류
- 대칭적 다중프로세서 (SMP, Symmetric Multiprocessors) <br>
  - 64개 이하의 프로세서들을 가지는 중대형급 시스템 <br>
  - 완전 공유 구조(프로세서들이 시스템 내의 모든 자원을 공유) <br>
  - 시스템 내 하나의 OS만 존재 <br>
  - 대칭적 <br>
    - 모든 프로세서들이 필요시 직접 OS 코드 수행 <br>
    - 모든 프로세서들이 자원을 동등한 권한으로 사용 <br><br>

- 대규모 병렬프로세서 (MPP, Massively Parallel Processors) <br>
  - 무공유 구조를 기반으로 하는 대규모 병렬처리 시스템 <br>
  - 수천, 수백개의 프로세싱 노드들로 구성 <br>
  - 간단한 구조의 노드 프로세서 사용 <br>
  - 마이크로 커널 수준의 노드 OS 탑재 <br>
  - 노드간 통신은 메세지 전송 방식 이용 <br>
  - 복잡도 높은 상호연결망 이용 <br><br>

- 캐시 일관성 NUMA (CC-NUMA, Cache-Coherent NUMA) <br>
  - 독립적인 노드들이 상호 연결망에 의해 접속 <br>
  - 모든 노드들이 캐시 및 주기억장치들 사이에 데이터 일관성 유지 <br>
  - 시스템 내의 모든 기억장치들이 전역 주소공간을 가지는 분산 공유 기억장치 시스템으로 구성 <br>
  - 소프트웨어 변경 없이 SMP 보다 더 큰 시스템 구축 가능 <br><br>