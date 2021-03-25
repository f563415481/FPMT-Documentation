# 自定义截面 `CUSTOM`

![](/SECTION/PICS/SectionCustom.png)

---

## 输入格式

> $N_{sect}$, sectName, `SHAPE`, $A$, $I_y$, $I_z$, $I_{yz}$

| 参数     | 说明              |
| -------- | ----------------- |
| $A$      | 截面面积          |
| $I_y$    | 截面 $y$ 向惯性矩 |
| $I_z$    | 截面 $z$ 向惯性矩 |
| $I_{yz}$ | 截面极惯性矩      |


## 适用单元

- [杆单元 `TRUSS`]()
- [索单元 `CABLE`]()

---

## 示例

```c
1, sect_custom, TYPE, CUSTOM
1, sect_custom, SHAPE, 0.5, 0.1, 0.1, 0.2
```