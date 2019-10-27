# 你不知道的html
  ![banner](https://github.com/Danielhard/step-by-step/blob/master/images/iron.jpg)
+ 利用images测试网速，上报数据

  1. img 属性crossorigin 和后台协商跨域 
   (其实这个属性可以用到很多标签，后台如果不在header里返回。则资源无效)
  ```
   <img crossorigin="anonymous">

   <script>
   //测试网速
   var s = Date.now();
   image.crossOrigin = ""
   var image = new Image()
   img.src = "" // 1*1  3kb
   image.onLoad = () => {
       var e = Date.now();
       var w = 4 / e-s  //网速，有波动
   }

   //  系统性能监控平台 系统的bug监控 打点
   // https://map.baidu.com/mobile/img/t.gif?newmap=1&module
   var image = new Image();
   image.crossOrigin = "anonymous";
   image.src = "http://www.yideng.com/ok.gif?.." //加上元素的id等等等。get方法发送
  
    // 用js 统计打点需要使用,不用ajax,不占用业务资源。在浏览器空闲的下一帧发送, //不需要接口
    // 类似 requestAnimationFrame()
    navigator.sendBeacon("a.php")
   </script>
  ```

 






+ css远程攻击漏洞
  1.xss
    css 支持跨域方法  background content 可以执行js = = 可以说，支持url的都有风险
    ```
      .test{
          background:url('javascript:alert(123)'); 
          color:expressssion(alert("xss"))
      }
      .test::content{
          content:url('...')
      }
      
    ```
    控制dom数量 css gpu


+ iframe对远程localStorage的扩容

  1. 跨域常见方法 jsonp img iframe
   ```
    //iframe
    <iframe src="localhost/storage.html" frameborder="0"></iframe>
    <script>
       window.frames[0].postMessage("key","value")
    </script>

    //storage.html 目标域
    <script>
    // iframe 通信 
      window.addEventListener("message",function(e){
          if(e.source !== window.parent){
              return;
          }
          localStorage.setItem(e.data.key,e.data.value);
      })
    </script>

   ``` 



+ html语义化重要性
  1. 
  ```
   // = = 这个还用说吗
  ```

