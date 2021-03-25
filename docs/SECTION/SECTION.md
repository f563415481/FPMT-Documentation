# 截面 `SECTION`

---

## 通用输入格式

 > /SECTION/<br>
 $N_{sect}$, sectName, `KEYWORD`, ...<br>
 \#\#<br>

| 参数       | 说明                                |
| ---------- | ----------------------------------- |
| $N_{sect}$ | 截面编号, 从1开始, 必须**连续编号** |
| sectName   | 截面名称, 自定义, **不能重名**      |
| `KEYWORD`  | 参数关键词                          |


---

## 截面通用参数

- [截面种类 `TYPE`](/SECTION/GENERAL/TYPE.md)
- [截面转角 `ANGLE`](/SECTION/GENERAL/ANGLE.md)
- [截面形状 `SHAPE`](/SECTION/GENERAL/SHAPE.md)

---

## 截面种类

- [矩形截面 `RECT`](/SECTION/TYPES/RECT.md)
    
    ![](/PICS/SectionRect.png)

- [圆管截面 `TUBE`](/SECTION/TYPES/TUBE.md)
    
    ![](/PICS/SectionTube.png)

- [圆形截面 `ROUND`](/SECTION/TYPES/ROUND.md)
    
    ![](/PICS/SectionRound.png)

- [厚度截面 `THICK`](/SECTION/TYPES/THICK.md)
    
    ![](/PICS/SectionThick.png)

- [箱型截面 `BOX`](/SECTION/TYPES/BOX.md)
    
    ![](/PICS/SectionRect.png)

- [纤维截面 `FIBER`](/SECTION/TYPES/FIBER.md)
    
    ![](/PICS/SectionFiber.png)
    
- [自定义截面 `CUSTOM`](/SECTION/TYPES/CUSTOM.md)
    
    ![](/PICS/SectionCustom.png)

---

## 示例

```c
/SECTION/
// 圆管截面
1, tube, TYPE, TUBE
1, tube, SHAPE, 0.25, 0.025
// 圆形截面
2, round, TYPE, ROUND
2, round, SHAPE, 0.25
// 矩形截面
3, rect, TYPE, RECT
3, rect, ANGLE, 5
3, rect, SHAPE, 0.25, 0.25
// 纤维截面
4, rebar, TYPE, FIBER
4, rebar, ANGLE, 5
4, rebar, ADDFIBER, 0.105, 0.105, 0.000381
4, rebar, ADDFIBER, 0.105, -0.105, 0.000381
4, rebar, ADDFIBER, -0.105, -0.105, 0.000381
4, rebar, ADDFIBER, -0.105, 0.105, 0.000381
// 箱型截面
5, box, TYPE, BOX
5, box, SHAPE, 0.2, 0.025, 0.25, 0.025
##
```

