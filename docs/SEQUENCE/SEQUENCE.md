# 时程序列 `SEQUENCE`

---

## 输入格式

> /SEQUENCE/<br>
seqName, `MAXVAL`, $factor$<br>
seqName, `DATA`, $time$, $value$<br>
seqName, `DATA`, $time$, $value$<br>
...<br>
\#\#<br>

| 参数            | 说明                                                                         |
| --------------- | ---------------------------------------------------------------------------- |
| seqName         | 序列名称                                                                     |
| $factor$        | 非零的序列最大值，会根据此值对整条序列进行缩放，默认为 1.0                   |
| $time$, $value$ | 时间点值对，可以乱序，时间点默认从 0 开始；如果未指定 0 时刻的值，则默认为 0 |

## 示例

```c
/SEQUENCE/
// sequence 1
seq01, MAX, 1.0
seq01, DATA, 3, 1
seq01, DATA, 4, -1
seq01, DATA, 1, 5
// sequence 2
seq02, DATA, 3, 2
seq02, DATA, 4, -0.05
seq02, DATA, 1, 0.5
##

```