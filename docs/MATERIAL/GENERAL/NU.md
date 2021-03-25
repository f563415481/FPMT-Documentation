# 材料泊松比 `NU`

---

## 输入格式

> $N_{mat}$, matName, `NU`, $\nu$

| 材料参数       | 参数说明   |
| -------------- | ---------- |
| `KEYWORD`=`NU` |            |
| $\nu$          | 材料泊松比 |


## 前置条件

- [材料种类 `TYPE`](/MATERIAL/GENERAL/TYPE.md) 已定义

## 示例

```c
1, mat_LE, TYPE, LE
1, mat_LE, NU, 0.30
```