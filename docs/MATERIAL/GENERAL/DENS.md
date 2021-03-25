# 材料密度 `DENS`

---

## **输入格式**

> $N_{mat}$, matName, `DENS`, $\rho$

| 材料参数       | 参数说明     |
| -------------- | ------------ |
| `KEYWORD`=`EM` |              |
| $\rho$         | 材料质量密度 |


## 前置条件

- [材料种类 `TYPE`](/MATERIAL/GENERAL/TYPE.md) 已定义

## 示例

```c
1, mat_LE, TYPE, LE
1, mat_LE, DENS, 7850.00
```