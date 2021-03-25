# Concrete02 材料

---

## 本构说明

基于修正Kent-Park受压区骨架曲线、Yassin滞回规则，并考虑线性软化的受拉性能的一维混凝土本构

**参考文献**
- Mohd Hisham Mohd Yassin, "Nonlinear Analysis of Prestressed Concrete Structures under Monotonic and Cycling Loads", PhD dissertation, University of California, Berkeley, 1994.

---

## 输入格式

- 受压区参数 `COMP`

    > $N_{mat}$, matName, `COMP`, $f_{c0}$, $\epsilon_{c0}$, $f_{cu}$, $\epsilon_{cu}$, $\lambda$

    | 参数               | 说明                                     |
    | ------------------ | ---------------------------------------- |
    | `KEYWORD` = `COMP` | Compression 缩写                         |
    | $f_{c0}$           | 混凝土受压强度（取负值）                 |
    | $\epsilon_{c0}$    | 混凝土受压强度对应受压应变（取负值）     |
    | $f_{cu}$           | 混凝土受压极限强度（取负值）             |
    | $\epsilon_{cu}$    | 混凝土受压极限强度对应受压应变（取负值） |
    | $\lambda$          |                                          |


- 受拉区参数 `TENS`

    > $N_{mat}$, matName, `TENS`, $f_{c0}$, $\epsilon_{c0}$, $f_{cu}$, $\epsilon_{cu}$, $\lambda$

    | 参数               | 说明               |
    | ------------------ | ------------------ |
    | `KEYWORD` = `TENS` | Tension 缩写       |
    | $f_{t}$            | 混凝土受拉强度     |
    | $E_{ts}$           | 混凝土受压软化模量 |


---

## 示例

```c
1, mat_CONC2, TYPE, CONC2
1, mat_CONC2, DENS, 7850.00
1, mat_CONC2, EM, 2.06e+11
1, mat_CONC2, NU, 0.30
1, mat_CONC2, RDMP, 0, 0
1, mat_CONC2, COMP, -36.05E6, -0.00173, -18.03E6, -0.00365, 0.5
1, mat_CONC2, TENS, 3.22E6, 3250E6
```

