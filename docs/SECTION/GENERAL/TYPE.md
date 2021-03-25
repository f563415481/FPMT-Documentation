# 截面种类 `TYPE`

---

## 输入格式

> $N_{sect}$, sectName, `TYPE`, sectType

| 截面参数         | 参数说明                                                  |
| ---------------- | --------------------------------------------------------- |
| `KEYWORD` = `TYPE` |                                                           |
| sectType         | 截面种类，可选 `TUBE`、`ROUND`、`RECT`、`BOX`、`THICK`、`CUSTOM`、`FIBER` 等 |

---

## 示例

```c
1, sect_TUBE, TYPE, TUBE
1, sect_TUBE, ...
2, sect_BILH, TYPE, RECT
2, sect_BILH, ... 
```