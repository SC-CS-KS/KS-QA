# Code Coverage
```md
基本含义：测试后被测目标已执行的代码数 / 被测目标总的代码数
触发行为：功能测试、接口测试
```
## 度量维度
* 函数覆盖
* 语句覆盖
* 判断覆盖
* 条件覆盖
* 路径覆盖

## 参考意义
```md
分析未覆盖部分的代码，从而反推在前期测试用例设计是否充分，评估需求理解是否清晰，用例设计是否遗漏
检测出程序中的废代码，可以逆向反推在代码设计中思维混乱点，提醒开发人员理清代码逻辑关系，提升代码质量。
代码覆盖是一种度量方法，而不是衡量正确性或性能的指标。
    代码覆盖并不等于测试质量、代码质量，把它作为一种发现未被测试覆盖的代码的手段。
```

## 全量代码覆盖率

## 差异代码覆盖率
```md
针对小需求精准评估测试范围覆盖情况
把控RD上线自测情况
设置阈值，作为测试通过的指标
```
* [基于 codediff 的差异代码覆盖率统计实现](https://testerhome.com/topics/16436)

