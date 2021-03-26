# 单元定义

[REAL]: /REALCONSTANT/REALCONSTANT.md
[SECT]: /SECTION/SECTION.md
[MAT]: /MATERIAL/MATERIAL.md

---

## 通用输入格式

### 单元定义

- 前置条件
  - [质点 `/PARTICLE/`](/PARTICLE/PARTICLE.md) 已定义
  - [实常数 `/REALCONSTANT/`](/REALCONSTANT/REALCONSTANT.md) 已定义
  - [截面 `/SECTION/`](/SECTION/SECTION.md) 已定义
  - [材料 `/MATERIAL/`](/MATERIAL/MATERIAL.md) 已定义

> /ELEM/<br>
$N_{elem}$, `TYPE`, $\{nd_i\}_{n}$, $N_{real}$, $\{N_{sect}^i,N_{mat}^i\}_{m}$<br>
\#\#

| 参数                           | 值                                                                                                     |
| ------------------------------ | ------------------------------------------------------------------------------------------------------ |
| $N_{elem}$                     | 单元序号, 从 1 开始编号                                                                                |
| `TYPE`                         | 单元类别                                                                                               |
| $\{nd_i\}_{n}$                 | 单元质点序号, 个数为单元节点数                                                                         |
| $N_{real}$                     | [实常数 /REALCONSTANT/][REAL] 编号，不需要的编号可置 0 或空格                                          |
| $\{N_{sect}^i,N_{mat}^i\}_{m}$ | 每一组分所对应的 [截面 /SECTION/][SECT] 编号和 [材料 /MATERIAL/][MAT] 编号，不需要的置 0，个数为组分数 |

### 单元属性设置

- 前置条件
  - [单元集 `/ELEM_SET/`](/SET/ELEMENTSET.md) 已定义

> /ELEM_PROP/<br>
elemSetName, `PROP_TYPE`,  `FLAG`<br>
\#\#

| 参数        | 值                              |
| ----------- | ------------------------------- |
| elemSetName | 属性作用的单元集 /ELEM_SET/名称 |
| `PROP_TYPE` | 单元属性种类                    |
| `FLAG`      | 对应的属性标识符                |

---

## 单元种类

### 线单元

#### 杆单元 `TRUSS`

> $N_{elem}$, `TRUSS`, $nd_1$, $nd_2$, *, $N_{sect}$, $N_{mat}$

#### 索单元 `CABLE`

> $N_{elem}$, `CABLE`, $nd_1$, $nd_2$, $N_{real}$, $N_{sect}$, $N_{mat}$

#### 梁单元 `BEAM`

> $N_{elem}$, `BEAM`, $nd_1$, $nd_2$, *, $N_{sect}$, $N_{mat}$

- `PROP_TYPE` = `SHAPE_FUNC` 梁形函数设置
  - `FLAG` = `EB` 采用Euler-Bernoulli梁的形函数 `DEFAULT`
  - `FLAG` = `TIMO` 采用Timoshenko梁的形函数

#### [纤维梁单元 `FIBER_BEAM`](https://www.wolai.com/m5V9vvS1z3XqXkisoknPjw)

> $N_{elem}$, `FIBER_BEAM`, $nd_1$, $nd_2$, *, $N_{sect}$, $N_{mat}$

- `PROP_TYPE` = `SHAPE_FUNC` 梁形函数设置
  - `FLAG` = `EB` 采用Euler-Bernoulli梁的形函数 `DEFAULT`
  - `FLAG` = `TIMO` 采用Timoshenko梁的形函数

### 二维面单元

#### 三角形平面单元 `PLANE_TRI`

> $N_{elem}$, `PLANE_TRI`, $nd_1$, $nd_2$, $nd_3$, *, $N_{sect}$, $N_{mat}$

- `PROP_TYPE` = `PLANE_TYPE` 平面单元状态设置
  - `FLAG` = `PLANE_STRAIN` 设置为平面应变单元 `DEFAULT`
  - `FLAG` = `PLANE_STRESS` 设置为平面应力单元

#### 四边形平面单元 `PLANE_QUAD`

> $N_{elem}$, `PLANE_TRI`, $nd_1$, $nd_2$, $nd_3$, $nd_4$, *, $N_{sect}$, $N_{mat}$

- `PROP_TYPE` = `PLANE_TYPE` 平面单元状态设置
  - `FLAG` = `PLANE_STRAIN` 设置为平面应变单元 `DEFAULT`
  - `FLAG` = `PLANE_STRESS` 设置为平面应力单元

### 三维面单元

#### 三角形膜单元 `MEMBRANE_TRI`

> $N_{elem}$, `PLANE_TRI`, $nd_1$, $nd_2$, $nd_3$, $N_{real}$, $N_{sect}$, $N_{mat}$

#### 四边形膜单元 `MEMBRANE_QUAD`

> $N_{elem}$, `PLANE_TRI`, $nd_1$, $nd_2$, $nd_3$, $nd_4$, $N_{real}$, $N_{sect}$, $N_{mat}$

#### 三角形壳单元 `SHELL_TRI`

> $N_{elem}$, `PLANE_TRI`, $nd_1$, $nd_2$, $nd_3$, $nd_4$, *, $N_{sect}$, $N_{mat}$

#### 四边形板单元 `PLATE`

> $N_{elem}$, `PLATE`, $nd_1$, $nd_2$, $nd_3$, $nd_4$, *, $N_{sect}$, $N_{mat}$

### 实体单元

#### 四面体实体单元 `SOLID_TETRA`

> $N_{elem}$, `SOLID_TETRA`, $nd_1$, $nd_2$, $nd_3$, $nd_4$, *, *, $N_{mat}$

#### 六面体实体单元 `SOLID_HEX`

> $N_{elem}$, `SOLID_TETRA`, $nd_1$, ..., $nd_8$, *, *, $N_{mat}$

- `PROP_TYPE` = `INTEGRAL_ORDER` 单元积分阶数设置
  - `FLAG` = `FULL` 完全积分单元  `DEFAULT`
  - `FLAG` = `REDUCED` 缩减积分单元

- `PROP_TYPE` = `SHAPE_FUNC` 单元形函数设置
  - `LAG` = `DEFAULT` 标准形函数  `DEFAULT` 
  - `FLAG` = `MEAN_BBAR` 单元内平均的 $\overline{B}$ 形函数
  - `FLAG` = `CENTER_BBAR` 以单元中心点代替单元内平均的 $\overline{B}$ 形函数

### 组合单元

#### 双组纤维梁单元 `FIBER_BEAM_2C`

> $N_{elem}$, `FIBER_BEAM_2C`, $nd_1$, $nd_2$, *, $N_{sect}^1$, $N_{mat}^1$, $N_{sect}^2$, $N_{mat}^2$

- `PROP_TYPE` = `SHAPE_FUNC` 梁形函数设置
  - `FLAG` = `EB` 采用 Euler-Bernoulli 梁的形函数 `DEFAULT`
  - `FLAG` = `TIMO` 采用 Timoshenko 梁的形函数

#### 三组纤维梁单元 `FIBER_BEAM_3C`

> $N_{elem}$, `FIBER_BEAM_3C`, $nd_1$, $nd_2$, *, $N_{sect}^1$, $N_{mat}^1$, $N_{sect}^2$, $N_{mat}^2$, $N_{sect}^3$, $N_{mat}^3$

- `PROP_TYPE` = `SHAPE_FUNC` 梁形函数设置
  - `FLAG` = `EB` 采用Euler-Bernoulli梁的形函数 `DEFAULT`
  - `FLAG` = `TIMO` 采用Timoshenko梁的形函数

### 特殊单元

#### 质量惯性矩单元 `MASS`

> $N_{elem}$, `MASS`, $nd_1$, $N_{real}$, *, *

#### 弹簧阻尼单元 `SPRING`

> $N_{elem}$, `SPRING`, $nd_1$, $N_{real}$, *, *

#### 三角形界面单元 `INTERFACE`

> $N_{elem}$, `INTERFACE`, $nd_1$, $nd_2$, $nd_3$, $N_{real}$, $N_{sect}$, $N_{mat}$

- 按照 3 个质点右手螺旋决定外法线方向
- `PROP_TYPE` = `TARGET_SLAVE` 界面单元主从设置
  - `FLAG` = `SLAVE` 从界面单元 `DEFALULT`
  - `FLAG` = `TARGET` 目标界面单元

