#### 一.插入数据

```
INSERT INTO table_name ( field1, field2,...fieldN )
                       VALUES
                       ( value1, value2,...valueN );
//example
insert into person (name ,age)
values("danhuang",22)
```

#### 二.查询数据

```
SELECT column_name,column_name
FROM table_name
[WHERE Clause]
[LIMIT N][ OFFSET M]

//example
select * from person  where age >20 and age<66 limit  3//where表示条件 limit 设定返回数量
```

#### 三.更新数据

```
UPDATE table_name SET field1=new-value1, field2=new-value2
[WHERE Clause]
//example
update person  set name="xiaodanhuang" where person_id=1
```

#### 四.删除数据

```
DELETE FROM table_name [WHERE Clause]
//example
delete from person where person_id=1
```

#### 五.like 语句

```
SELECT field1, field2,...fieldN 
FROM table_name
WHERE field1 LIKE condition1 [AND [OR]] filed2 = 'somevalue'
//example
select* from person where name like "%a%"
```

#### 六.union操作符

###### MySQL UNION 操作符用于连接两个以上的 SELECT 语句的结果组合到一个结果集合中。多个 SELECT 语句会删除重复的数据。

```
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions]
UNION [ALL | DISTINCT]
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions];
//example
select* from person where name like "%a%" union select *  from person where person_id=2
```

#### 七.order by

order by 用于排序,ASC 升序，desc 降序，默认升序

```
SELECT field1, field2,...fieldN table_name1, table_name2...
ORDER BY field1, [field2...] [ASC [DESC]]
//example
select* from person order by person_id desc
```

#### 八.GROUP BY 语句





