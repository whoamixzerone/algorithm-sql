# [Challenges](https://www.hackerrank.com/challenges/challenges/problem)

### 출처 - HackerRank
[Challenges](https://www.hackerrank.com/challenges/challenges/problem)

#### 문제 풀이
두 테이블을 조인하고, 학생이 낸 총 과제 수 출력  
hacker_id, name으로 그룹화를 하고 조건으로 최대 도전 횟수 구한 값과  
동일한 수의 과제를 냈을 때 최대 도전 횟수보다 적으면 제외

### MySQL 풀이
```sql
select h.hacker_id, h.name, count(*) as challenges_created
from hackers h
    join challenges c on h.hacker_id = c.hacker_id
group by h.hacker_id, h.name
having challenges_created = (select max(t.challenges_created) as challenges_created
                           from (select count(*) as challenges_created
                                from challenges
                                group by hacker_id) t)
or challenges_created in (select t1.challenges_created
                         from (select hacker_id, count(*) as challenges_created
                              from challenges
                              group by hacker_id) t1
                          group by t1.challenges_created
                          having count(*) = 1)
order by 3 desc, 1 asc;
```

### 다른 사람 풀이
```sql
WITH ChallengeCounts AS (
  SELECT h.hacker_id, h.name, COUNT(*) AS num_challenges,
    RANK() OVER (ORDER BY COUNT(*) DESC) AS rank,
    COUNT(*) OVER (PARTITION BY COUNT(*)) AS count
  FROM Hackers h
  JOIN Challenges c ON h.hacker_id = c.hacker_id
  GROUP BY h.hacker_id, h.name
)
SELECT hacker_id, name, num_challenges
FROM ChallengeCounts
WHERE rank = 1 OR count = 1
ORDER BY num_challenges DESC, hacker_id
```

```sql
WITH counter AS (
	SELECT hackers.hacker_id, hackers.name, COUNT(*) AS cnt
  FROM Challenges
    INNER JOIN hackers ON challenges.hacker_id = Hackers.hacker_id
  GROUP BY hackers.hacker_id, hackers.name
)

SELECT counter.hacker_id, counter.name, counter.challenges_created
FROM counter
WHERE cnt = (SELECT MAX(cnt) FROM counter)
OR cnt IN (SELECT cnt FROM counter GROUP BY cnt HAVING count(*) = 1)
ORDER BY counter.cnt DESC, counter.hacker_id
```