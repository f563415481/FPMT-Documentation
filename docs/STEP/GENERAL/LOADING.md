# 加载控制 `LOADING`

---

## 输入格式

> $stepName$, `LOADING`, `LOADING_TYPE`, $\lambda_{ramp}$, $n_{seg}$

| 参数                  | 说明                                                                         |
| --------------------- | ---------------------------------------------------------------------------- |
| `KEYWORD` = `LOADING` |                                                                              |
| `LOADING_TYPE`        | 加载类型，可为瞬时加载 `INSTANT`、斜坡加载 `RAMP` 或阶梯加载 `LADDER`        |
| $\lambda_{ramp}$      | 加载斜坡段占总时长的比例，$\lambda_{ramp}\in[0,1]$，默认$\lambda_{ramp}=0.5$ |
| $n_{seg}$             | 加载的阶梯段数，默认 $n_{seg}=1$                                             |

## 加载方式

- 瞬时加载 `INSTANT`

![instant](/LOADING_PICS/LoadingStep.png)

?> 强制 $\lambda_{ramp}=0$ 且 $n_{seg}=1$，无需对 $\lambda_{ramp}$ 和 $n_{seg}$ 进行设置

- 斜坡加载 `RAMP`

![ramp](/LOADING_PICS/LoadingRamp.png)

?> 强制 $n_{seg}=1$，无需对 $n_{seg}$ 进行设置

- 阶梯加载 `LADDER`

![ladder](/LOADING_PICS/LoadingLadder.png)


## 前置条件

- [求解步类型 `TYPE`](/step/GENERAL/TYPE.md) 已设置

---

## 示例

```c
step1, STEP_TYPE, STATIC
step1, LOADING_PARAM, INSTANT

step2, STEP_TYPE, STATIC
step2, LOADING_PARAM, RAMP, 0.8

step3, STEP_TYPE, STATIC
step3, LOADING_PARAM, LADDER, 0.5, 10
```