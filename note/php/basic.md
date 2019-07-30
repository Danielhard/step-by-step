# 有关php的基本操作及常见内置API
## 1.常见内置API 
  + 字符串函数
    1. 返回字符串长度 strlen() 
       ```
       <?php
         echo strlen("Hello world!"); // 12
       ?>
       ```
    2. 神奇的API 可以统计单词数量  - -, 
        ```
        str_word_count("# arguments of String")   //参数为string字符串
        ```
    3. 反转字符串strrev()
        ```
        strrev("hello")   //参数为string字符串 
        // 输出  olleh
        ```
    4. strpos()  用于检索字符串制定字符或文本，如果找到就返回首个匹配字符位置。没有返回false
       ```
       <?php
         echo strpos("Hello world!","world");
       ?>
       ```
    5. 替换 str_replace() 
       ```
       <?php
        echo str_replace("world", "Kitty", "Hello world!"); // 输出 Hello Kitty!
       ?>
       ```   
## 2.       