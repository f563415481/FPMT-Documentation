# 初始求解步 `INITIAL`

- 任何求解过程均需要对初始求解步进行设置，且必须为第一个设置的求解步

---

## 必选参数

- [求解步类型 `TYPE`](/STEP/GENERAL/TYPE.md)
  - `TYPE` = `INITIAL`

## 可选参数

- [荷载组设置 `LOAD`](/STEP/GROUP/LOAD.md)
  - 仅允许施加 [静力荷载 `STATIC`]()
  - 若继承荷载效应，即 $b_{inherit}$ = `YES`，则等效于在下一求解步开始时刻瞬时施加该荷载
  - 若不继承荷载效应，即 $b_{inherit}$ = `NO`，则此荷载无任何效果

- [边界组设置 `CONSTRAINT`](/STEP/GROUP/CONSTRAINT.md)
  - 仅允许施加 [恒定边界 `STATIC`]()
  - 若继承边界效应，即 $b_{inherit}$ = `YES`，则等效于在下一求解步开始时刻瞬时施加该边界约束
  - 若不继承边界效应，即 $b_{inherit}$ = `NO`，则此边界约束无任何效果

---

## 示例

```c
/CONSTRAINT/
cons1, STATIC, FIXED, ...
##

/STEP/
step_initial, TYPE, INITIAL
step_initial, CONSTRAINT, cons1, YES
## 
```