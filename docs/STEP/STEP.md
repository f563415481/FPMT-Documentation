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

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md)
- [步长控制 `TIME`](/STEP/GENERAL/TIME.md)
- [收敛控制 `CONV`](/STEP/GENERAL/CONV.md)
- [阻尼控制 `DAMPING`](/STEP/GENERAL/DANPING.md)
- [加载控制 `LOADING`](/STEP/GENERAL/LOADING.md)
- [输出控制 `OUTPUT`](/STEP/GENERAL/OUTPUT.md)
- [找形控制 `SHAPE`](/STEP/GENERAL/SHAPE.md)

## 作用组设置

- [荷载组设置 `LOAD`](/STEP/GROUP/LOAD.md)
- [边界组设置 `CONSTRAINT`](/STEP/GROUP/CONSTRAINT.md)

---

## 求解步类型

- [初始求解步 `INITIAL`](/STEP/TYPES/INITIAL.md)
- [静力求解步 `STATIC`](/STEP/TYPES/STATIC.md)
- [动力求解步 `DYNA`](/STEP/TYPES/DYNA.md)
- [形态求解步 `SHAPE`](/STEP/GENERAL/SHAPE.md)

---

## 示例

```c
/CONSTRAINT/
cons1, STATIC, FIXED, ...
cons2, DYNA, DISP, ...
##

/LOAD/
load1, STATIC, FORCE, ...
##

/STEP/
step_initial, TYPE, INITIAL
step_initial, CONSTRAINT, cons1, YES
step_static, TYPE, STATIC
step_static, TIME, ...
step_static, LOAD, load1, YES
step_dyna, TYPE, DYNA
step_dyna, TIME, ...
step_dyna, CONSTRAINT, cons2, NO
## 
```

