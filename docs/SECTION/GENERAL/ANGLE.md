# 截面转角 `ANGLE`

---

## 输入格式

> $N_{sect}$, sectName, `ANGLE`, $\phi$

| 截面参数            | 参数说明           |
| ------------------- | ------------------ |
| `KEYWORD` = `ANGLE` |                    |
| $\phi$              | 截面欧拉角，角度制 |


## 前置条件

- [截面种类 `TYPE`](/SECTION/GENERAL/TYPE.md) 已定义

---

## 示例

```c
1, sect_RECT, TYPE, RECT
1, sect_RECT, ANGLE, 12
```