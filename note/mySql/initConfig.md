# 有关PHP怎么和MySQL开心的在一起。(常见API)
  ## 首先需要创建连接数据库的实例方法
  + 创建数据库连接
     ```
        <?php 
          // 假定数据库用户名：root，密码：空，数据库：RUNOOB ,本地      localhost 数据库默认用户root ,密码空
          $con=mysqli_connect("localhost","root","","RUNOOB"); 
          if (mysqli_connect_errno($con)) 
          { 
              echo "连接 MySQL 失败: " . mysqli_connect_error(); 
          } 
          
          // 修改数据库连接字符集为 utf8  
          mysqli_set_charset($con,"utf8"); 
          
          mysqli_close($con);//手动断开连接
        ?>
     ```
  + 设置客户端默认字符集,修改数据库连接字符集为utf-8,不然会存进去一坨乱码
      ```
       mysqli_set_charset(connection,charset);

      ```

    |参数|描述|
    |:-:|:-:|
    |connection|	必需。规定要使用的 MySQL 连接。|
    |charset|	必需。规定默认字符集。|
    |返回值：|	如果成功则返回 TRUE，如果失败则返回 FALSE。|
    |PHP 版本：|	5.0.5+|

  + 执行针对数据库的查询
    ```
        <?php 
          // 假定数据库用户名：root，密码：123456，数据库：RUNOOB 
          $con=mysqli_connect("localhost","root","123456","RUNOOB"); 
          if (mysqli_connect_errno($con)) 
          { 
              echo "连接 MySQL 失败: " . mysqli_connect_error(); 
          } 
           
          // 执行查询
          mysqli_query($con,"SELECT * FROM websites");
          mysqli_query($con,"INSERT INTO websites (name, url, alexa, country)
          VALUES ('百度','https://www.baidu.com/','4','CN')");
           
          mysqli_close($con);
        ?>
    ```  
    **语法**
    ```
    mysqli_query(connection,query,resultmode);
    ```
    
    |参数|描述|
    |:-:|:-:|
    |connection|	必需。规定要使用的 MySQL 连接。|
    |query|	必需，规定查询字符串|
    |resultmode|可选。一个常量。可以是下列值中的任意一个：MYSQLI_USE_RESULT（如果需要检索大量数据，请使用这个）MYSQLI_STORE_RESULT（默认）|
    |返回值|针对成功的 SELECT、SHOW、DESCRIBE 或 EXPLAIN 查询，将返回一个 mysqli_result 对象。针对其他成功的查询，将返回 TRUE。如果失败，则返回 FALSE。|
    |PHP 版本：|5+|
    |更新日志：	|在 PHP 5.3.0 中新增了异步查询的功能。|