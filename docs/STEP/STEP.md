# 求解步 `STEP`

---

## 通用输入格式

> /STEP/<br>
stepName, `KEYWORD`, $P_1$...<br>
\#\#<br>

| 参数      | 说明       |
| --------- | ---------- |
| stepName  | 求解步名称 |
| `KEYWORD` | 参数类型   |
| $P_1$...  | 求解步参数 |

---

## 参数设置

### 必选参数

#### 求解步类型 `TYPE`

!> `TYPE`字段的求解步类型设置必须在其他设置字段前

> stepName, `TYPE`，stepType

| 参数               | 说明                                                 |
| ------------------ | ---------------------------------------------------- |
| `KEYWORD` = `TYPE` |                                                      |
| stepType           | 求解步类型，可为 `INITIAL`、`STATIC`、`DYNA` 或 `SHAPE` |

```c
stepInit, TYPE, INITIAL
step1, TYPE, STATIC
step3, TYPE, SHAPE
step2, TYPE, DYNA
```

#### 步长控制 `TIME`

- 除了`INITIAL`求解步之外，其余类型的求解步`TIME`参数必须设置
- 前置条件
  - 求解步类型 `TYPE` 已设置

> stepName, `TIME`, $t_{total}$, $h$, $b_{autoH}$

| 参数               | 说明                                                      |
| ------------------ | --------------------------------------------------------- |
| `KEYWORD` = `TYPE` |                                                           |
| $t_{total}$        | 求解步总时长，默认                                        |
| $h$                | 求解步初始时间步长                                        |
| $b_{autoH}$        | 是否开启自动时间步长，`ON` 为开启，`OFF` 为关闭，默认关闭 |

?> 若开启自动时间步长，$h$ 参数为求解初始时刻的时间步长，否则为全程恒定步长

```c
step1, STEP_TYPE, STATIC
step1, TIME, 5.0, 1e-4, OFF
```

### 可选参数

#### 收敛控制 `CONV`

- 若不对`CONV`字段进行设置，则不进行收敛判断
- 前置条件
  - 求解步类型 `TYPE` 为 `STATIC` 或 `SHAPE`
  - 步长控制 `TIME` 已设置

> stepName, `CONV`, $n_{interval}$, $\xi_{d}$, $\xi_{f}$

| 参数               | 说明                                                  |
| ------------------ | ----------------------------------------------------- |
| `KEYWORD` = `CONV` |                                                       |
| $n_{interval}$     | 收敛判断的步数间隔                                    |
| $\xi_{d}$          | 收敛判断的位移增量判据，默认 $\xi_{d}=1\times10^{-8}$ |
| $\xi_{f}$          | 收敛判断的不平衡力判据，默认 $\xi_{f}=5\times10^{-6}$ |

```c
step1, TYPE, STATIC
step1, TIME, 5.0, 1e-4, OFF 
step1, CONV, 50, , 3e-6
```

#### 阻尼控制 `DAMPING`

- 前置条件
  - 求解步类型 `TYPE` 为 `STATIC` 或 `DYNA`

> stepName, `DAMPING`, $b_{global}$, $\alpha$, $\beta$

| 参数                  | 说明                                                    |
| --------------------- | ------------------------------------------------------- |
| `KEYWORD` = `DAMPING` |                                                         |
| $b_{global}$          | 是否使用全局阻尼参数，`ON`为开启，`OFF`为关闭，默认开启 |
| $\alpha$              | 全局质量阻尼系数，默认为 100                            |
| $\beta$               | 全局刚度阻尼系数，默认为 0                              |

?> 若不对`DAMPING`字段的参数进行设置，则计算采用 $\alpha=100$ 和 $\beta=0$ 进行计算<br>
若 $b_{autoH}$ = `OFF`，则无需设置 $\alpha$ 和 $\beta$<br>

```c
step1, TYPE, STATIC
step1, DAMPING, ON, 5, 0.1
```

#### 加载控制 `LOADING`

- 前置条件
  - 求解步类型 `TYPE` 为 `STATIC`

> $stepName$, `LOADING`, `LOADING_TYPE`, $\lambda_{ramp}$, $n_{seg}$

| 参数                  | 说明                                                                         |
| --------------------- | ---------------------------------------------------------------------------- |
| `KEYWORD` = `LOADING` |                                                                              |
| `LOADING_TYPE`        | 加载类型，可为瞬时加载 `INSTANT`、斜坡加载 `RAMP` 或阶梯加载 `LADDER`        |
| $\lambda_{ramp}$      | 加载斜坡段占总时长的比例，$\lambda_{ramp}\in[0,1]$，默认$\lambda_{ramp}=0.5$ |
| $n_{seg}$             | 加载的阶梯段数，默认 $n_{seg}=1$                                             |

- 瞬时加载 `INSTANT`: 强制 $\lambda_{ramp}=0$ 且 $n_{seg}=1$，无需对 $\lambda_{ramp}$ 和 $n_{seg}$ 进行设置

![instant](/IMAGES/LoadingStep.png)

- 斜坡加载 `RAMP`: 强制 $n_{seg}=1$，无需对 $n_{seg}$ 进行设置

![ramp](/IMAGES/LoadingRamp.png)

- 阶梯加载 `LADDER`

![ladder](/IMAGES/LoadingLadder.png)

```c
step1, TYPE, STATIC
step1, LOADING_PARAM, INSTANT

step2, TYPE, STATIC
step2, LOADING_PARAM, RAMP, 0.8

step3, TYPE, STATIC
step3, LOADING_PARAM, LADDER, 0.5, 10
```

#### 输出控制 `OUTPUT`

- 前置条件
  - 求解步类型 `TYPE` 已设置
  - 步长控制 `TIME` 已设置

> stepName, `OUTPUT`, $n_{total}$, $idx_{start}$, $idx_{end}$

| 参数                 | 说明                                         |
| -------------------- | -------------------------------------------- |
| `KEYWORD` = `OUTPUT` |                                              |
| $n_{total}$          | 总输出步数，默认 $n_{total} = 100$              |
| $idx_{start}$        | 进行输出的起始步编号，默认为 0                |
| $idx_{end}$          | 进行输出的终止步编号，默认为求解步的终止子步 |

?> 需要保证 $n_{total}<(idx_{end}-idx_{start})$

```c
step1, TYPE, STATIC
step1, TIME, 10.0, 1e-2
step1, OUTPUT, 500 

step2, TYPE, DYNA
step2, TIME, 10.0, 1e-2
step2, OUTPUT, 100, 500, 1000
```

#### 找形控制 `SHAPE`

- 前置条件
  - 求解步类型 `TYPE` 为 `SHAPE`
  - 步长控制 `TIME` 已设置

> stepName, `SHAPE`, $\gamma_{soft}$, $C_{pace}$, $b_{diss}$, $\gamma_{diss}$

| 参数                | 说明                                                                                |
| ------------------- | ----------------------------------------------------------------------------------- |
| `KEYWORD` = `SHAPE` |                                                                                     |
| $\gamma_{soft}$     | 柔性体弹性模量缩放系数，$\gamma_{soft}\in(0,1]$，默认$\gamma_{soft}=1\times10^{-6}$ |
| $C_{pace}$          | 步幅放大系数，默认 $C_{pace}=100$                                                   |
| $b_{diss}$          | 是否使用虚拟耗能，$b_{diss} = $`ON`（使用）或 $b_{diss} = $`OFF`（不使用）              |
| $\gamma_{diss}$     | 虚拟耗能系数，$\gamma_{diss}\in[0,1]$，一般取 $95\%$                                |

?> 若 $b_{diss}$ = `OFF`，则可不对 $\gamma_{diss}$ 进行设置，此时 $\gamma_{diss}=0\%$

```c
step1, TYPE, SHAPE
step1, TIME, 10.0, 1e-2
step1, SHAPE, 1e-6, 50, ON, 0.98
```

### 作用组设置

#### 荷载组设置 `LOAD`

- 前置条件
  - 求解步类型 `TYPE` 已设置
  - [荷载 `/LOAD/`]() 已定义

> stepName, `LOAD`, loadName, $b_{inherit}$ ...

| 参数               | 说明                                                                       |
| ------------------ | -------------------------------------------------------------------------- |
| `KEYWORD` = `LOAD` |                                                                            |
| loadName         | [荷载 `/LOAD/`]() 名称                                                            |
| $b_{inherit}$      | 是否继承至后续求解步，$b_{inherit}$ = `YES` 或 $b_{inherit}$ = `NO` |

```c
/LOAD/
load1, STATIC, ...
load2, STATIC, ...
##

/STEP/
step1, TYPE, STATIC
step1, TIME, ...
step1, LOAD, load1, YES, load2, NO
##
```

#### 边界组设置 `CONSTRAINT`

- 前置条件
  - 求解步类型 `TYPE` 已设置
  - [边界 `/CONSTRAINT/`]() 已定义

> stepName, `CONSTRAINT`, consName, $b_{inherit}$ ...

| 参数                     | 说明                                                                |
| ------------------------ | ------------------------------------------------------------------- |
| `KEYWORD` = `CONSTRAINT` |                                                                     |
| consName                 | [边界 `/CONSTRAINT/`]() 名称                                        |
| $b_{inherit}$            | 是否继承至后续求解步，$b_{inherit}$ = `YES` 或 $b_{inherit}$ = `NO` |

```c
/CONSTRAINT/
cons1, DYNA, ...
cons2, DYNA, ...
##

/STEP/
step1, TYPE, DYNA
step1, TIME, ...
step1, CONSTRAINT, cons1, NO, cons2, YES
##
```

## 求解步类型

### 初始求解步 `INITIAL`

!> 任何求解过程均需要对初始求解步进行设置，且必须为第一个设置的求解步

- 必选参数
  - 求解步类型 `TYPE`: `INITIAL`
- 可选参数
  - 荷载组设置 `LOAD`: 仅允许施加 [静力荷载 `STATIC`]()
  - 边界组设置 `CONSTRAINT`: 仅允许施加 [恒定边界 `STATIC`]()

```c
/CONSTRAINT/
cons1, STATIC, FIXED, ...
##

/STEP/
step_initial, TYPE, INITIAL
step_initial, CONSTRAINT, cons1, YES
## 
```

### 静力求解步 `STATIC`

- 必选参数
  - 求解步类型 `TYPE`: `STATIC`
  - 步长控制 `TIME`
- 可选参数：输出控制 `OUTPUT`
  - 阻尼控制 `DAMPING`
  - 加载控制 `LOADING`
  - 收敛控制 `CONV`
  - 荷载组设置 `LOAD`: 仅允许施加 [静力荷载 `STATIC`]()
  - 边界组设置 `CONSTRAINT`: 仅允许施加 [恒定边界 `STATIC`]()

```c
/CONSTRAINT/
cons1, STATIC, FIXED, ...
##

/LOAD/
load1, STATIC, FORCE, ...
##

/STEP/
step_static, TYPE, STATIC
step_static, TIME, ...
step_static, CONSTRAINT, cons1, YES
step_static, LOAD, load1, NO
## 
```

### 动力求解步 `DYNA`

- 必选参数
  - 求解步类型 `TYPE`: `DYNA`
  - 步长控制 `TIME`
- 可选参数
  - 输出控制 `OUTPUT`
  - 阻尼控制 `DAMPING`
  - 荷载组设置 `LOAD`: 仅允许施加 [动力荷载 `DYNA`]()
  - 边界组设置 `CONSTRAINT`: 仅允许施加 [动力边界 `DYNA`]()

```c
/PARTICLE_SET/
cons_set, ...
##

/SEQUENCE/
seq1, DATA, 0, 1.0
seq1, DATA, 0.2, 5.3
...
##

/CONSTRAINT/
cons1, DYNA, DISP, cons_set, 1, seq1
##

/STEP/
step_dyna, TYPE, DYNA
step_dyna, TIME, ...
step_dyna, CONSTRAINT, cons1, NO
## 
```

### 形态求解步 `SHAPE`

- 必选参数
  - 求解步类型 `TYPE`: `SHAPE`
  - 步长控制 `TIME`
  - 找形控制 `SHAPE`
- 可选参数
  - 输出控制 `OUTPUT`
  - 阻尼控制 `DAMPING`
  - 收敛控制 `CONV`
  - 荷载组设置 `LOAD`: 仅允许施加 [静力荷载 `STATIC`]()
  - 边界组设置 `CONSTRAINT`: 仅允许施加 [恒定边界 `STATIC`]()

```c
/CONSTRAINT/
cons1, STATIC, FIXED, ...
##

/STEP/
step_shape, TYPE, SHAPE
step_shape, TIME, 10.0, 1e-2
step_shape, CONSTRAINT, cons1, YES
step_shape, SHAPE, 1e-6, 50, ON, 0.98
## 
```

