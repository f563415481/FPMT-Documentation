# 实常数种类 `TYPE`

---

## 输入格式

> $N_{real}$, realName, `TYPE`, realType

| 截面参数         | 参数说明                                                  |
| ---------------- | --------------------------------------------------------- |
| `KEYWORD` = `TYPE` |                                                           |
| realType         | 实常数种类，可选 `INER`、`INTF`、`PRES`、`SPRG` 等 |

---

## 示例

```c
1, sect_TUBE, TYPE, TUBE
1, sect_TUBE, ...
2, sect_BILH, TYPE, RECT
2, sect_BILH, ... 
```