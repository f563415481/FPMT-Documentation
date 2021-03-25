# 厚度截面 `THICK`

![](/SECTION/PICS/SectionThick.png)

---

## 输入格式

> $N_{sect}$, sectName, `SHAPE`, $t$

| 参数 | 说明 |
| ---- | ---- |
| $t$  | 厚度 |

## 适用单元

- [三角形壳单元 `SHELL_TRI`]()
- [三角形膜单元 `MEMBRANE_TRI`]()

---

## 示例

```c
1, sect_shell, TYPE, THICK
1, sect_shell, SHAPE, 0.01
```