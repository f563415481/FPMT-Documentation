# 圆形截面 ROUND

![](/SECTION/PICS/SectionRound.png)

---

## 输入格式

> $N_{sect}$, sectName, `SHAPE`, $D$

| 参数 | 说明 |
| ---- | ---- |
| $D$  | 外径 |

## 适用单元

- [杆单元 `TRUSS`]()
- [索单元 `CABLE`]()
- [梁单元 `BEAM`]()
- [纤维梁单元 `FIBER_BEAM`]()
- [双组纤维梁单元 `FIBER_BEAM_2C`]()
- [三组纤维梁单元 `FIBER_BEAM_3C`]()

---

## 示例

```c
1, sect_roud, TYPE, ROUND
1, sect_roud, SHAPE, 0.2
```