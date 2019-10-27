# 测试的核心概念
  + 单元测试
    1. 目的:单元测试能够让开发者明确知道代码结果
    2. 原则:单一职责、接口抽象、层次分离
    3. 断言库:保证最小单元是否正常运行检测方法
    4. 测试风格:测试驱动开发(Test_driven Development,TDD)、(Behavior Driven Development ,BDD)行为驱动开发均是敏捷开发方法论
       TDD:关注所有的功能是否被实现(每一个功能都必须有对应一个测试用例，suite配合test利用assert('aa'===name))
       BDD关注整体行为是否符合整体预期，编写的每一行代码都有目的提供一个全面测试用例集 should describe配合it利用自然语言expect(1).toEqueal   (fn())

     ```
      单元测试框架
       better-assert (TDD断言库)
       should.js(BDD断言库)
       expect.js(BDD断言库)
       chai.js(TDD BDD双模)
       Jasmine.js(BDD断言库)
     ```
     ```
       单元测试运行流程
        before -> beforeEach -> it -> after ->afterEach 
        每一个测试用例通过describe进行设置
        1.before 单个测试用例 (it)开始前
        2.beforeEach 每一个测试用例开始前
        3.it定义测试用例，并利用断言库进行设置chai如:expect(x).to.eaqual(true)
        4 异步mocha 专业术语叫mock
     ```
     ```
      自动化单元测试
      karma 自动化runner 继承PhantomJs 无刷新
      npm install -g karma
      npm install karma-cli --save-dev
      npm install karma-chrome-launcher --save-dev
      npm install karma-phantomjs-launcher --save-dev
      npm install karma-mocha --save-dev
      npm install karma-chai
     ```
     ```
      报告和单测覆盖率检查
      npm install karma-coverage --save-dev
      coverageReporter:{
          type:'html',
          dir:'coverage/'
      }//配置代码覆盖测试率生成结果
     ```
     ```
      压力测试
      1.对网络接口做压力测试需要检查的几个常用指标有吞吐率，响应时间和并发数，这些指标反映了服务器并发处理能力
      2.PV网站当日访问人数UV独立访问人数。PV每天几十万甚至上百万就需要考虑压力测试。换算公式 QPS = PV/t ps:1000000/10*60*60=27.7(100万去请求集中在10小时，服务器美妙处理27.7个业务请求)
      3.常用的压力测试工具是ab,siege,http_load
      4.ab -c 100 -n 100 http://localhost:8001 每秒持续发出28个请求Request per second 表示服务器每秒请求处理请求书即为QPS
      Failed requests 表示此次请求实际的请求数 客户端向服务器端建立连接，服务器端处理请求。等待报文等
     ```
  + 性能测试
     ```
      基准测试
      1.面向切面编程AOP无侵入式统计
      2.Banchmark基准测试方法，它并不是简单的统计执行多少次测试代码后对比时间，它对测试有着严密的抽样过程。执行多少次取决于采样到的数据是否能完成统计。根据统计次数计算方差
     ```
  + 安全测试
     ```
     安全测试
      安全漏洞检查
      XSS
      SQL
      CSRF
     ```
  + 功能测试
    ```
     用户真实性检查

     selenium-webdriver
     protractor selenium-standalone
     htt0://webdriver.io/WEBDRIVER/O
     冒烟测试 SmokeTest 自由测试的一种。找到一个BUG开发修复。然后专门针对此BUG,优点节省时间防止build失败，缺点是覆盖率极低。
     回归测试 修改一处对整体功能的测试。一般配合自动化测试


     JsLint  &&  JsHint
     目的: 检测js代码标准
     原因 js代码诡异，保证团队代码规范
     搭配自动化任务化任务管理工具完善自动化测试grunt-jshint grunt-jslint


     Q&A
    ```