# Property-Based 测试

```md
Property-based测试实际上提出了两个策略来保证测试的有效性：
1. 随机产生输入值，保证足够多的测试用例
2. 找出并断言功能具有的普遍适应性的属性
```
```md
基于属性的测试主要起源于哈斯克尔快速审计（Haskell’s QuickCheck），
因此通常与富类型语言、形式规约以及其他相关领域联系到一起。
```

## 实例
* 测试一个sort（排序）函数
```md
@given(st.lists(st.integers()))
def test_sort(s):
out = list(sorted(s))
assert set(out) == set(s)
assert all(x<=y for x,y in zip(out, out[1:]))
```
