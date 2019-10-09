# 质量意识

## 测试服务化 -  “把简单留给开发者，把复杂留给工具。” 

## 测试认证 (Google Test Certified) - 如何让开发参与进来一起做测试呢？
### What TC？
```md
2006年Google内部2位工程师创建了一个项目叫Testing Grouplet(这是一个20%时间的项目，Gmail就是20%时间孕育的产品)，
此项目旨在推动开发人员测试，这是一个文化转变的项目。

提高对自动化测试重要性的认识
通过不断改进测试框架和组件来减轻编写测试的痛苦
提供信息和指导开发人员达到良好的测试实践
```
```md
Testing Grouplet下面又包含好几个项目，比如Testing on the Toilet(每周在厕所里贴张测试小技巧)， 
Design for testability principles(代码可测试性)、Test Certified。
```
```md
测试认证项目包含一系列递增的认证级别，每个级别定义了一个可衡量的测试目标。
参与的团队达成的目标越多，获得的级别越高，它是一个推进测试文化的项目。
```
### Why TC？
```md
越晚发现bug，修复的成本越高
Google没有大规模的手工测试团队，即使有，也更愿意通过自动化来解决问题
开发人员测试来提前发现bug是一个相对便宜和有效的方式
没有一个统一的测试标准来让工程团队遵守
```
```md
我们相信良好的测试方法是有效的软件开发的重要组成部分。
测试认证计划是促进测试作为工程团队的一种文化，通过指导来养成工程团队的测试习惯。
```
### TC Level 1
* Set up test coverage bundles - 使用测试覆盖率工具
* Set up a continuous build - 建立持续集成
* Classify your tests as Small, Medium, and Large - 将测试分成小型、中型、大型
* Identify nondeterministic tests - 识别不确定性的测试
* Create a smoke test suite - 创建一个冒烟测试集

### Level 2
* No releases with red tests - 有测试失败不发布
* Require smoke test suite to pass before a submit - 提交之前必须通过冒烟测试
* Incremental coverage by all tests >= 50% - 各种类型测试整体增量覆盖率大于 50%
* Incremental coverage by small tests >= 10% - 小型测试增量覆盖率大于 10%
* At least one feature tested by an integration test - 每一个功能至少需要有一个对应的集成测试用例

### Level 3
* Require tests for all nontrivial changes - 所有重要的变更都要经过测试
* Incremental coverage by small tests >= 50% - 小型测试增量覆盖率大于 50%
* New significant features are tested by integration tests - 新增的重要功能都要经过集成测试验证

### Level 4
* Automate running of smoke tests before submitting new code - 在提交任何代码前能自动运行冒烟测试
* Smoke tests should take less than 30 minutes to run - 冒烟测试必须在30分钟之内执行完成
* No nondeterministic tests - 没有不确定性的测试 
* Total test coverage should be at least 40% - 总体测试覆盖率不小于 40%
* Test coverage from small tests alone should be at least 25% - 小型测试的代码覆盖率不小于 %25
* All significant features are tested by integration tests - 所有重要功能都应该由集成测试验证到

### Level 5
* Add a test for each non-trivial bug fix - 每一个重要的缺陷都需要增加一个对应的测试用例
* Actively use available analysis tools - 积极使用代码分析工具
* Total test coverage should be at least 60% - 总体测试覆盖率不低于 60%
* Test coverage from small tests alone should be at least 40% - 小型测试的代码覆盖率不小于 %40

### 为什么退休
```md
团队成员的测试习惯已经养成
标准是静态的，级别达成后团队可能没有再进一步的动力，甚至项目实际情况已经降级了
Project Health的出现，PH可以自动且动态的每天无需人工干预的考量项目的健康度
(PH是整个生命周期的考量，设计到开发、测试、发布和部署)
```

## 项目健康度

## 赋能&共建
