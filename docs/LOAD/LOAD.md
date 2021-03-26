# 荷载 /LOAD/

[SEQUENCE]: /SEQUENCE/SEQUENCE.md
[PARTICLE]: /PARTICLE/PARTICLE.md
[PARTICLESET]: /SET/PARTICLESET.md

---

## 通用输入格式

> /LOAD/<br>
loadName, `LOADTYPE`, `OBJECTTYPE`, setName...<br>
\#\#br

| 参数         | 说明                                                                                                  |
| ------------ | ----------------------------------------------------------------------------------------------------- |
| loadName     | 荷载组名称                                                                                            |
| `LOADTYPE`   | 荷载类别，为`STATIC`或`DYNA`                                                                          |
| `OBJECTTYPE` | 荷载子类别，为`GRAVITY`、`FORCE`或`ACEL`                                                              |
| setName      | 作用对象名称，可为 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称，或 [质点 `/PARTICLE/`][PARTICLE] 编号 |

---

## 荷载种类

### 静力荷载 `STATIC`

#### 质点静力荷载

##### 重力 `GRAVITY`

- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义

> loadName, `STATIC`, `GRAVITY`, setName, $DOF_i$, $g_i$...

| 参数           | 说明                                                   |
| -------------- | ------------------------------------------------------ |
| setName        | 施加重力的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称 |
| $DOF_i$, $g_i$ | 自由度标识符与对应重力加速度分量，可设定平动 3 分量    |

```C++
/PARTICLE_SET/
all_set, ...
##

/LOAD/
load_gravity, STATIC, GRAVITY, all_set, 3, -9.8
## 
```

##### 质点集中力 `FORCE`

- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义

> loadName, `STATIC`, `FORCE`, setName, $DOF_i$, $f_i$...

| 参数           | 说明                                                                    |
| -------------- | ----------------------------------------------------------------------- |
| setName        | 施加质点集中力的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称            |
| $DOF_i$, $f_i$ | 自由度标识符与对应力分量，可设定平动 3 分量 [1-3] 以及转动 3 分量 [4-6] |

```C++
/PARTICLE_SET/
nset1, ...
##

/LOAD/
load_1, STATIC, FORCE, nset1, 1, 2000, 3, 1000
## 
```

##### 质点加速度 `ACEL`

- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义

> loadName, `STATIC`, `ACEL`, setName, $DOF_i$, $a_i$...

| 参数           | 说明                                                                        |
| -------------- | --------------------------------------------------------------------------- |
| setName        | 施加质点加速度的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称                |
| $DOF_i$, $a_i$ | 自由度标识符与对应加速度分量，可设定平动 3 分量 [1-3] 以及转动 3 分量 [4-6] |

```C++
/PARTICLE_SET/
nset1, ...
##

/LOAD/
load_1, STATIC, ACEL, nset1, 1, 0.05, 3, 0.1
## 
```

#### 线分布静力荷载

To be added...

#### 面分布静力荷载

To be added...

### 动力荷载 `DYNA`

#### 质点动力荷载

##### 质点集中力时程 `FORCE`

- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义
  - [时程序列 `/SEQUENCE/`][SEQUENCE] 已定义

> loadName, `DYNA`, `FORCE`, setName, $DOF_i$, seqName...

| 参数    | 说明                                                                          |
| ------- | ----------------------------------------------------------------------------- |
| setName | 施加质点集中力时程的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称              |
| $DOF_i$ | 集中力时程所作用的自由度标识符，可设定平动 3 分量 [1-3] 以及转动 3 分量 [4-6] |
| seqName | 施加在 $DOF_i$ 的集中力时程所使用的 [时程序列 `/SEQUENCE/`][SEQUENCE] 名称    |

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

/LOAD/
dyna_force, DYNA, FORCE, nset1, 1, seq1, 2, seq2
## 
```

##### 质点加速度时程 `ACEL`

- 前置条件
  - [质点集 `/PARTICLE_SET/`][PARTICLESET] 已定义
  - [时程序列 `/SEQUENCE/`][SEQUENCE] 已定义

> loadName, `DYNA`, `ACEL`, setName, $DOF_i$, seqName...

| 参数    | 说明                                                                          |
| ------- | ----------------------------------------------------------------------------- |
| setName | 施加质点加速度时程的 [质点集 `/PARTICLE_SET/`][PARTICLESET] 名称              |
| $DOF_i$ | 加速度时程所作用的自由度标识符，可设定平动 3 分量 [1-3] 以及转动 3 分量 [4-6] |
| seqName | 施加在 $DOF_i$ 的加速度时程所使用的 [时程序列 `/SEQUENCE/`][SEQUENCE] 名称    |

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

/LOAD/
dyna_force, DYNA, ACEL, nset1, 1, seq1, 2, seq2
## 
```

#### 线分布动力荷载

To be added...

#### 面分布动力荷载

To be added...

