# *GROUP BY*와 *HAVING*의 차이
> GROUP BY란?
* 특정 열을 기준으로 삼아 해당하는 값을 그룹으로 모아주는 함수
```
SELECT position, SUM(earnings)
FROM EMPLOYEE
GROUP BY position
;

위에서 GROUP BY는 같은 포지션 별로 급여의 합을 보여주게 만든다
(ex. 사원 2500만원, 대리 3000만원 ...)
```
> HAVING이란?
* 그룹화된 대상 속에서 조건을 걸어, 그에 해당하는 값을 출력하기 위해 쓰이는 함수
```
SELECT position
FROM EMPLOYEE
GROUP BY position
HAVING SUM(earnings) > 40000000
;

위에서 HAVING은 포지션 별 급여의 합이 4000만원이 넘는 포지션 이름만 출력하게 만든다
(ex. 과장, 부장 ...)
```
> GROUP BY와 HAVING의 공통점
* 두 함수 모두 데이터들을 그룹으로 분류해 해당 그룹 안에서 기준이 되는 열별 통계 정보를 얻을 때 추가로 사용됨
* FROM 및 WHERE절 뒤에 위치해야 함
> GROUP BY와 HAVING의 차이점
> GROUP BY에는 직접적으로 집계함수를 사용할 수 없지만, HAVING에는 가능함
```
SELECT position
FROM EMPLOYEE
GROUP BY AVG(position) (불가능)
HAVING SUM(earnings) > 40000000 (가능)
;

HAVING에서 따로 집계함수를 사용하지 않는다면, SELECT의 불러올 컬럼에 적용하는 방법 등이 있음
```
> (MYSQL 기준) GROUP BY에는 ALIAS 사용 불가, HAVING에는 사용 가능함
```
SELECT position, SUM(earnings) AS ern_sum
FROM EMPLOYEE
GROUP BY ern_sum (불가능)
HAVING ern_sum > 40000000 (가능)
;
```
* GROUP BY에서 불가능한 이유? 실행순서 때문!
> 쿼리가 최종적으로 실행될 때는 별칭을 설정한 SELECT절이 GROUP BY보다 나중에 실행됨<br/>
> 따라서 먼저 실행된 GROUP BY절은 별칭을 알 수 없겠죠?<br/>
* GROUP BY 다음 실행순서가 HAVING, SELECT인데 그럼 HAVING은 왜 될까?
> 논리적으로 HAVING이 SELECT보다 먼저 실행되지만, HAVING은 SELECT의 별칭을 내부적으로 미리 참조할 수 있게 해줌<br/>
> But, 이것은 MYSQL에만 적용되는 내용이므로 다른 DBMS(Oracle 등)에서는 문제가 생길 수 있음

# *NULL*과 *NULL* 처리 함수
> NULL이란?
* 0 및 공백과는 다른, 값 자체가 입력되지 않아 무의 상태임을 나타내는 값
> NULL 처리 함수에는 어떤 것이 있나?
1. IFNULL
```
IFNULL (표현식1, 표현식2)
```
* 표현식1의 값이 NULL이면 표현식2의 값을 출력, NULL이 아니면 표현식1의 값을 그대로 출력
* 표현식들 간의 타입이 달라도 SQL이 자동으로 형변환을 시켜줌
2. NULLIF
```
NULLIF (표현식1, 표현식2)
```
* 표현식1과 표현식2의 값이 같으면 NULL, 다르면 표현식1의 값을 그대로 출력
3. COALESCE
```
COALESECE (표현식1, 표현식2, ...)
```
* 표현식이 여러 개 주어지는 경우 해당 표현식들 중 NULL이 아닌 최초의 값을 리턴함
* 모든 표현식이 NULL이라면 NULL 리턴
> 그렇다면 NULLIF와 COALESCE는 어떨 때 사용할까?
* NULLIF는 인자가 꼭 2개, COALESCE는 2개 이상도 가능함
* NULLIF는 특정 조건하에서 NULL을 처리할 때 주로 사용하고, (표현식 간의 값이 같다/다르다는 조건)
* COALESCE는 모든 NULL에 기본값을 지정할 때 주로 사용함
