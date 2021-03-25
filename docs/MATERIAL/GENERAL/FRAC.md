# 材料断裂参数 `FRAC`

---

## 输入格式

> $N_{mat}$, matName, `FRAC`, $\sigma_{max}$, $E_{fracture}$

| 材料参数           | 参数说明       |
| ------------------ | -------------- |
| `KEYWORD` = `FRAC` | Fracture 缩写  |
| $\sigma_{max}$     | 材料临界应力   |
| $E_{fracture}$     | 材料断裂释放能 |

## 前置条件

- [材料种类 `TYPE`](/MATERIAL/GENERAL/TYPE.md) 已定义

## 示例

```c
1, mat1, TYPE, LE
1, mat1, FRAC, 7.0e8, 12.25e3
```