# GROUP BY와 HAVING의 차이
> GROUP BY란?
* 특정 열을 기준으로 삼아 해당하는 값을 그룹으로 모아주는 함수
```
SELECT position, SUM(earnings)
FROM EMPLOYEE
GROUP BY position

위에서 GROUP BY는 같은 포지션 별로 급여의 합을 보여주게 만든다
(ex. 사원 2500만원, 대리 3000만원 ...)
```
> HAVING이란?
* 그룹화된 대상 속에서 조건을 걸어, 그에 해당하는 값을 출력하기 위해 쓰이는 함수
> GROUP BY와 HAVING의 공통점
