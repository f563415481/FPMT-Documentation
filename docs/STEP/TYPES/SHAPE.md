# 形态求解步 `SHAPE`

---

## 必选参数

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md)
  - `TYPE` = `SHAPE`
- [步长控制 `TIME`](/STEP/GENERAL/TIME.md)
- [找形控制 `SHAPE`](/STEP/TYPES/SHAPE.md)
- [输出控制 `OUTPUT`](/STEP/GENERAL/OUTPUT.md)

## 可选参数

- [阻尼控制 `DAMPING`](/STEP/GENERAL/DAMPING.md)
- [收敛控制 `CONV`](/STEP/GENERAL/CONV.md)
- [荷载组设置 `LOAD`](/STEP/GROUP/LOAD.md)
  - 仅允许施加 [静力荷载 `STATIC`]()
- [边界组设置 `CONSTRAINT`](/STEP/GROUP/CONSTRAINT.md)
  - 仅允许施加 [恒定边界 `STATIC`]()

---

## 示例

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