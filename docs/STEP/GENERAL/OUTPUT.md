# 输出控制 `OUTPUT`

---

## 输入格式

> stepName, `OUTPUT`, $n_{total}$, $idx_{start}$, $idx_{end}$

| 参数                 | 说明                                         |
| -------------------- | -------------------------------------------- |
| `KEYWORD` = `OUTPUT` |                                              |
| $n_{total}$          | 总输出步数，默认 $n_{total} = 100$              |
| $idx_{start}$        | 进行输出的起始步编号，默认为 0                |
| $idx_{end}$          | 进行输出的终止步编号，默认为求解步的终止子步 |


注：需要保证 $n_{total}<(idx_{end}-idx_{start})$

## 前置条件

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md) 已设置
- [步长控制 `TIME`](/STEP/GENERAL/TIME.md) 已设置

---

## 示例

```c
step1, TYPE, STATIC
step1, TIME, 10.0, 1e-2
step1, OUTPUT, 500 

step2, TYPE, DYNA
step2, TIME, 10.0, 1e-2
step2, OUTPUT, 100, 500, 1000
```