# PHP基础
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
   2. 变量名必须以字母或者下划线字符开始
   3. 变量名只能包含字母数字字符以及下划线（A-z、0-9 和 _ ）,不能包含空格，且严格区分大小写。
   4. PHP是弱类型语言所以变量不必声明类型和JS类似 

   ### 作用域范围
   1. 局部作用域(local)
   2. 全局作用域(global)
      ```
       <?php
         $c = '全局的';
         function test(){
          $d = '局部的'; //局部变量
           echo $d; 
           global $c; //访问全局作用域
           echo $GLOBALS["b"]; //访问全局作用域，可以访问其他文件内部变量,需在当前文件内引入
           echo $c; //可以输出函数外部的变量c
         }
         test();
      ?>
      ```
   + $c 是在函数外部定义的变量，拥有全局作用域，但是函数内部普通访问是获取不到的。
   + $d 是在函数内部声明的变量所以是局部变量，只能在函数内部访问
   + global $c 是在函数内部调用函数外部定义的全局变量,正常在函数内部访问函数外部的变量为NULL
   + PHP 同时在名为 $GLOBALS[index] 的数组中存储了所有的全局变量。下标存有变量名。这个数组在函数内也可以访问，并能够用于直接更新全局变量

   3. statc(静态作用域)
      ```
        <?php
         function myTest() {
          static $x=0;
          echo $x;
          $x++;
         }
         myTest();
         myTest();
         myTest();
        ?>
      ```

   + 通常，当函数完成/执行后，会删除所有变量。有时需要不删除某个局部变量。实现这一点需要更进一步的工作。这是需要在声明变量时使用 static 关键词
   + 每当函数被调用时，这个变量所存储的信息都是函数最后一次被调用时所包含的信息
   + 注意。该变量仍是函数的局部变量
   + 静态全局变量的作用域局限于一个源文件内，只能为该源文件内的函数公用
   + 不能对静态变量用表达式的结果赋值，否则会导致解析错误
   + static全局变量只初使化一次，下一次依据上一次结果值，上例子中调用三次执行的结果是累加的。
   + 在内存的静态存储区中（静态存储区在整个程序运行期间都存在，其他局部变量存储在栈中。)
   ## 数据类型
   + String(字符)
   + Integer(整型)
   + Boolean(布尔值)
   + Float(浮点类型)
   + 数组
     ```
      $arrayTest = array('0'=> '苹果', 1=> '测试');
      echo $arrayTest[0] // 苹果

     ```
   + 对象

     **php中，对象是存储数据和有关如何处理数据的信息的数据类型。必须明确地声明对象。首先必须**
     **使用class关键词,声明对象的类,类是包含属性和方法的结构。然后在对象类中定义数据类型,**
     **然后在该类的实例中使用此数据类型:**
     ```
     <?php
       class Car
       {
         var $color;
         function Car($color="green") {
           $this->color = $color;
         }
         function what_color() {
           return $this->color;
         }
       }
     ?>
     ```
   + NULL(空值)

   ## 常量 
   **php常量是单个值的标识符（名称）。在脚本中无法改变该值,有效的常量名以字符或下划线开头（常量名称前面没有 $ 符号）。**
   **(注释：与变量不同，常量贯穿整个脚本是自动全局的。)**

## php会话机制session 
   ```
     session_start();//一般在配置文件中初始化打开。可以在全局使用，设置存储变量
     // a.php
     $_SESSION['views'] = 1;
     // b.php
     echo $_SESSION['views'] // 1
   ```   

## The Next: 

[PHP基本操作及常用内置API](https://github.com/Danielhard/step-by-step/blob/master/note/php/basic.md)
_ _ _

[返回主目录](https://github.com/Danielhard/step-by-step/blob/master/note/php/index.md)
