# 纤维截面 `FIBER`

![](/SECTION/PICS/SectionFiber.png)

---

## 输入格式

> $N_{sect}$, sectName, `ADDFIBER`, $y$, $z$, $A$

| 参数 | 说明          |
| ---- | ------------- |
| $y$  | 纤维 $y$ 坐标 |
| $z$  | 纤维 $z$ 坐标 |
| $A$  | 纤维面积      |

## 适用单元

- [杆单元 `TRUSS`]()
- [梁单元 `BEAM`]()
- [纤维梁单元 `FIBER_BEAM`]()
- [双组纤维梁单元 `FIBER_BEAM_2C`]()
- [三组纤维梁单元 `FIBER_BEAM_3C`]()

---

## 示例

```c
1, sect_rebar, TYPE, FIBER
2, sect_rebar, ADDFIBER, 0.105, 0.105, 0.000381
2, sect_rebar, ADDFIBER, 0.105, -0.105, 0.000381
2, sect_rebar, ADDFIBER, -0.105, -0.105, 0.000381
2, sect_rebar, ADDFIBER, -0.105, 0.105, 0.000381 
```