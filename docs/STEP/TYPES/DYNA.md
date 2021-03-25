# 动力求解步 `DYNA`

---

## 必选参数

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md)
  - `TYPE` = `DYNA`
- [步长控制 `TIME`](/STEP/GENERAL/TIME.md)

## 可选参数

- [输出控制 `OUTPUT`](/STEP/GENERAL/OUTPUT.md)
- [阻尼控制 `DAMPING`](/STEP/GENERAL/DAMPING.md)
- [荷载组设置 `LOAD`](/STEP/GROUP/LOAD.md)
  - 仅允许施加 [动力荷载 `DYNA`]()
- [边界组设置 `CONSTRAINT`](/STEP/GROUP/CONSTRAINT.md)
  - 仅允许施加 [动力边界 `DYNA`]()

---

## 示例

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