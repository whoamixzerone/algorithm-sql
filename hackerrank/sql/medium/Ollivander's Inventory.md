# [Ollivander's Inventory](https://www.hackerrank.com/challenges/harry-potter-and-wands/problem)

### 출처 - HackerRank
[Ollivander's Inventory](https://www.hackerrank.com/challenges/harry-potter-and-wands/problem)

#### 문제 풀이
두 테이블을 조인하고, non-evil 지팡이를 찾기 때문에 ```is_evil = 0```으로 조건을 걸어준다.  
그리고 지팡이 구매를 최소 금액으로 하려고 하기 때문에 조건을 걸어주는데 최소 금액을 찾기 위해 서브쿼리에서 찾아주는데  
**가장 중요한 점은 서브쿼리에서 power, age 조건이 중요하다.**  
메인 쿼리의 power, age와 서브쿼리의 power, age가 일치하는 것 중에 최소 금액을 뽑아야 한다.

### MySQL 풀이
```sql
select w.id, wp.age, w.coins_needed, w.power
from wands w
    join wands_property wp on w.code = wp.code
where wp.is_evil = 0
and w.coins_needed = (select min(w1.coins_needed)
                    from wands w1
                        join wands_property wp1 on w1.code = wp1.code
                    where wp1.is_evil = 0
                     and w1.power = w.power
                     and wp1.age = wp.age)
order by 4 desc, 2 desc;
```

### 다른 사람 풀이
```sql
WITH Wand_Cost_Ranks AS (
    SELECT 
        W.id, 
        WP.age, 
        W.coins_needed, 
        W.power, 
        ROW_NUMBER() OVER (PARTITION BY W.power, WP.age ORDER BY W.coins_needed) AS cost_rank
    FROM 
        Wands W
        JOIN Wands_Property WP ON W.code = WP.code
    WHERE 
        WP.is_evil = 0
)
SELECT 
    id, 
    age, 
    coins_needed, 
    power
FROM 
    Wand_Cost_Ranks
WHERE 
    cost_rank = 1
ORDER BY 
    power DESC, 
    age DESC;
```

```sql
SELECT id, age, coins_needed, power
FROM (SELECT code, power, MIN(coins_needed) as coins_needed FROM WANDS GROUP BY code, power) AS M
    JOIN WANDS AS W
    ON W.code = M.code AND W.power = M.power and W.coins_needed = M.coins_needed
    JOIN WANDS_PROPERTY AS P
    ON M.code = P.code
WHERE P.is_evil = 0
ORDER BY W.power DESC, P.age DESC;
```