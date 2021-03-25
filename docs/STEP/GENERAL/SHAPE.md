# 找形控制 `SHAPE`

---

## 输入格式

> stepName, `SHAPE`, $\gamma_{soft}$, $C_{pace}$, $b_{diss}$, $\gamma_{diss}$

| 参数                | 说明                                                                                |
| ------------------- | ----------------------------------------------------------------------------------- |
| `KEYWORD` = `SHAPE` |                                                                                     |
| $\gamma_{soft}$     | 柔性体弹性模量缩放系数，$\gamma_{soft}\in(0,1]$，默认$\gamma_{soft}=1\times10^{-6}$ |
| $C_{pace}$          | 步幅放大系数，默认 $C_{pace}=100$                                                   |
| $b_{diss}$          | 是否使用虚拟耗能，$b_{diss} = $`ON`（使用）或 $b_{diss} = $`OFF`（不使用）              |
| $\gamma_{diss}$     | 虚拟耗能系数，$\gamma_{diss}\in[0,1]$，一般取 $95\%$                                |


**注**：若 $b_{diss}$ = `OFF`，则可不对 $\gamma_{diss}$ 进行设置，此时 $\gamma_{diss}=0\%$

## 前置条件

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md) 已设置
- [步长控制 `TIME`](/STEP/GENERAL/TIME.md) 已设置

---

## 示例

```c
step1, TYPE, SHAPE
step1, TIME, 10.0, 1e-2
step1, SHAPE, 1e-6, 50, ON, 0.98
```

