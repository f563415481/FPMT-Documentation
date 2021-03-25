# 圆管截面 `TUBE`

![](/SECTION/PICS/SectionTube.png)

---

## 输入格式

> $N_{sect}$, sectName, `SHAPE`, $D$, $t$

| 参数 | 说明 |
| ---- | ---- |
| $D$  | 外径 |
| $t$  | 厚度 |

## 适用单元

- [杆单元 `TRUSS`]()
- [梁单元 `BEAM`]()
- [纤维梁单元 `FIBER_BEAM`]()
- [双组纤维梁单元 `FIBER_BEAM_2C`]()
- [三组纤维梁单元 `FIBER_BEAM_3C`]()

---

## 示例

```c
1, sect_tube, TYPE, TUBE
1, sect_tube, SHAPE, 0.1, 0.03
```