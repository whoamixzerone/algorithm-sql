# [SQL Project Planning](https://www.hackerrank.com/challenges/sql-projects/problem)

### 출처 - HackerRank
[SQL Project Planning](https://www.hackerrank.com/challenges/sql-projects/problem)

#### 문제 풀이
서브 쿼리로 end_date에 없는 start_date 값을 구하고 마찬가지로 start_date에 없는 end_date 값을 구한다.  
2개의 서브 쿼리로 구하면 cross join이 되서 여러 값들이 나오는데 그 중에 start_date가 end_date보다 크면 안되기 때문에 조건을 걸어주고  
start_date와 end_date의 날짜가 연관되는 값으로 매칭하기 위해 start_date로 그룹화를 해서 end_date를 최소값으로 지정한다.  
마지막으로 정렬은 프로젝트 기간이 적은 순으로 하기 때문에 datediff로 종료일에서 시작일을 빼주고 같으면 start_date로 오름차순 정렬한다.

### MySQL 풀이
```sql
select start_date, min(end_date) as end_date
from (select start_date
     from projects
     where start_date not in (select end_date from projects)) a,
     (select end_date
     from projects
     where end_date not in (select start_date from projects)) b
where start_date < end_date
group by start_date
order by datediff(min(end_date), start_date) asc, 1 asc;
```

### 다른 사람 풀이
```sql
with sub1 as (
  select start_date, row_number() over (order by start_date) rnk1
  from projects
  where start_date not in (select end_date from projects)
),
sub2 as (
  select end_date, row_number() over (order by end_date) rnk2
  from projects
  where end_date not in (select start_date from projects)
)
select sub1.start_date, sub2.end_date
from sub1 join sub2 on sub1.rnk1 = sub2.rnk2
order by (sub2.end_date - sub1.start_date), sub1.start_date
```