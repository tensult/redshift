=== Useful Redshift queries
**Get Copy command history with tableNames**
```sql
SELECT l.curtime,q.database, split_part(q.querytxt,' ', 2) AS tableName,l.filename
FROM stl_load_commits l, stl_query q
WHERE l.query=q.query AND l.curtime > '2019-10-25' ORDER BY l.curtime
```
