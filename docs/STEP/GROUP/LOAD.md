# 荷载组设置 `LOAD`

---

## 输入格式

> stepName, `LOAD`, loadName, $b_{inherit}$ ...

| 参数               | 说明                                                                       |
| ------------------ | -------------------------------------------------------------------------- |
| `KEYWORD` = `LOAD` |                                                                            |
| loadName         | [荷载 `/LOAD/`]() 名称                                                            |
| $b_{inherit}$      | 是否继承至后续求解步，$b_{inherit}$ = `YES` 或 $b_{inherit}$ = `NO` |


## 前置条件

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md) 已设置
- [荷载 `/LOAD/`]() 已定义

---

## 示例

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