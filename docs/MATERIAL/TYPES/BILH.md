# 双线性混合强化

双线性混合强化材料

---

## 硬化方式

### 无硬化 `NONH`

> $N_{mat}$, matName, `NONH`, $\sigma_{cr}$

| 参数               | 说明               |
| ------------------ | ------------------ |
| `KEYWORD` = `NONH` | Non-hardening 缩写 |
| $\sigma_{cr}$      | 屈服强度           |


### 等向硬化 `ISOH`

> $N_{mat}$, matName, `ISOH`, $\sigma_{cr}$, $H_{iso}$

| 参数               | 说明                     |
| ------------------ | ------------------------ |
| `KEYWORD` = `ISOH` | Isotropic Hardening 缩写 |
| $\sigma_{cr}$      | 屈服强度                 |
| $H_{iso}$          | 等向硬化模量             |


### 随动硬化 `KINH`

> $N_{mat}$, matName, `KINH`, $\sigma_{cr}$, $H_{kin}$

| 参数               | 说明                     |
| ------------------ | ------------------------ |
| `KEYWORD` = `KINH` | Kinematic Hardening 缩写 |
| $\sigma_{cr}$      | 屈服强度                 |
| $H_{kin}$          | 随动硬化模量             |


### 混合硬化 `COMH`

> $N_{mat}$, matName, `COMH`, $\sigma_{cr}$, $H_{iso}$, $H_{kin}$

| 参数               | 说明                    |
| ------------------ | ----------------------- |
| `KEYWORD` = `COMH` | Combined Hardening 缩写 |
| $\sigma_{cr}$      | 屈服强度                |
| $H_{iso}$          | 等向硬化模量            |
| $H_{kin}$          | 随动硬化模量            |

---

## 示例

```c
// no hardening
1, mat_NONH, TYPE, BILH
1, mat_NONH, DENS, 7850.00
1, mat_NONH, EM, 2.06e+11
1, mat_NONH, NU, 0.30
1, mat_NONH, NONH, 235E9
// isotropic hardening
2, mat_ISOH, TYPE, BILH
2, mat_ISOH, DENS, 7850.00
2, mat_ISOH, EM, 2.06e+11
2, mat_ISOH, NU, 0.30
2, mat_ISOH, ISOH, 235E9, 2e10
// kinematic hardening
3, mat_KINH, TYPE, BILH
3, mat_KINH, DENS, 7850.00
3, mat_KINH, EM, 2.06e+11
3, mat_KINH, NU, 0.30
3, mat_KINH, KINH, 235E9, 3E9
// combined hardening
4, mat_COMH, TYPE, BILH
4, mat_COMH, DENS, 7850.00
4, mat_COMH, EM, 2.06e+11
4, mat_COMH, NU, 0.30
4, mat_COMH, COMH, 235E9, 2e10, 3E9 
```