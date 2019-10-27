## MySQL复杂查询语句

  + sql语句当中条件查询配合函数
    1. 查询数量 count() 函数
    ```
     SELECT count(字段名称) FROM `table_name`  WHERE `condition`.
    ```
    2. min函数(字段名称 不能为所有条件*) 求最小值
    ```
     SELECT min(比如生日) FROM `table_name`  WHERE `condition`.

     SELECT min(i_name) , `table_name.*` <!-- 使用函数并且还需查询表中其他字段  .*  固定格式--> FROM `table_name`.
    ```
    3. max函数求最大值。用法同上
    4. sum() 求和
    5. sqrt() 求平方根
    6. rand() 随机数
    7. now() 获得当前时间
      ```
      SELECT now()
      ```
    8. concat()拼接字符串函数
       ```
       SELECT concat('AAA','BBB ')
       ```  

  + where子句，条件查询
  1.  >=  <=  
      ```
       SELECT * FROM `table_name` WHERE `leter` <= ''  AND `leter` >= ''
      ```   
  2.  BETWEEN 
      ```
        SELECT * FROM `table_name` WHERE `leter` BETWEEN '' AND ''
      ```     
  3.  SQL 中 = 是完全匹配 , LIKE 关键字 'pattern leter %'  % 是通配符   (模糊查询)
     ```
       SELECT * FROM `table_name` WHERE name LIKE 'letter%'    -- 找出以什么字符开头
       SELECT * FROM `table_name` WHERE name LIKE '%letter%'    -- 只要包字符就可以搜
       SELECT * FROM `table_name` WHERE name LIKE '%letter'   -- 找出以什么字符结尾
     ```
 
  + where 子句复杂查询
    1. ORDER BY  排序
       ```
        SELECT * FROM `table_name` ORDER BY `leter` DESC  (倒序)   -- 不添加DESC 默认为正序  (ASC 正序 可省略 )
       ```
    2. LEFT JOIN ON  左连接查询 关键字会从左表 (table_name1) 那里返回所有的行，即使在右表 (table_name2) 中没有匹配的行
       ```
         SELECT   `tableA_name`.`tableA_letter`,`tableB_name`.`tableB_letter` FROM  `tableA_name` LEFT JOIN `tableB_name`  ON   `tableA`.id=`tableB`.parent_id  
       ```
   + join 查询    
    1. RIGHY JOIN ON 右连接查询  关键字会右表 (table_name2) 那里返回所有的行，即使在左表 (table_name1) 中没有匹配的行。
       ``` 
        SELECT `column_name` FROM `tableA_name` RIGHT JOIN `tableb_name` ON `tableA`.id = `tableB`.parent_id
       ```
    2. FULL JOIN  ON 全连接查询 只要其中某个表存在匹配，FULL JOIN 关键字就会返回行。
       ```
        SELECT `column_name` FROM `tableA_name` FULL JOIN `tableb_name` ON `tableA`.id = `tableB`.parent_id
       ```
    3. INNER JOIN ON 内连接查询   在表中存在至少一个匹配时，INNER JOIN 关键字返回行
      ```
       SELECT `column_name` FROM `tableA_name` INNER JOIN `tableb_name` ON `tableA`.id = `tableB`.parent_id
      ```

    + Union操作符 UNION 操作符用于合并两个或多个 SELECT 语句的结果集，UNION 内部的 SELECT 语句必须拥有相同数量的列。列也必须拥有相似的数据类型。   同时，每条 SELECT 语句中的列的顺序必须相同。
      ```
        SELECT column_name(s) FROM table_name1
        UNION
        SELECT column_name(s) FROM table_name2
      ```
     