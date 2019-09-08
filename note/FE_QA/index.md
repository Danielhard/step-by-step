# 测试的核心概念
  + 单元测试
    1. 目的:单元测试能够让开发者明确知道代码结果
    2. 原则:单一职责、接口抽象、层次分离
    3. 断言库:保证最小单元是否正常运行检测方法
    4. 测试风格:测试驱动开发(Test_driven Development,TDD)、(Behavior Driven Development ,BDD)行为驱动开发均是敏捷开发方法论
       TDD:关注所有的功能是否被实现(每一个功能都必须有对伊尼戈测试用例，suite配合test利用assert('aa'===name))
       BDD关注整体行为是否符合整体预期，编写的每一行代码都有目的提供一个全面测试用例集 should describe配合it利用自然语言expect(1).toEqueal   (fn())

     ```
      单元测试框架
       better-assert (TDD断言库)
       should.js(BDD断言库)
       expect.js(BDD断言库)
       chai.js(TDD BDD双模)
       Jasmine.js(BDD断言库)
     ```

     
  + 性能测试
  + 安全测试
  + 功能测试
  