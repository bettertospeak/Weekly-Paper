# DAG와 TASK의 관계
> 🔁 DAG (Directed Acyclic Graph) 유향 비순환 그래프
  * 하나의 방향으로 나아가고, 되돌아오는 등 순환하지 않는 작업 그래프
  * 관계와 의존성을 가진 작업들의 집합
  - 제시간에, 정확한 순서로, 이슈없이 작업을 실행시킴
> ❗️ DAG의 특징
  1. 파이썬 코드로 정의됨
  2. 일정한 간격, 스케줄에 따라 주기적으로 실행시키기 위한 구조임
  3. Airflow 등을 통해 DAG 구조와 실행 현황을 시각화로 확인할 수 있음

> 📤 TASK
 * 가장 기본이 되는 작업 단위
 * Operator를 통해 정의되며, 간단한 함수 실행 ~ GCP 연동 작업까지 폭넓게 가능함

> 🤝 DAG와 TASK
* DAG에는 Operator로 정의된 TASK 세트가 포함되어있음
  - TASK들끼리 관계와 의존성을 가지고있고, 그것을 유향 비순환으로 처리함
* DAG에서 공통 정보를 정의하고, 그를 바탕으로 TASK가 실행됨
  - 공통 정보 기반 각 TASK가 정의되면, 실행 순서를 설정해 TASK를 순서대로 실행함

# Operator들의 종류와 활용 사례
> ✅ 학습한 Operator들
1. (01) EmptyOperator : 아무 동작도 하지 않지만, TASK의 흐름 제어를 위해 존재
2. (02-06) PythonOperator : 파이썬 함수를 Airflow에서 실행 가능하도록 해줌
3. (07-08) BranchPythonOperator : 조건에 따라 특정 TASK만 실행하고, 나머지는 건너뛰도록 만들어줌 → 파이썬의 if-else문 역할
4. (13-14) HttpOperator : http로부터 요청을 받고, 응답을 반환함
5. (15) SQLExcuteQueryOperator : 주어진 데이터에 대해 SQL 쿼리를 실행시킴
6. (17,19) BigQueryCreateEmptyDatasetOperator : BigQuery 관련 Operator 중, BigQuery에 빈 데이터셋을 생성해주는 것
7. (18-19) BigQueryInsertJobOperator : BigQuery 관련 Operator 중, BigQuery에 컬럼 및 값을 삽입하는 것
8. (20) GCSCreateBucketOperator : GCS 관련 Operator 중, 버킷을 생성하는 것
9. (21) GCSToBigQueryOperator, BigQueryToGCSOperator : 각각 GCS에서 BigQuery로, BigQuery에서 GCS로 파일을 내보내는 것
10. (22) BigQueryToPostgresOperator, PostgresToGCSOperator : 각각 BigQuery에서 Postgres로, Postgres에서 BigQuery로 파일을 내보내는 것

> 💥 이외의 Operator들
1. (Python) PythonVirtualenvOperator : 자동으로 생성되고 삭제되는 env(가상환경)에서 함수 실행 가능 → but, 전역변수를 사용할 수 없어 사용할 변수를 모두 함수 안에 기재해야함
2. (SQL) SQLThresholdCheckOperator : 특정 SQL 쿼리를 실행할 때, 최솟값과 임계값을 비교해볼 수 있음 → min_threshold, max_threshold 파라미터를 통해
