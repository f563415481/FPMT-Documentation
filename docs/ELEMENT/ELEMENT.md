# 单元定义

---

## 通用输入格式

### 单元定义

> /ELEM/<br>
$N_{elem}$, `TYPE`, $\{nd_i\}_{n}$, $N_{real}$, $\{N_{sect}^i,N_{mat}^i\}_{m}$<br>
\#\#<br>

| 参数                           | 值                                                                                 |
| ------------------------------ | ---------------------------------------------------------------------------------- |
| $N_{elem}$                     | 单元序号, 从 1 开始编号                                                            |
| `TYPE`                         | 单元类别                                                                           |
| $\{nd_i\}_{n}$                 | 单元质点序号, 个数为单元节点数                                                     |
| $N_{real}$                     | 实常数 /REALCONSTANT/编号，不需要的编号可置0或空格                                 |
| $\{N_{sect}^i,N_{mat}^i\}_{m}$ | 每一组分所对应的截面 /SECTION/编号和材料 /MATERIAL/编号，不需要的置0，个数为组分数 |


**前置条件**

- [质点 `/PARTICLE/`](/PARTICLE/PARTICLE.md) 已定义
- [实常数 `/REALCONSTANT/`](/REALCONSTANT/REALCONSTANT.md) 已定义
- [截面 `/SECTION/`](/SECTION/SECTION.md) 已定义
- [材料 `/MATERIAL/`](/MATERIAL/MATERIAL.md) 已定义

### 单元属性设置

> /ELEM_PROP/<br>
elemSetName, `PROP_TYPE`,  `FLAG`<br>
\#\#<br>

| 参数        | 值                              |
| ----------- | ------------------------------- |
| elemSetName | 属性作用的单元集 /ELEM_SET/名称 |
| `PROP_TYPE` | 单元属性种类                    |
| `FLAG`      | 对应的属性标识符                |


**前置条件**

- 单元集 /ELEM_SET/ 已定义

---

## 单元种类

### 线单元

- [杆单元 `TRUSS`](https://www.wolai.com/p4rVeCU2JaWc5i3aRdbUYf)
- [索单元 `CABLE`](https://www.wolai.com/7yzZvHR7NyZ5hwZ4SNxcuz)
- [梁单元 `BEAM`](https://www.wolai.com/xwh8tQmnufeE8XNkExCcKF)
- [纤维梁单元 `FIBER_BEAM`](https://www.wolai.com/m5V9vvS1z3XqXkisoknPjw)

### 平面单元

- [三角形平面单元 `PLANE_TRI`](https://www.wolai.com/7inNHnhQiJK8GBG62Szi2E)
- [四边形平面单元 `PLANE_QUAD`](https://www.wolai.com/4iwWRjQMJjuLijwxbGBUoD)

### 三维面单元

- [三角形膜单元 `MEMBRANE_TRI`](https://www.wolai.com/232Hfc4vvCcHFFttnftayp)
- [三角形壳单元 `SHELL_TRI`](https://www.wolai.com/ikhB7er5CskKCTcjH9sZDy)

### 实体单元

- [四面体实体单元 `SOLID_TETRA`](https://www.wolai.com/s7R6BiBYN9ipWNeDcdp2Jv)
- [六面体实体单元 `SOLID_HEX`](https://www.wolai.com/rT4fQtXvyMDkTh1moLiB8L)

### 组合单元

- [双组纤维梁单元 `FIBER_BEAM_2C`](https://www.wolai.com/atsYpZmarqytbbuXtZFGgy)
- [三组纤维梁单元 `FIBER_BEAM_3C`](https://www.wolai.com/shLy3eWpJKroLUhFwoAkMt)

### 特殊单元

- [质量惯性矩单元 `MASS`](https://www.wolai.com/t5aNa2XkZs8eQQRDrnwB18)
- [弹簧阻尼单元 `SPRING`](https://www.wolai.com/p13v9L2UqcVRpYp46eS8oV)
- [三角形界面单元 `INTERFACE`](https://www.wolai.com/akQ9mhnUqtkTV5CYzoxrQ2)

