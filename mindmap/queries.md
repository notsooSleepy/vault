---
tags:
  - child
aliases:
---
2025-11-15 13:28
# queries
1. ==SELECT==
2. ==FROM==
```sql
SELECT * FROM table;
```

3. ==AS==
```sql
SELECT field AS field_alias FROM table;
```

4. ==SELECT DISTINCT==
```sql
SELECT DISTINCT year_hired FROM employees;
```
takes unique values from 'year_hired' field
```sql
SELECT DISTINCT depth_id, year_hired FROM employees;
	``` 
![[Pasted image 20251115134239.png|150]]
and select unique combination of two fields

5. ==CREATE VIEW== 
creates a view **which is a saved query for reuse not table**
```sql
CREATE VIEW employee_hired_years AS
SELECT id, name, year_hired
FROM employees;
```
that you can query from
```sql
SELECT id, name
FROM employee_hire_years;
```

# References
