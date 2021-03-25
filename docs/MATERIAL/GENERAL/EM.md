# 材料弹性模量 `EM`

---

## 输入格式

> $N_{mat}$, matName, `EM`, $E$

| 材料参数       | 参数说明     |
| -------------- | ------------ |
| `KEYWORD`=`EM` |              |
| $E$            | 材料弹性模量 |

## 前置条件

- [材料种类 `TYPE`](/MATERIAL/GENERAL/TYPE.md) 已定义

## 示例

```c
1, mat_LE, TYPE, LE
1, mat_LE, EM, 2.06e+11
```