# Drucker-Prager `DP`

Drucker-Prager材料

## 硬化方式

### 线性 Drucker-Prager `LDP`

> $N_{mat}$, matName, `LDP`, $c$, $\phi_{f}$, $\phi_d$

| 参数            | 说明           |
| --------------- | -------------- |
| `KEYWORD` = `LDP` |                |
| $c$             | 材料粘聚力     |
| $\phi_f$        | 摩擦角，角度制 |
| $\phi_d$        | 剪胀角，角度制 |

## 示例

```c
1, mat_DP, TYPE, DP
1, mat_DP, DENS, 7850.00
1, mat_DP, EM, 2.06e+11
1, mat_DP, NU, 0.30
1, mat_DP, RDMP, 0, 0
1, mat_DP, LDP, 3e6, 12.0, 0.0 
```

