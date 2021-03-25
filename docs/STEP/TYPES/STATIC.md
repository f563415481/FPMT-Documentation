# 静力求解步 `STATIC`

---

## 必选参数

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md)
  - `TYPE` = `STATIC`
- [步长控制 `TIME`](/STEP/GENERAL/TIME.md)

## 可选参数

- [输出控制 `OUTPUT`](/STEP/GENERAL/OUTPUT.md)
- [阻尼控制 `DAMPING`](/STEP/GENERAL/DAMPING.md)
- [加载控制 `LOADING`](/STEP/GENERAL/LOADING.md)
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