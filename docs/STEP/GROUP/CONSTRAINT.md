# 边界组设置 `CONSTRAINT` 

---

## 输入格式

> stepName, `CONSTRAINT`, consName, $b_{inherit}$ ...

| 参数                     | 说明                                                                |
| ------------------------ | ------------------------------------------------------------------- |
| `KEYWORD` = `CONSTRAINT` |                                                                     |
| consName                 | [边界 `/CONSTRAINT/`]() 名称                                        |
| $b_{inherit}$            | 是否继承至后续求解步，$b_{inherit}$ = `YES` 或 $b_{inherit}$ = `NO` |


## 前置条件

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md) 已设置
- [边界 `/CONSTRAINT/`]() 已定义

---

## 示例

```c
/CONSTRAINT/
cons1, DYNA, ...
cons2, DYNA, ...
##

/STEP/
step1, STEP_TYPE, DYNA
step1, TIME, ...
step1, CONSTRAINT, cons1, NO, cons2, YES
##
```