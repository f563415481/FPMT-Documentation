# 收敛控制 `CONV`

- 若不对`CONV`字段进行设置，则不进行收敛判断

---

## 输入格式

> stepName, `CONV`, $n_{interval}$, $\xi_{d}$, $\xi_{f}$

| 参数               | 说明                                                  |
| ------------------ | ----------------------------------------------------- |
| `KEYWORD` = `CONV` |                                                       |
| $n_{interval}$     | 收敛判断的步数间隔                                    |
| $\xi_{d}$          | 收敛判断的位移增量判据，默认 $\xi_{d}=1\times10^{-8}$ |
| $\xi_{f}$          | 收敛判断的不平衡力判据，默认 $\xi_{f}=5\times10^{-6}$ |

## 前置条件

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md) 已设置
- [步长控制 `TIME`](/STEP/GENERAL/TIME.md) 已设置

---

## 示例

```c
step1, STEP_TYPE, STATIC
step1, TIME, 5.0, 1e-4, OFF 
step1, CONV, 50, , 3e-6
```

