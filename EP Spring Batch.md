## EP Spring Batch 구조

**스케줄링 관리 및 실행 방법**

크론탭 프로그램 활용.

![image](https://user-images.githubusercontent.com/40616436/94753313-d3ff5280-03c8-11eb-850b-19ac53bb489f.png)

CommandLineJobRunner

- Spring Batch를 명령행으로 실행할 수 있다.

  ~~~html
  java org.springframework.batch.core.launch.support.CommandLineJobRunner jobPath <options> jobIdentifier (jobParameters)
  ~~~



**AS-IS EP 프로세스**

1. 제휴 업체에 나갈 데이터 조회(full query) 후 파일 생성 진행
2. 생성 파일 ftp 전송 진행
3. 제휴 업체에게 url 제공



**EP 이슈 사항(네이버)**

- 네이버에 제공되는 데이터 : 약 800만건.
- 데이터 조회 및 파일 생성되는 시간 : 4시간 30분
- 컬럼 및 테이블 추가로 프로세스 진행 예정 시간 초과 : 6시간 30분



**EP 이슈 사항에 대한 분석**

- FULL QUERY 조회 후 10,000건씩 패치로 인해 데이터를 가져오는데, 예정 패치 시간 OVER
- QUERY 자체가 너무 무거워 패치에서 가져오는 시간 이슈 발생



**EP 이슈 사항에 대한 해결 방안**

- QUERY 중  function & procedure, full 조회 부분 분리
- 위 부분 제외한 QUERY 조회 후 TEMP TABLE에 INSERT
- TEMP TABLE과 function & procedure, full 조회 분리 부분 JOIN
- 파일 생성 프로세스 3등분으로 나누어 병렬 처리



**EP 개선 사항**

- INSERT 진행 시간 : 40분
- JOIN 및 파일 생성 시간 : 1시간 10분

