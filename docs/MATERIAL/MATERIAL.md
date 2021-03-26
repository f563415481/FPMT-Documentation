# 材料 `/MATERIAL/`

---

## 通用输入格式

> /MATERIAL/<br>
$N_{mat}$, matName, `KEYWORD`, ......<br>
##<br>

| 参数      | 说明                                |
| --------- | ----------------------------------- |
| $N_{mat}$ | 材料编号, 从1开始, 必须连续编号 |
| matName   | 材料名称, 自定义, 不能重名      |
| `KEYWORD` | 参数关键词                          |

---

## 材料通用参数

### 必选参数

#### 材料种类 `TYPE`

> $N_{mat}$, matName, `TYPE`, matType

| 材料参数         | 参数说明                                      |
| ---------------- | --------------------------------------------- |
| `KEYWORD`=`TYPE` |                                               |
| matType          | 材料种类，可选 `LE`、`BILH`、`DP`、`CONC2` 等 |

```c
1, mat_LE, TYPE, LE
2, mat_BILH, TYPE, BILH
```

#### 弹性模量 `EM`

- 前置条件
  - 材料种类 `TYPE`

> $N_{mat}$, matName, `EM`, $E$

| 材料参数       | 参数说明             |
| -------------- | -------------------- |
| `KEYWORD`=`EM` | Elastic Modulus 缩写 |
| $E$            | 材料弹性模量         |

```c
1, mat_LE, TYPE, LE
1, mat_LE, EM, 2.06e+11
```

#### 泊松比 `NU`

- 前置条件
  - 材料种类 `TYPE`

> $N_{mat}$, matName, `NU`, $\nu$

| 材料参数       | 参数说明   |
| -------------- | ---------- |
| `KEYWORD`=`NU` |            |
| $\nu$          | 材料泊松比 |

```c
1, mat_LE, TYPE, LE
1, mat_LE, NU, 0.30
```

#### 密度 `DENS`

- 前置条件
  - 材料种类 `TYPE`

> $N_{mat}$, matName, `DENS`, $\rho$

| 材料参数       | 参数说明     |
| -------------- | ------------ |
| `KEYWORD`=`EM` | Density 缩写 |
| $\rho$         | 材料质量密度 |

```c
1, mat_LE, TYPE, LE
1, mat_LE, DENS, 7850.00
```

### 可选参数

#### 材料阻尼 `RDMP`

- 前置条件
  - 材料种类 `TYPE`

> $N_{mat}$, matName, `RDMP`, $\alpha$，$\beta$

| 材料参数           | 参数说明              |
| ------------------ | --------------------- |
| `KEYWORD` = `RDMP` | Rayleigh Damping 缩写 |
| $\alpha$           | 材料质量阻尼系数      |
| $\beta$            | 材料刚度阻尼系数      |

```c
1, mat_LE, TYPE, LE
1, mat_LE, RDMP, 5, 0.01
```

#### 材料断裂参数 `FRAC`

- 前置条件
  - 材料种类 `TYPE`

> $N_{mat}$, matName, `FRAC`, $\sigma_{max}$, $E_{fracture}$

| 材料参数           | 参数说明       |
| ------------------ | -------------- |
| `KEYWORD` = `FRAC` | Fracture 缩写  |
| $\sigma_{max}$     | 材料临界应力   |
| $E_{fracture}$     | 材料断裂释放能 |

```c
1, mat1, TYPE, LE
1, mat1, FRAC, 7.0e8, 12.25e3
```

#### 材料显示颜色 `COLOR`

> $N_{mat}$, matName, `COLOR`, $r$, $g$, $b$

| 参数                | 说明                     |
| ------------------- | ------------------------ |
| `KEYWORD` = `COLOR` |                          |
| $r$, $g$, $b$       | RGB 色彩空间内的颜色参数 |

```c
1, mat1, TYPE, ...
1, mat1, COLOR, 163, 163, 173
```

---

## 材料种类

### 线弹性材料 `LE`

线弹性材料
- 使用通用参数输入即可

### 非线性弹性 `NLE`

To be added...

### 双线性混合强化材料 `BILH`

基于 J2 塑性理论，融合双线性等向强化、双线性随动强化的双线性混合强化材料
- 需要设置硬化模式 `NONH`, `ISOH`, `KINH` 或 `COMH`
- 详细参数请参考 [双线性混合强化材料 `BILH`](/MATERIAL/TYPES/BILH.md)

### Drucker-Prager 材料 `DP`

采用非关联流动法则的线性 Drucker-Prager 材料
- 详细参数请参考 [Drucker-Prager材料 `DP`](/MATERIAL/TYPES/DP.md)

### Concrete02材料 `CONC2`

约束混凝土本构
- 需要设置受压区 `COMP` 和受拉区 `TENS` 本构曲线参数
- 详细参数请参考 [Concrete02材料 `CONC2`](/MATERIAL/TYPES/CONC2.md)

---

## 示例

```c
/MATERIAL/
// elestic
1, mat_LE, TYPE, LE
1, mat_LE, DENS, 7850.00
1, mat_LE, EM, 2.06e+11
1, mat_LE, NU, 0.30
1, mat_LE, RDMP, 0, 0
// concrete
2, mat_CONC2, TYPE, CONC2
2, mat_CONC2, DENS, 7850.00
2, mat_CONC2, EM, 2.06e+11
2, mat_CONC2, NU, 0.30
2, mat_CONC2, RDMP, 0.2, 0
2, mat_CONC2, COMP, -36.05E6, -0.00173, -18.03E6, -0.00365, 0.5
2, mat_CONC2, TENS, 3.22E6, 3250E6
// metal
3, mat_KINH, TYPE, BILH
3, mat_KINH, DENS, 7850.00
3, mat_KINH, EM, 2.06e+11
3, mat_KINH, NU, 0.30
3, mat_KINH, KINH, 235E9, 3E9
## 
```