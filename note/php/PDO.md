# PDO，PHP的数据对象， 拓展为PHP访问数据库定义了一个轻量级的一致接口。
**提供了一个数据访问抽象层，这意味着，不管使用哪种数据库，都可以用相同的函数（方法）来查询和获取数据。**

## ---为了更好的理解，先上个DEMO---;
  ```
    <?php
      header("Content-Type: text/html;charset=utf-8"); //加个脑袋，正常流程
      $dbms = "mysql";   //数据库类型
      $host= "localhost"; //数据库主机名
      $dbName = "zzxPHP";   //使用的数据库
      $user ="root";  //数据库连接用户名
      $pass = "";   //对应的密码
      $dsn = "$dbms:host=$host;dbname=$dbName;charset=utf8"; //如果需要规定字符串编码，可以加在这，也可以用PDO::_construct 或者exec一些其他API
      try{
         $dbh = new PDO($dsn,$user,$pass); //初始化一个PDO对象
      //   foreach($dbh->query("SELECT * FROM `news`") as $row){ 你还可以进行一次搜索操作
      //      print_r($row); //这里把库里的数据拎出来晒一晒
      //   }
        $sql = "INSERT INTO `test`(`test_title`,`test_img`,`test_content`,`test_time`) VALUES ('c噗噗噗','c图片新地址','c新闻新内容','2017-09-28')";
        $res = $dbh->exec($sql); //执行一条 SQL 语句，并返回受影响的行数 ,好用- -
        echo "插入成功，受影响的行数" . $res;

        //默认这个不是长连接，如果需要数据库长连接，需要最后加一个参数：array(PDO::ATTR_PERSISTENT => true) 变成这样：
        $db = new PDO($dsn, $user, $pass, array(PDO::ATTR_PERSISTENT => true));

        $dbh = null;  //记得关闭
        //echo "连接成功<br/>";
      }catch(PDOException $e){
        die("ERROR:" . $e.getMessage() . "<br/>");
      }
    ?>
  ``` 

  ## The Next: 


_ _ _

[返回主目录](https://github.com/Danielhard/step-by-step/blob/master/note/php/index.md)
