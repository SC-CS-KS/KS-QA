# End-to-End Testing（端到端测试）
```md
端到端测试模拟用户行为。
在Web应用程序中，他们会启动服务器，打开浏览器，到处点击，断言浏览器中发生了特定的事情，让我们相信功能可以正常运行。
这些测试会给我们巨大的信心，但是它们缓慢而脆弱，并且同用户界面紧密地耦合在了一起。

不同于行为驱动测试（BDD）和单元测试独立运行并使用模拟/存根，
端到端测试将试着尽可能从用户的视角，对真实系统的访问行为进行仿真。
对Web应用来说，这意味着需要打开浏览器、加载页面、运行JavaScript，以及进行与DOM交互等操作。
```

## 前端测试
* 单元测试
```md
前端测试框架很多，目前的主流应该是jest和jest-dom，
主要是它是create-react-app自带的，也是facebook的，以及配套的react-testing-library。
其它常见的还有mocha,jasmine,ava等，以及chai/sinon等断言库，基本大同小异。
```
* 组件测试
```md
针对React组件开发的两个高层次的测试框架：airbnb.io/enzyme/ storybook.js.org
```
* 数据工具
```md
各类Mock库，jest自带的基本够用，数据相关测试辅助生成工具，例如：github.com/marak/Faker。
```

## 手机端测试
