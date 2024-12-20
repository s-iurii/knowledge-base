[[🐒 PostgreSQL]]

https://habr.com/ru/companies/otus/articles/861240/

```SQL
CREATE OR REPLACE FUNCTION get_filtered_data(start_date DATE, end_date DATE, status TEXT)
RETURNS TABLE(id INT, created_at DATE, status TEXT) AS $$
BEGIN    
RETURN QUERY EXECUTE FORMAT(        
'SELECT id, created_at, status         
FROM orders         
WHERE created_at BETWEEN %L AND %L           
AND status = %L',        
start_date, end_date, status    );
END $$ LANGUAGE plpgsql;
```


```SQL
SELECT * FROM get_filtered_data('2024-01-01', '2024-12-31', 'active');
```