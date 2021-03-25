# 材料 `/MATERIAL/`

---

## 通用输入格式

> /MATERIAL/<br>
$N_{mat}$, matName, `KEYWORD`, ......<br>
##<br>

| 参数      | 说明                                |
| --------- | ----------------------------------- |
| $N_{mat}$ | 材料编号, 从1开始, 必须**连续编号** |
| matName   | 材料名称, 自定义, **不能重名**      |
| `KEYWORD` | 参数关键词                          |

---

## 材料通用参数

**必选参数(!)** 

- [材料种类 `TYPE`](/MATERIAL/GENERAL/TYPE.md)
- [弹性模量 `EM`](/MATERIAL/GENERAL/EM.md)
- [泊松比 `NU`](/MATERIAL/GENERAL/NU.md)
- [密度 `DENS`](/MATERIAL/GENERAL/DENS.md)

**可选参数(?)**

- [材料阻尼 `RDMP`](/MATERIAL/GENERAL/RDMP.md)
- [材料断裂参数 `FRAC`](/MATERIAL/GENERAL/FRAC.md)
- [材料显示颜色 `COLOR`](/MATERIAL/GENERAL/COLOR.md)

---

## 材料弹性参数

- [线弹性 `LE`](/MATERIAL/TYPES/LE.md)
- [非线性弹性 `NLE`]()

## 材料塑性参数

- [双线性混合强化 `BILH`](/MATERIAL/TYPES/BILH.md)
- [Drucker-Prager `DP`](/MATERIAL/TYPES/DP.md)
- [Concrete02 `CONC2`](/MATERIAL/TYPES/CONC2.md)

---

## 示例

```c
/MATERIAL/
// concrete
1, mat_CONC2, TYPE, CONC2
1, mat_CONC2, DENS, 7850.00
1, mat_CONC2, EM, 2.06e+11
1, mat_CONC2, NU, 0.30
1, mat_CONC2, RDMP, 0.2, 0
1, mat_CONC2, COMP, -36.05E6, -0.00173, -18.03E6, -0.00365, 0.5
1, mat_CONC2, TENS, 3.22E6, 3250E6
// metal
2, mat_KINH, TYPE, BILH
2, mat_KINH, DENS, 7850.00
2, mat_KINH, EM, 2.06e+11
2, mat_KINH, NU, 0.30
2, mat_KINH, KINH, 235E9, 3E9
## 
```