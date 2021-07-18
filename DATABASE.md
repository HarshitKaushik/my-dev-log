# RDBMS
## SQL
### Postgres
- How to select first row in each GROUP BY group? 
```sql
-- on databases that support CTE and windowing functions
with summary as (
select
	p.id,
	p.customer,
	p.total,
	row_number() over(partition by p.customer
order by
	p.total desc) as rank
from
	PURCHASES p)
select
	*
from
	summary
where
	rank = 1

-- supported by any database
select
	MIN(x.id),
	-- change to MAX if you want the highest
 x.customer,
	x.total
from
	PURCHASES x
join (
	select
		p.customer,
		MAX(total) as max_total
	from
		PURCHASES p
	group by
		p.customer) y on
	y.customer = x.customer
	and y.max_total = x.total
group by
	x.customer,
	x.total
```
