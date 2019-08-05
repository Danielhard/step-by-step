# PHP面向对象
## 先简单介绍OOP(Object-Oriented Programming)面向对象编程，使编程代码更简洁。更易于维护。和具有更强的可重用性。OOP达到了软件工程的三个目标：重用性、灵活性、拓展性 
## OOP面向对象编程的特点:封装、继承、多态
## 内容
   ```
     类 − 定义了一件事物的抽象特点。类的定义包含了数据的形式以及对数据的操作

     对象 − 是类的实例
     
     成员变量 − 定义在类内部的变量。该变量的值对外是不可见的，但是可以通过成员函数访问，在类被实例化为对象后，该变量即可称为对象的属性
     
     成员函数 − 定义在类的内部，可用于访问对象的数据
     
     继承 − 继承性是子类自动共享父类数据结构和方法的机制，这是类之间的一种关系。在定义和实现一个类的时候，可以在一个已经存在的类的基础之上来进行，把这个已经存     在的类所定义的内容作为自己的内容，并加入若干新的内容
     
     父类 − 一个类被其他类继承，可将该类称为父类，或基类，或超类
     
     子类 − 一个类继承其他类称为子类，也可称为派生类
     
     多态 − 多态性是指相同的函数或方法可作用于多种类型的对象上并获得不同的结果。不同的对象，收到同一消息可以产生不同的结果，这种现象称为多态性
     
     重载 − 简单说，就是函数或者方法有同样的名称，但是参数列表不相同的情形，这样的同名不同参数的函数或者方法之间，互相称之为重载函数或者方法
     
     抽象性 − 抽象性是指将具有一致的数据结构（属性）和行为（操作）的对象抽象成类。一个类就是这样一种抽象，它反映了与应用有关的重要性质，而忽略其他一些无关内     容。任何类的划分都是主观的，但必须与具体的应用有关
     
     封装 − 封装是把对象中的成员属性成员方法加上修饰符，使其尽可能隐藏对象的内部细节，以达到对成员的访问控制(不是拒绝访问)
     
     构造函数 − 主要用来在创建对象时初始化对象， 即为对象成员变量赋初始值，总与new运算符一起使用在创建对象的语句中
     
     析构函数 − 析构函数(destructor) 与构造函数相反，当对象结束其生命周期时（例如对象所在的函数已调用完毕），系统自动执行析构函数。析构函数往往用来做"清理     善后" 的工作（例如在建立对象时用new开辟了一片内存空间，应在退出前在析构函数中用delete释放）
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