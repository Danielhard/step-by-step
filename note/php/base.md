# PHP基础
#(本篇持续更新)
##  语法，变量，数据类型
   ## 语法
   1. php以<?php 开头 以?>结束  文件名后缀为.php
   2. php文件html标签以及php脚本代码
   3. php每行代码以分号结束,否则会输出错误
   ```
    <?php
    $a = "测试";
    if(1>2){
       echo "hello PHP";
    }else{
       echo "my first php $a";
    }
    ?>

   ```
   ## 变量
   ### 规则
   1. php变量声明必须以$符开头（$a）
   2.变量名必须以字母或者下划线字符开始
   3.变量名只能包含字母数字字符以及下划线（A-z、0-9 和 _ ）,不能包含空格，且严格区分大小写。
   4. PHP是弱类型语言所以变量不必声明类型和JS类似 

   ###作用域范围

  ##数据类型
  + 数组
   ```
   $arrayTest = array('0'=> '苹果', 1=> '测试');
   echo $arrayTest[0] // 苹果
   ```


## php会话机制session 
   ```
     session_start();//一般在配置文件中初始化打开。可以在全局使用，设置存储变量
     // a.php
     $_SESSION['views'] = 1;
     // b.php
     echo $_SESSION['views'] // 1
   ```   