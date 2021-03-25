# 求解步类型 `TYPE`

- `TYPE`字段的求解步类型设置必须在其他设置字段前

---

## 输入格式

> stepName, `TYPE`，stepType

| 参数               | 说明                                                 |
| ------------------ | ---------------------------------------------------- |
| `KEYWORD` = `TYPE` |                                                      |
| stepType           | 求解步类型，可为 `INITIAL`、`STATIC`、`DYNA` 或 `SHAPE` |

---

## 示例

```c
step1, STEP_TYPE, STATIC
step2, STEP_TYPE, DYNA
```