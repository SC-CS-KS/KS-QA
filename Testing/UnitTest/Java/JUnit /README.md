# JUnit
```md
JUnit由极限编程（eXtreme programming）创始人 Kent Beck 、
《 设计模式：可复用面向对象软件的基础 》合著者 Erich Gamma 共同创造，
并且很快变成单元测试领域的事实标准，被移植和克隆到几乎所有流行的编程语言中
```

## Annotation
```md
@BeforeClass
	针对所有测试，只执行一次，且必须为static void
@Before
	初始化方法
@Test
	测试方法，在这里可以测试期望异常和超时时间
@After
	释放资源
@AfterClass
	针对所有测试，只执行一次，且必须为static void
@Ignore
	忽略的测试方法
```
```md
一个单元测试用例执行顺序为：
	@BeforeClass –> @Before –> @Test –> @After –> @AfterClass
每一个测试方法的调用顺序为：
	@Before –> @Test –> @After
```
* @RunWith - 一个运行器
```md
@RunWith(JUnit4.class)
@RunWith(SpringJUnit4ClassRunner.class)
	使用了Spring的SpringJUnit4ClassRunner
		以便在测试开始的时候自动创建Spring的应用上下文
@RunWith(Suite.class)
	一套测试集合
@RunWith（MockitoJUnitRunner.class）
```

## Reference
* [JUnit 5 Tutorial](https://howtodoinjava.com/junit-5-tutorial/)
* [JUnit 5 扩展模型](http://www.infoq.com/cn/articles/deep-dive-junit5-extensions?utm_source=tuicool&utm_medium=referral)

