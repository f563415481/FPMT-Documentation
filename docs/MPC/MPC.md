# 多质点约束 `MPC`

---

## 通用输入格式

> /MPC/<br>
mpcName, `TYPE`, $N_{targetParticle}$, $N_{slavePSet}$<br>
\#\#<br>

| 参数                 | 说明                                                 |
| -------------------- | ---------------------------------------------------- |
| mpcName              | 多质点约束名称                                       |
| `TYPE`               | 多质点约束种类，可为 `PIN`、`BEAM` 或 `PLANE`        |
| $N_{targetParticle}$ | 目标 [质点 `/PARTICLE/`](/PARTICLE/PARTICLE.md) 编号 |
| $N_{slavePSet}$      | 从属 [质点集 `/PARTICLE_SET/`]() 名称                |

---

## 前置条件

- [质点 `/PARTICLE/`](/PARTICLE/PARTICLE.md) 已定义
- [质点集 `/PARTICLE_SET/`]() 已定义

---

## 多质点约束种类 `TYPE` 

### 质点间铰接耦合 `PIN`

> $mpcName$, `PIN`, $N_{targetParticle}$, $N_{slavePSet}$

?> 将从属质点集中的质点与目标质点进行平动自由度耦合，使得参与耦合的质点的位移相同

### 质点间刚性耦合 `BEAM`

> $mpcName$, `BEAM`, $N_{targetParticle}$, $N_{slavePSet}$

?> 将从属质点集中的质点与目标质点进行全部自由度耦合，使得参与耦合的质点的位移与转角相同

### 质点与面刚性耦合 `PLANE`

> $mpcName$, `PLANE`, $N_{targetParticle}$, $N_{slavePSet}$

?> 将从属质点集所成面的等效转角与目标质点的转角自由度进行耦合，使得二者之间转动的保持刚性

---

## 示例

```c
/PARTICLE/
1, ...
...
12, ...
##

/PARTICLE_SET/
pin_set, ENUMERATE, 2, 3, 4
beam_set, ENUMERATE, 6
plane_set, GENERATE, 8, 12, 1
##

/MPC/
mpc1, PIN, 1, pin_set
mpc2, BEAM, 5, beam_set
mpc3, PLANE, 7, plane_set
##
```