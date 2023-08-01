# [Contest Leaderboard](https://www.hackerrank.com/challenges/contest-leaderboard/problem)

### 출처 - HackerRank
[Contest Leaderboard](https://www.hackerrank.com/challenges/contest-leaderboard/problem)

#### 문제 풀이
서브 쿼리에서 그룹을 hacker_id, challenge_id로 그룹화 해서 같은 challenge_id에서 최대 값을 구하고,
서브 쿼리에서 나온 테이블과 hackers 테이블을 조인하고 hacker_id, name으로 그룹화 하고  
총 점수가 0이면 제외를 하도록 조건을 준다.

### MySQL 풀이
```sql
select h.hacker_id, h.name, sum(t.score) as total_score
from (select hacker_id, max(score) as score
      from submissions
      group by hacker_id, challenge_id
     ) t
     join hackers h on t.hacker_id = h.hacker_id
group by h.hacker_id, h.name
having total_score > 0 
order by 3 desc, 1 asc;
```

### 다른 사람 풀이
```sql
WITH total_score AS (
    SELECT DISTINCT
        h.hacker_id,
        h.name,
        s.challenge_id,
        MAX(s.score) OVER (PARTITION BY h.hacker_id, s.challenge_id) AS max_score_per_subm
    FROM
        Hackers h JOIN Submissions s ON h.hacker_id = s.hacker_id
)
SELECT
    hacker_id,
    name,
    SUM(max_score_per_subm) AS total
FROM total_score
GROUP BY
    hacker_id,
    name
HAVING SUM(max_score_per_subm) > 0
ORDER BY
    total DESC,
    hacker_id
```