# 箱型截面 `BOX`

---

## 输入格式

 $N_{sect}$, sectName, `SHAPE`, $W$, $H$, $t_w$, $t_h$

| 参数  | 说明         |
| ----- | ------------ |
| $W$   | 矩形宽度     |
| $H$   | 矩形高度     |
| $t_w$ | 宽度方向厚度 |
| $t_h$ | 高度方向厚度 |


## 适用单元

- [杆单元 `TRUSS`]()
- [梁单元 `BEAM`]()
- [纤维梁单元 `FIBER_BEAM`]()
- [双组纤维梁单元 `FIBER_BEAM_2C`]()
- [三组纤维梁单元 `FIBER_BEAM_3C`]()

---

## 示例

```c
1, sect_box, TYPE, BOX
1, sect_box, ANGLE, 30
1, sect_box, SHAPE, 0.2, 0.025, 0.25, 0.025 
```