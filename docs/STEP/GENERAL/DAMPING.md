# 阻尼控制 `DAMPING`

---

## 输入格式

> stepName, `DAMPING`, $b_{global}$, $\alpha$, $\beta$

| 参数                  | 说明                                                    |
| --------------------- | ------------------------------------------------------- |
| `KEYWORD` = `DAMPING` |                                                         |
| $b_{global}$          | 是否使用全局阻尼参数，`ON`为开启，`OFF`为关闭，默认开启 |
| $\alpha$              | 全局质量阻尼系数，默认为 100                            |
| $\beta$               | 全局刚度阻尼系数，默认为 0                              |

`注：`
- 若不对`DAMPING`字段的参数进行设置，则计算采用 $\alpha=100$ 和 $\beta=0$ 进行计算
- 若 $b_{autoH}$ = `OFF`，则无需设置 $\alpha$ 和 $\beta$

## 前置条件

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md) 已设置

---

## 示例

```c
step1, STEP_TYPE, STATIC
step1, DAMPING, ON, 5, 0.1
```