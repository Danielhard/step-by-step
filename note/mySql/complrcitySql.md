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
