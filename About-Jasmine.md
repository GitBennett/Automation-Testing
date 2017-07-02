# Jasmine 单元测试
不依赖任何其他JS框架，也不需要对DOM操作

基于行为驱动开发 (Behavior-Driven Development) 的测试框架

可运行于Node.js

多终端支持

# 理解BDD和TDD的区别
BDD 与 TDD (Test Driven Development) 的主要区别是，使得非程序人员也能参与到测试用例的编写中来，大大降低了客户、用户、项目管理者与开发者之间来回翻译的成本。所以BDD更加注重业务需求而不是技术

# 理解AAA
Arrange -> 输入数据组装

Act -> 模拟操作

Assert -> 验证输出

# 基础语法
Suite (测试集) - 使用全局的 Jasmine 函数 describe(string, function) 来创建，其中 string 为 Suite 的标题
Spec (测试用例) - 使用全局的 Jasmine 函数 it(string, function) 来创建，其中 string 为 Spec 的标题

Setup / Teardown -> 为了在复杂的测试用例中更加便于组装和拆卸，Jasmine提供了四个函数：

  beforeEach() ： 在describe函数中每个Spec执行之前执行一次。
  afterEach()  ： 在describe函数中每个Spec数执行之后执行一次。
  beforeAll()  ： 在describe函数中所有的Specs执行之前执行，但只执行一次，在Sepc之间并不会被执行。
  afterAll()   ： 在describe函数中所有的Specs执行之后执行，但只执行一次，在Sepc之间并不会被执行。

Expectation (断言) - 使用 expect(expectObj).callback(function(actualObj)) 来创建，和 Matchers 连用，设置测试的预期值

Spy: 能监测任何function的调用和方法参数的调用痕迹，使用两个特殊的Matcher -> toHaveBeenCalled, toHaveBeenCalledWith

spyOn(obj, '') -> 声明一个Spy
and.stub -> 阻止Spy继续对实际值产生影响，对实际实现的影响还原到最终状态
and.callThrough -> 返回函数调用后实际的值

自定义Matcher -> 

1.定义到特定的describe函数中 -> 

describe("matchers: 'toBeCover'", function(){
  beforeEach(function(){ jasmine.addMatchers(customMatchers); })
})

2.定义到全局beforeEach函数中 ->

beforeEach(function(){
   jasmine.addMatchers({
      toBePlaying: function(){
         return { compare: function(expect, actual){ var player = actual; return { pass: player.current === expected && player.isPlaying } } };
      }
   })
})

# Matchers
toBe() -> ===
toNotBe()
toBeDefined()
toBeUndefined()
toBeNull()
toBeTruthy() //如果转换为布尔值，是否为true
toBeFalsy() //false
toBeLessThan() //数值比较，小于
toBeGreaterThan() //数值比较，大于
toEqual() -> ==
toNotEqual()
toContain() //数组中是否包含元素，只用于数组
toBeCloseTo() //数值比较定义精度，先四舍五入再比较
toMatch() //按正则表达式匹配
toNotMatch()
toThrow() //抛出异常

禁用Suites -> xdescribe //被Disabled的Suites在执行中会被跳过，该Suite的结果也不会显示在结果集中

挂起Specs -> xit(), it(""), it("", function(){ pending('') //Display: PENDING WITH MESSAGE })

Jasmine Clock //用于setTimeout和setInterval的回调控制 -> jasmine.clock().install(), uninstall()

Mocking Timeout -> jasmine.clock().tick(nTime)

全局匹配 -> jasmine.any, jasmine.anything, jasmine.objectContaining, jasmine.arrayContaining

# 自定义Matcher

高级功能的定制。

