+ 反柯里化
  ```
   Function.prototype.uncurry = function(){
       return this.call.bind(this)
   }

   //push通用化
   var push = Array.prototype.push.uncurry();

   var arr = [];
   push(arr,1);
   push(arr,2);
   push(arr,3);
  ``` 
+ 柯里化
  ```
  
  ```