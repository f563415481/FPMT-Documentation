# 截面 `SECTION`

---

## 通用输入格式

 > /SECTION/<br>
 $N_{sect}$, sectName, `KEYWORD`, ...<br>
 \#\#<br>

| 参数       | 说明                                |
| ---------- | ----------------------------------- |
| $N_{sect}$ | 截面编号, 从1开始, 必须连续编号 |
| sectName   | 截面名称, 自定义, 不能重名      |
| `KEYWORD`  | 参数关键词                          |

---

## 截面参数设置

### 截面种类 `TYPE`

> $N_{sect}$, sectName, `TYPE`, sectType

| 截面参数           | 参数说明                                                                     |
| ------------------ | ---------------------------------------------------------------------------- |
| `KEYWORD` = `TYPE` |                                                                              |
| sectType           | 截面种类，可选 `TUBE`、`ROUND`、`RECT`、`BOX`、`THICK`、`CUSTOM`、`FIBER` 等 |

```c
1, sect_TUBE, TYPE, TUBE
1, sect_TUBE, ...
2, sect_BILH, TYPE, RECT
2, sect_BILH, ... 
```

### 截面转角 `ANGLE`

- 前置条件
  - 截面种类 `TYPE` 已定义

> $N_{sect}$, sectName, `ANGLE`, $\phi$

| 截面参数            | 参数说明           |
| ------------------- | ------------------ |
| `KEYWORD` = `ANGLE` |                    |
| $\phi$              | 截面欧拉角，角度制 |

```c
1, sect_RECT, TYPE, RECT
1, sect_RECT, ANGLE, 12
```

### 截面形状 `SHAPE`

- 前置条件
  - 截面种类 `TYPE` 已定义

> $N_{sect}$, sectName, `SHAPE`, $P_1$, $P_2$...

| 截面参数            | 参数说明 |
| ------------------- | -------- |
| `KEYWORD` = `SHAPE` |          |
| $P_1$, $P_2$ ...    | 形状参数 |

#### 矩形截面 `RECT`

![](/PICS/SectionRect.png)

> $N_{sect}$, sectName, `SHAPE`, $W$, $H$

| 参数 | 说明     |
| ---- | -------- |
| $W$  | 矩形宽度 |
| $H$  | 矩形高度 |

- 适用单元
  - [杆单元 `TRUSS`]()
  - [梁单元 `BEAM`]()
  - [纤维梁单元 `FIBER_BEAM`]()
  - [双组纤维梁单元 `FIBER_BEAM_2C`]()
  - [三组纤维梁单元 `FIBER_BEAM_3C`]()

```c
1, sect_rect, TYPE, RECT
1, sect_rect, ANGLE, 30
1, sect_rect, SHAPE, 0.1, 0.1
```

#### 圆管截面 `TUBE`

![](/PICS/SectionTube.png)

> $N_{sect}$, sectName, `SHAPE`, $D$, $t$

| 参数 | 说明 |
| ---- | ---- |
| $D$  | 外径 |
| $t$  | 厚度 |

- 适用单元
  - [杆单元 `TRUSS`]()
  - [梁单元 `BEAM`]()
  - [纤维梁单元 `FIBER_BEAM`]()
  - [双组纤维梁单元 `FIBER_BEAM_2C`]()
  - [三组纤维梁单元 `FIBER_BEAM_3C`]()

```c
1, sect_tube, TYPE, TUBE
1, sect_tube, SHAPE, 0.1, 0.03
```

#### 圆形截面 `ROUND`

![](/PICS/SectionRound.png)

> $N_{sect}$, sectName, `SHAPE`, $D$

| 参数 | 说明 |
| ---- | ---- |
| $D$  | 外径 |

- 适用单元
  - [杆单元 `TRUSS`]()
  - [索单元 `CABLE`]()
  - [梁单元 `BEAM`]()
  - [纤维梁单元 `FIBER_BEAM`]()
  - [双组纤维梁单元 `FIBER_BEAM_2C`]()
  - [三组纤维梁单元 `FIBER_BEAM_3C`]()

```c
1, sect_roud, TYPE, ROUND
1, sect_roud, SHAPE, 0.2
```

#### 厚度截面 `THICK`

![](/PICS/SectionThick.png)

> $N_{sect}$, sectName, `SHAPE`, $t$

| 参数 | 说明 |
| ---- | ---- |
| $t$  | 厚度 |

- 适用单元
  - [三角形壳单元 `SHELL_TRI`]()
  - [三角形膜单元 `MEMBRANE_TRI`]()

```c
1, sect_shell, TYPE, THICK
1, sect_shell, SHAPE, 0.01
```

#### 箱型截面 `BOX`

![](/PICS/SectionRect.png)

$N_{sect}$, sectName, `SHAPE`, $W$, $H$, $t_w$, $t_h$

| 参数  | 说明         |
| ----- | ------------ |
| $W$   | 矩形宽度     |
| $H$   | 矩形高度     |
| $t_w$ | 宽度方向厚度 |
| $t_h$ | 高度方向厚度 |

- 适用单元
  - [杆单元 `TRUSS`]()
  - [梁单元 `BEAM`]()
  - [纤维梁单元 `FIBER_BEAM`]()
  - [双组纤维梁单元 `FIBER_BEAM_2C`]()
  - [三组纤维梁单元 `FIBER_BEAM_3C`]()

```c
1, sect_box, TYPE, BOX
1, sect_box, ANGLE, 30
1, sect_box, SHAPE, 0.2, 0.025, 0.25, 0.025 
```

#### 纤维截面 `FIBER`

![](/PICS/SectionFiber.png)

> $N_{sect}$, sectName, `ADDFIBER`, $y$, $z$, $A$

| 参数 | 说明          |
| ---- | ------------- |
| $y$  | 纤维 $y$ 坐标 |
| $z$  | 纤维 $z$ 坐标 |
| $A$  | 纤维面积      |

- 适用单元
  - [杆单元 `TRUSS`]()
  - [梁单元 `BEAM`]()
  - [纤维梁单元 `FIBER_BEAM`]()
  - [双组纤维梁单元 `FIBER_BEAM_2C`]()
  - [三组纤维梁单元 `FIBER_BEAM_3C`]()

```c
1, sect_rebar, TYPE, FIBER
2, sect_rebar, ADDFIBER, 0.105, 0.105, 0.000381
2, sect_rebar, ADDFIBER, 0.105, -0.105, 0.000381
2, sect_rebar, ADDFIBER, -0.105, -0.105, 0.000381
2, sect_rebar, ADDFIBER, -0.105, 0.105, 0.000381 
```

#### 自定义截面 `CUSTOM`

![](/PICS/SectionCustom.png)

> $N_{sect}$, sectName, `SHAPE`, $A$, $I_y$, $I_z$, $I_{yz}$

| 参数     | 说明              |
| -------- | ----------------- |
| $A$      | 截面面积          |
| $I_y$    | 截面 $y$ 向惯性矩 |
| $I_z$    | 截面 $z$ 向惯性矩 |
| $I_{yz}$ | 截面极惯性矩      |


- 适用单元
  - [杆单元 `TRUSS`]()
  - [索单元 `CABLE`]()

```c
1, sect_custom, TYPE, CUSTOM
1, sect_custom, SHAPE, 0.5, 0.1, 0.1, 0.2
```

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

