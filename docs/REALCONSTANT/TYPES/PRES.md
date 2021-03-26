| Element Type | TYPE   | SUBTYPE | D1   |

| ------------ | ------ | ------- | ---- |

| Cable        | `PRES` | `SIG`   | Sig  |

| Cable        | `PRES` | `FN`    | Fn   |

| Cable        | `PRES` | `L0`    | L0   |

| Element Type | TYPE   | SUBTYPE | D1   | D2   | D3     | D4     | D5     | D6     | D7     | D8     |

| ------------ | ------ | ------- | ---- | ---- | ------ | ------ | ------ | ------ | ------ | ------ |

| Membrane     | `PRES` | `SIG`   | Sig  | -    | -      | -      | -      | -      | -      | -      |

| Membrane     | `PRES` | `PROJ`  | Sigx | Sigy | XAxisx | XAxisy | XAxisz | YAxisx | YAxisy | YAxisz |

# 输入格式

```c
/REALCONSTANT/
iREAL, NAME, `PRES`, `SUBTYPE`, D1...
##
```

iREAL

NAME

`TYPE`

`SUBTYPE`

D1...

实常数编号, 从1开始, 必须连续编号

实常数名称, 自定义, 不能重名

实常数参数类别

实常数参数子类别

实常数参数

---

# `SUBTYPE`=`SIG`

---

# 示例

```c
/REAL_CONSTANT/
1, prestress_cable_1, PRES, SIG,   6e4
2, prestress_cable_2, PRES, FN,    8e5
3, prestress_cable_3, PRES, L0,    3.0
4, prestress_mem_1,   PRES, SIG,   2e7
5, prestress_mem_2,   PRES, PROJ,  2e7, 2e7, 1.0, 0.0, 0.0, 0.0, 1.0, 0.0 
```

