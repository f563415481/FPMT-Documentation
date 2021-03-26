# 边界 /CONSTRAINT/

[SEQUENCE]: /SEQUENCE/SEQUENCE.md
[PARTICLE]: /PARTICLE/PARTICLE.md
[PARTICLESET]: /SET/PARTICLESET.md

---

## 通用输入格式

> /CONSTRAINT/<br>
consName, `CONSTYPE`, `OBJECTTYPE`, setName...<br>
\#\#br

| 参数         | 说明                                                                                                  |
| ------------ | ----------------------------------------------------------------------------------------------------- |
| loadName     | 边界组名称                                                                                            |
| `CONSTYPE`   | 边界类别，为`STATIC`或`DYNA`                                                                          |
| `OBJECTTYPE` | 边界子类别，为`GRAVITY`、`FORCE`或`ACEL`                                                              |
| setName      | 作用对象名称，可为 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称，或 [质点 `/PARTICLE/`][PARTICLE] 编号 |

---

## 边界种类

### 恒定边界 `STATIC`

#### 固定边界 `FIXED`

- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义

> loadName, `STATIC`, `FIXED`, setName, $DOF_i$, $DOF_j$...

| 参数             | 说明                                                                  |
| ---------------- | --------------------------------------------------------------------- |
| setName          | 施加约束的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称                |
| $DOF_i$, $DOF_j$ | 施加约束的自由度标识符，可设定平动 3 分量 [1-3] 以及转动 3 分量 [4-6] |

```C++
/PARTICLE_SET/
nset1, ...
##

/CONSTRAINT/
cons_1, STATIC, FIXED, nset1, 1, 2, 3, 4, 5, 6
## 
```

#### 位移边界 `DISP`

- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义

> loadName, `STATIC`, `FORCE`, setName, $DOF_i$, $d_i$...

| 参数           | 说明                                                                                |
| -------------- | ----------------------------------------------------------------------------------- |
| setName        | 施加约束的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称                              |
| $DOF_i$, $d_i$ | 施加约束的自由度标识符与对应位移分量，可设定平动 3 分量 [1-3] 以及转动 3 分量 [4-6] |

```C++
/PARTICLE_SET/
nset1, ...
##

/CONSTRAINT/
cons_1, STATIC, DISP, nset1, 1, 0.5, 2, 0.1
##
```

#### 初速度边界 `VEL`

- 仅在初始求解步 `INITIAL` 中设置有效
- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义

> loadName, `STATIC`, `VEL`, setName, $DOF_i$, $v_i$...

| 参数           | 说明                                                                                  |
| -------------- | ------------------------------------------------------------------------------------- |
| setName        | 施加约束的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称                                |
| $DOF_i$, $v_i$ | 施加约束的自由度标识符与对应初速度分量，可设定平动 3 分量 [1-3] 以及转动 3 分量 [4-6] |

```C++
/PARTICLE_SET/
nset1, ...
##

/CONSTRAINT/
cons_1, STATIC, VEL, nset1, 1, 0.5, 2, 0.1
##
```

#### 弹簧阻尼边界 `SPDP`

- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义

> loadName, `STATIC`, `SPDP`, setName, $DOF_i$, $K_i$, $C_i$...

| 参数    | 说明                                                                  |
| ------- | --------------------------------------------------------------------- |
| setName | 施加质点集中力的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称          |
| $DOF_i$ | 施加约束的自由度标识符，可设定平动 3 分量 [1-3] 以及转动 3 分量 [4-6] |
| $K_i$   | 与自由度标识符对应的弹簧刚度                                          |
| $C_i$   | 与自由度标识符对应的阻尼系数                                          |

```C++
/PARTICLE_SET/
nset1, ...
##

/CONSTRAINT/
cons_1, STATIC, SPDP, nset1, 3, 2e6, 1e3
##
```

### 动力边界 `DYNA`

#### 位移约束时程 `DISP`

- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义
  - [时程序列 `/SEQUENCE/`][SEQUENCE] 已定义

> loadName, `DYNA`, `FORCE`, setName, $DOF_i$, seqName...

| 参数    | 说明                                                                      |
| ------- | ------------------------------------------------------------------------- |
| setName | 施加约束时程的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称                |
| $DOF_i$ | 施加约束时程的自由度标识符，可设定平动 3 分量 [1-3] 以及转动 3 分量 [4-6] |
| seqName | 施加在 $DOF_i$ 的位移时程所使用的 [时程序列 `/SEQUENCE/`][SEQUENCE] 名称  |

```C++
/PARTICLE_SET/
nset1, ...
##

/SEQUENCE/
seq1, DATA, ...
...
seq2, DATA, ...
...
##

/CONSTRAINT/
dyna_force, DYNA, DISP, nset1, 1, seq1, 2, seq2
## 
```

#### 速度约束时程 `VEL`

- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义
  - [时程序列 `/SEQUENCE/`][SEQUENCE] 已定义

> loadName, `DYNA`, `VEL`, setName, $DOF_i$, seqName...

| 参数    | 说明                                                                      |
| ------- | ------------------------------------------------------------------------- |
| setName | 施加约束时程的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称                |
| $DOF_i$ | 施加约束时程的自由度标识符，可设定平动 3 分量 [1-3] 以及转动 3 分量 [4-6] |
| seqName | 施加在 $DOF_i$ 的速度时程所使用的 [时程序列 `/SEQUENCE/`][SEQUENCE] 名称  |

```C++
/PARTICLE_SET/
nset1, ...
##

/SEQUENCE/
seq1, DATA, ...
...
seq2, DATA, ...
...
##

/CONSTRAINT/
dyna_force, DYNA, VEL, nset1, 1, seq1, 2, seq2
## 
```

