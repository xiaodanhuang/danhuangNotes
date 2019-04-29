#### 一.创建数据表

    CREATE table table_name (column_name column_type);

    create table if not exist family (
        `person_id` INT UNSIGNED AUTO_INCREMENT,
        `person_name` varchar(128) default null,
        `age` INT default null,
         PRIMARY KEY ( `person_id` )
        )ENGINE=InnoDB DEFAULT CHARSET=utf8;

#### 二.删除数据表

```
drop table table_name;
```

#### 三.修改数据表

```
alter  table  family rename to person//修改表名
alter  table person modify person_name varchar(20)//修改表字段的数据类型
alter  table person change person_name name varchar(20)//修改表字段的名称
alter  table person add  birthday DATETIME//添加表字段
alter  table person drop   birthday DATETIME//删除表字段
```

-2019.04.29

