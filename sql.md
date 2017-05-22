```sql
SELECT prod_name, prod_price FROM products WHERE (ven_id = 1002 OR vend_id = 1003) AND prod_price >=10;
SELECT prod_name, prod_price FROM products WHERE ven_id IN (1002, 1003) ORDER BY prod_name;
SELECT prod_name, prod_price FROM products WHERE ven_id NOT IN (1002, 1003) ORDER BY prod_name;
-- % 表示任何字符出现任意次数;  _ 下划线匹配单个字符
SELECT prod_name, prod_price FROM products WHERE prod_name LIKE 'jet%';
SELECT prod_name, prod_price FROM products WHERE prod_name LIKE '_jet';
```
