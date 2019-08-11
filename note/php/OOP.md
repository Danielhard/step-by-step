# PHP面向对象
## 先简单介绍OOP(Object-Oriented Programming)面向对象编程，使编程代码更简洁。更易于维护。和具有更强的可重用性。OOP达到了软件工程的三个目标：重用性、灵活性、拓展性 
## OOP面向对象编程的特点:封装、继承、多态
## 内容
   ```
     类 − 定义了一件事物的抽象特点。类的定义包含了数据的形式以及对数据的操作

     对象 − 是类的实例
     
     成员变量 − 定义在类内部的变量。该变量的值对外是不可见的，但是可以通过成员函数访问，在类被实例化为对象后，该变量即可称为对象的属性
     
     成员函数 − 定义在类的内部，可用于访问对象的数据
     
     继承 − 继承性是子类自动共享父类数据结构和方法的机制，这是类之间的一种关系。在定义和实现一个类的时候，可以在一个已经存在的类的基础之上来进行，把这个已经存在的类所定义的内容作为自己的内容，并加入若干新的内容
     
     父类 − 一个类被其他类继承，可将该类称为父类，或基类，或超类
     
     子类 − 一个类继承其他类称为子类，也可称为派生类
     
     多态 − 多态性是指相同的函数或方法可作用于多种类型的对象上并获得不同的结果。不同的对象，收到同一消息可以产生不同的结果，这种现象称为多态性
     
     重载 − 简单说，就是函数或者方法有同样的名称，但是参数列表不相同的情形，这样的同名不同参数的函数或者方法之间，互相称之为重载函数或者方法
     
     抽象性 − 抽象性是指将具有一致的数据结构（属性）和行为（操作）的对象抽象成类。一个类就是这样一种抽象，它反映了与应用有关的重要性质，而忽略其他一些无关内容。任何类的划分都是主观的，但必须与具体的应用有关
     
     封装 − 封装是把对象中的成员属性成员方法加上修饰符，使其尽可能隐藏对象的内部细节，以达到对成员的访问控制(不是拒绝访问)
     
     构造函数 − 主要用来在创建对象时初始化对象， 即为对象成员变量赋初始值，总与new运算符一起使用在创建对象的语句中
     
     析构函数 − 析构函数(destructor) 与构造函数相反，当对象结束其生命周期时（例如对象所在的函数已调用完毕），系统自动执行析构函数。析构函数往往用来做"清理、善后" 的工作（例如在建立对象时用new开辟了一片内存空间，应在退出前在析构函数中用delete释放）
   ```
## 类和对象之间的关系： 类是一个大的概念。对象是类里面具体到的某个实体。 两者间的关系。就是通过实例化一个类产出一个对象，(js v8引擎中有个隐藏的类)
## 面向对象的主要三个主要特征：
   + 对象的行为  (对象里面具体的方法)
   + 对象的状态  (属性)
   + 对象的标识  (可以理解为实例)

## 如何抽象一个类 
   + 类的声明
   + 成员属性
   + 成员方法

## 类的声明 (php)
   ```
     <?php
       class People {
        // 公有成员属性
         // public 修饰符
         public $name = 'zhangsan';
         public $age = 28;
         // 公有成员函数方法
         public function sayName () {
           //业务逻辑 
         }
       }
     ?>
   ```

## 对象中的成员访问
   **语法**
   $引用名 = new 类名(构造参数);
   $引用名 ->成员属性=赋值;//对象属性赋值；
   echo $引用名->成员属性;//输出对象属性；
   $引用名->成员方法(参数);//调用对象的方法;

## 特殊对象引用$this   
   特殊对象的引用$this
   ```
   public function play(){
       echo "正在玩手机";
   }
   public function info(){
       $this -> play();
       return "手机的宽度:{$this->width},手机的高度:{$this->height}";
   }
   ```
## 修饰符->访问控制
   + public(公有的 默认)
   + private (私有的)
     声明成员属性方法后,使用privare修饰实现对成员的私有封装，封装后的成员在对象外部不能直接访问，只能在对象的内部方法中使用$this访问
   + protected(受保护的)

   ```
    <?php
      /**
      * 基类
      * Define Person
      */
      class Person
      {
        //声明一个公有的构造函数
        public function __construct (){}    
        //声明一个公有的方法
        public function say()
        {
           echo 'say';
        }
        // 声明一个受保护的方法
        protected function swim()
        {
            echo 'swim<br/>
        }
        // 声明一个私有的方法
        private function study()
        {
            echo 'study'
        }
        //不加关键字默认公有方法
        function getFun()
        {
          $this->say();
          $this->swim();
          $this->study();
        }
      }
      $people = new Person();
      // 正常运行
      $people->say();
      // 产生错误
      $people->swim();
      // 产生错误
      $people->study();
      // 公有，受保护，私有都可以执行
      $people->getFun(); 

      /**
      * 子类
      * Define Boy
      */

     class Boy extends Person
     {
       function getFun2 ()
       {
         $this->sayName();
         $this->swim();
         // 这行会产生一个错误
         $this->study(); 
       }
     }
     $body = new Boy();
     // 这行能被正常执行
     $body ->sayName();
     // 公有的和受保护的都可执行，但私有的不行
     $body->getFun2(); 
    ?>
   ```
      
## 魔术方法
   + public __set ( string $name , mixed $value ) : void // 设置私有属性值的时候调用（protected private）
   + public __get ( string $name ) : mixed  // 获取私有属性值的时候调用
   + public __isset ( string $name ) : bool // 当判断一个私有成员属性是否被设置过时调用
   + public __unset ( string $name ) : void // 当销毁一个私有成员属性的时候调用

## 构造函数 
   ```
    <?php
      class Person{
        //通过构造函数为成员变量赋初始值
        function __construct($name,$age){
          $this->name = $name;
          $this->age = $age;
        }
        public function say(){
            echo "姓名".$this->name . "年龄".$this->age;
        }
      }
      $xiaowang = new Person('xiaowang ',28);
      $xiaowang->say(); // 姓名 xiaowang 年龄 28
    ?>
   ```
## 析构函数
   **析构函数 (destructor) 与构造函数相反，当对象结束其生命周期时，系统自动执行析构函数，常用场景例如连接数据库在__construct中,处理完数据断开连接在__destruct方法中**
   ```
    <?php
      class Person{
         function __construct($name,$age){
           this->name = $name;
           this->age = $age;
         }
         public function say(){
            echo "姓名".$this->name . "年龄".$this->age;
         }
         function __destruct(){
             $this->name = '';
             return true;
         }
      }
      $xiaowang = new Person('xiaowang',28);
      var_dump($xiaowang);
      echo "<br/>"
      if($xiaowang -> __destruct){
          echo '销毁成功';
          var_dump($xiaowang);
      }
    ?> 
   ```   

   ## 类的继承
     **PHP只支持单继承，一个子类只能有一个父类。不允许一个类直接继承多个类，但一个类可以被多个类继承**
     **可以有多层继承，即一个类可以继承某一个类的子类，如类B继承了类A,类C又继承了类B,那么类C也间接的继承了类A**
     
```
class Woman extends Person
 {
     function __construct($name, $age)
     {
         parent::__construct($name, $age);//实现父级构造方法的方式parent::__construct
     }
     public function goOutAge()
     {
         parent::goOutAge(); //实现父级的普通方法重载
         echo '<br/> myGoOutage<br/>';
     }
     public function haveExtends()
     {
         $this->sayName();
         //$this->goOutAge();
     }
 }
 $chengxuyuan = new Woman('程序媛', 18);
 $chengxuyuan->haveExtends();
 $chengxuyuan->goOutAge();
```

   + 类继承的应用
   + 访问类型控制
   + 子类中重载父类的方法
     ```
      parent::handler();//实现重载父类的方法
     ```

## PHP中的抽象类(abstract 声明抽象类)
   + 抽象方法和抽象类，当类中有一个方法，没有方法体，也就是没有花括号，直接分号结束，像这种方法我们叫做抽象方法，必须使用关键字abstract定义。
     如
     ```
      public abstrat function fun();
     ```
     包含这种方法的类必须是抽象类也要使用关键字abstract加以声明。(即使用关键字abstract修饰的类为抽象类)
   + 抽象类的特点:
     1.不能实例化，也就是不能new成对象
     2.若是想使用抽象类。就必须定义一个类去继承这个抽象类，并定义覆盖父类的抽象方法(实现抽象方法)   
    

## 接口技术
   + PHP与大多数面向对象编程语言一样，不支持多重继承，也就是说每个类只能继承一个父类。为了解决这个问题，PHP引入了接口，接口的思想是指定了一个实现了该接口的类必须实现的一系列函数。
   
   ```
    //定义格式
    interface 接口名称{
        //常量成员 (使用const 关键字定义)
        //抽象方法 (不需要使用abstract关键字)
    }
    //使用格式: class类名 implements 接口名1,接口名2{...}
   ```
 ## 接口和抽象类的区别
   + 当关注一个事物的本质的时候，用抽象类，当关注一个操作的时候，用接口;
   + 接口是对动作的抽象，表示这个对象能做什么，对类的局部行为进行抽象。
   + 抽象类是对根源的抽象，表示这个类是什么，对类的整体进行抽象。对一类事物的抽象描述
     (比如，男人，女人这两个类,抽象类是人，说明，他们都是人，人可以吃东西，狗也可以吃东西，你可以把'吃东西'定义成一个接口，然后让这些类去实现它)
   + 所以，在高级语言上，一个类只能继承一个类(抽象类)(不可能是生物同时是非生物)但可以实现多个接口(吃东西，走路)    
   + 具体区别:
     1. 接口是抽象类的变体，接口中所有的方法都是抽象的，而抽象类是声明方法的存在而不去实现它的类
     2. 接口可以多继承，抽象类不行
     3. 接口定义方法，不能实现，而抽象类可以实现部分方法。
     4. 接口总基本数据类型为static 而抽象类不是
     5. 接口中不能含有静态代码块及静态方法。而抽象类可以含有静态方法和静态代码块 
  
## 常见关键字
   + final
     ```
     只能修饰类和方法，不能使用final这个关键字修饰成员属性
     特性:
     1. 使用final关键字标识的类不能被继承
     2. 使用final关键字标识的方法不能被子类覆盖(重写),是最终版本
     目的:安全 没必要被继承或重写
     ```
   + static关键字
     ```
     静态修饰类成员属性和方法,类中静态属性方法不能实例化， 可以直接通过使用类名访问
     格式：类::$静态属性   类::静态方法
     在类的方法中。不能使用this引用静态变量、方法，用self引用
     格式：self::$静态属性  self::静态方法
     静态方法中不可以使用非静态的内容。就是不让使用$this.
     静态属性是共享的。也就是new很多对象也是共用一个属性
     ```
   + 单例设计模式
     ```
     主要作用在保证面向对象编程设计中。一个类只有一个实例对象存在
     ```
   + const关键字
     ```
       常量 在PHP中定义常量使用define()函数,在类里面定义常量使用 'const' 这个关键字

       const CONSTANT = 'constant value';//定义
       echo self::CONSTANT;//类内部访问
       echo className::CONSTANT;//类外部访问
     ```
   + instanceof关键字
     **检测当前对象实例是否属于某一个类或者这个类的子类**

## 自动加载类
 **PHP4中当new实例化一个不存在的类时，则自动调用此函数__autoload(),并将类名作为参数传入次函数。可以使用这个实现类的自动加载**

##PHP错误处理类
  + 系统自带异常处理
    ```
     class Exception{
       protected $message = "Unknown exception";//异常信息
       protected $code = 0;   //用户自定义异常代码
       protected $file; //发生异常的文件名
       protected $line;
       function __contract($message = null,$code =0);
       final function getMessage();//返回异常的信息
       final function getCode();//返回异常代码
       final function getFile();//返回发生异常的文件名
       final function getLine();//返回发生异常的代码行号
       final function getTrace();//backtrace()数组
       final function getTraceAsString();//已格式化成字符串的getTrace()信息
       final __toString();//可输出的字符串
     }
    ```
  + 自定义异常处理
    try{}catch(e){}
    ```
    <?php
      try{
          //...
      }catch(Exception $e){
        echo '错误文件';
        echo $e->getFile();
        //...
      }
    ?>
    <?php
    //自定义异常类时要继承系统的异常处理类
     class myException extends Exception{
      public function getAllInfo(){
          return "异常文件为:{$this->getFile()}";
      }

     }
     //捕捉时注意到类型约束为自己定义的异常处理类名
     try{
        if($_GET['num']==5){
            throw new Exception('这是一个自定义的错误');
        } 
     }catch(myException $e){
         echo $e->getAllInfo();
     }
    ?>
    ```

  + 捕捉多个异常处理
  ```
    class myException extends Exception{
      public function getAllInfo(){
          return $this->getMessage();
      }
     }
 
   try{
       //捕捉多个异常处理要抛出多个异常对象，不能是由一个异常处理类实例化和对象
        if($_GET['num']==1){
            throw new Exception('user')
        } elseif($_GET['num']==2){
          throw new Exception('sys')
        }
        echo 'success';
        //在捕捉时系统的异常处理分支要放到最后
        //注意类型约束
     }catch(myException $e){
         echo $e->getAllInfo();
     }catch(Exception $e){
         echo $e->getMessage();
     }
  ```
