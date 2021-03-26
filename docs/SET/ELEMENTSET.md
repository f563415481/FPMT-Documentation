# 单元集 /ELEMENT_SET/

---

## 输入格式

- 前置条件
  - [单元 `/ELEMENT/`](/ELEMENT/ELEMENT.md) 已定义

> /ELEMENT_SET/<br>
setName, `TYPE`, $P_i$...<br>
\#\#

| 参数    | 说明                                                                |
| ------- | ------------------------------------------------------------------- |
| setName | 单元集名称, 不可重名                                                |
| `TYPE`  | 单元集创建方式，可按枚举方式 `ENUMERATE` 或生成方式 `GENERATE` 进行 |

### 枚举方式 `ENUMERATE`

> $setName$, `ENUMERATE`, $elem_1$, $elem_2$, $elem_3$...

- 直接列出所有单元序号: $elem_1, elem_2, elem_3$...<br>
- 当集内单元较多时，可以针对同一单元集，分多行列出

### 生成方式 `GENERATE`

> $setName$, `GENERATE`, $elem_1$, $elem_2$, $increment$

- 根据初始单元$elem_1$，终止单元$elem_2$，增量$increment$，生成单元集<br>
- 要求$elem_2>elem_1$, 且$(elem_2-elem_1)\mid increment$

---

## 示例

```C++
/ELEMENT/
1, ...
...
5, ...
##

/ELEMENT_SET/
nset1, ENUMERATE, 1, 3, 5
nset1, ENUMERATE, 2, 4
nset2, GENERATE, 1, 5, 2
##
```