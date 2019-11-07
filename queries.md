## Useful Redshift queries
**Get Copy command history with tableNames**
```sql
SELECT l.curtime,q.database, 
SPLIT_PART(trim(replace(replace(lower(q.querytxt), 'copy', ''), 'analyze', '')),' ', 1) AS tableName,
l.filename 
FROM stl_load_commits l, stl_query q
WHERE l.query=q.query AND l.curtime > '2019-10-25' ORDER BY l.curtime
```

**Get queries matching to table**
```sql
SELECT * FROM stl_query WHERE STRPOS(querytxt, 'table_name') != 0;
```
