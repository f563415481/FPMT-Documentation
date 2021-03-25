# 矩形截面 `RECT`

![](/SECTION/PICS/SectionRect.png)

---

## 输入格式

> $N_{sect}$, sectName, `SHAPE`, $W$, $H$

$N_{sect}$

| 参数 | 说明     |
| ---- | -------- |
| $W$  | 矩形宽度 |
| $H$  | 矩形高度 |

## 适用单元

- [杆单元 `TRUSS`]()
- [梁单元 `BEAM`]()
- [纤维梁单元 `FIBER_BEAM`]()
- [双组纤维梁单元 `FIBER_BEAM_2C`]()
- [三组纤维梁单元 `FIBER_BEAM_3C`]()

---

## 示例

```c
1, sect_rect, TYPE, RECT
1, sect_rect, ANGLE, 30
1, sect_rect, SHAPE, 0.1, 0.1
```