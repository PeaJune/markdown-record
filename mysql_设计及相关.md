## 创建table

```mysql
create table prj( 
	   id int primary key not null auto_increm
    -> ip varchar(20) primary key,
    -> online varchar(20))
    -> ;

create table prj_online(
    -> ip varchar(20) primary key,
    -> timestamp0 varchar(30),
    -> timestamp1 varchar(20));
```



## 表与表之间的关系

```mysql
select * from prj a left join prj_online b on a.ip = b.ip;

表与表关系
select * from prj a left join prj_online b on a.ip = b.ip where a.ip='192.168.8.1';

插入一个数据，如果存在，则更新
insert into prj(ip, moved) values("192.168.8.3", 1) on duplicate key update prj.moved=values(moved);

insert into prj(ip, online, moved) values("192.168.8.3",'1', '0') on duplicate key update prj.online=values(onlinee) , prj.moved=values(moved);

## 重命名table
alter table aibee_beijing_showroom-cs rename to aibee_beijing_showroom_cs
```



## 利用存储进程批量添加与删除表项

```mysql
DELIMITER $
CREATE PROCEDURE t0add_property () 
BEGIN
  DECLARE tb VARCHAR (64) ;
  DECLARE done INT DEFAULT FALSE ;
  DECLARE cur CURSOR FOR 
  SELECT 
    table_name 
  FROM
    information_schema.tables 
  WHERE table_schema = 'abdms' ;
  DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE ;
  OPEN cur ;
  posLoop :
  LOOP
    FETCH cur INTO tb ;
    IF done 
    THEN LEAVE posLoop ;
    END IF ;
    SET @_SQL = CONCAT('alter table ', tb, " add moved_timestamp varchar(20) default 0 ", " , "," add online_timestamp varchar(20) default 0;");
    PREPARE stmt FROM @_SQL ;
    EXECUTE stmt ;
    DEALLOCATE PREPARE stmt ;
  END LOOP posLoop ;
  CLOSE cur ;
END $
DELIMITER ;
```

