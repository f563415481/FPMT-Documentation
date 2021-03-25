# 界面参数 `INTF`

---

## 输入格式

### 包围盒网格设置 `CELL`

!> `CELL` 为必须进行设置的参数字段

> $N_{real}$, realName, `CELL`, $S_{cell}$, $d_{\phi}$, $d_{ext}$

| 参数               | 说明                             |
| ------------------ | -------------------------------- |
| `KEYWORD` = `CELL` |                                  |
| $S_{cell}$         | 包围盒单元格尺寸                 |
| $d_{\phi}$         | 判断是否进行作用对侦察的距离阈值 |
| $d_{ext}$          | 包围盒的拓宽尺寸                 |

### 界面粘结断裂行为设置 `BOND`

!> `BOND` 为可选设置

> $N_{real}$, realName, `BOND`, $b_{slide}$, $\lambda_{ts}$, $\sigma_{bond}$, $G_{c}$

| 参数               | 说明                                                            |
| ------------------ | --------------------------------------------------------------- |
| `KEYWORD` = `BOND` |                                                                 |
| $b_{slide}$        | 是否允许滑动，$b_{slide}\neq0$允许滑动，$b_{slide}=0$不允许滑动 |
| $\lambda_{ts}$     | 界面剪拉耦合系数，$\lambda_{ts}\in[0,1]$                        |
| $\sigma_{bond}$    | 界面粘合应力临界值，默认$\sigma_{bond}=0$                       |
| $G_c$​             | 界面断裂能, 默认$G_{c}=0$                                       |

?> 若`BOND`参数未设置，或 $\sigma_{bond}\leq0$，则不考虑界面粘结，仅考虑接触<br>
若 $G_c\leq0$​，界面粘结应力断裂后直接转为接触状态，否则按照内聚力模型计算断裂过程应力<br>

### 界面接触行为设置

!> `BISHEAR` 与 `REGSHEAR`需要二选一进行设置

#### 双线性库伦摩擦模型 `BISHEAR`

> $N_{real}$, realName, `BISHEAR`, $K_{n}$, $K_{s}$, $C$, $\phi_{f}$, $\phi_{d}$

| 参数                  | 说明         |
| --------------------- | ------------ |
| `KEYWORD` = `BISHEAR` |              |
| $K_{n}$               | 界面法向刚度 |
| $K_{s}$               | 界面切向刚度 |
| $C$                   | 界面粘聚力   |
| $\phi_f$              | 界面摩擦角   |
| $\phi_d$              | 界面剪胀角   |


#### 连续化库伦摩擦模型 `REGSHEAR`

> $N_{real}$, realName, `REGSHEAR`, $K_{n}$, $\alpha_f$, $C$, $\phi_{f}$, $\phi_{d}$

| 参数                   | 说明                                                    |
| ---------------------- | ------------------------------------------------------- |
| `KEYWORD` = `REGSHEAR` |                                                         |
| $K_{n}$                | 界面法向刚度                                            |
| $\alpha_f$             | $arctan$ 型摩擦力连续化参数，一般 $\alpha_f \in[0.001,1]$ |
| $C$                    | 界面粘聚力                                              |
| $\phi_f$               | 界面摩擦角                                              |
| $\phi_d$               | 界面剪胀角                                              |

---

## 有效单元种类

- [三角形界面单元 `INTERFACE`]()

---

## 示例

```c
// real1 - BISHEAR contact only
1, real1, TYPE, INTF
1, real1, CELL, 0.1, 0.001, 0.05
1, real1, BISHEAR, 3e10, 3e10, 5e8, 12, 0

// real2 - breakable bond with REGSHEAR contact
2, real2, TYPE, INTF
2, real2, CELL, 0.1, 0.001, 0.05
2, real2, BOND, 1, 1.0, 5e9, 2e3
2, real2, REGSHEAR, 3e10, 0.01, 5e8, 12, 0
```