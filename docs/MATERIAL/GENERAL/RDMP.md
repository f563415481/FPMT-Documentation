# 材料阻尼 `RDMP`

---

## 输入格式

> $N_{mat}$, matName, `RDMP`, $\alpha$，$\beta$

| 材料参数 | 参数说明         |
| -------- | ---------------- |
| $\alpha$ | 材料质量阻尼系数 |
| $\beta$  | 材料刚度阻尼系数 |


## 前置条件

- [材料种类 `TYPE`](/MATERIAL/GENERAL/TYPE.md) 已定义

## 示例

```c
1, mat_LE, TYPE, LE
1, mat_LE, RDMP, 5, 0.01
```