# 质点集 /PARTICLE_SET/

---

## 输入格式

- 前置条件
  - [质点 `/PARTICLE/`](/PARTICLE/PARTICLE.md) 已定义

> /PARTICLE_SET/<br>
setName, `TYPE`, $P_i$...<br>
\#\#

| 参数    | 说明                                                                |
| ------- | ------------------------------------------------------------------- |
| setName | 质点集名称, 不可重名                                                |
| `TYPE`  | 质点集创建方式，可按枚举方式 `ENUMERATE` 或生成方式 `GENERATE` 进行 |

### 枚举方式 `ENUMERATE`

> $setName$, `ENUMERATE`, $nd_1$, $nd_2$, $nd_3$...

- 直接列出所有质点序号: $nd_1, nd_2, nd_3$...<br>
- 当集内质点较多时，可以针对同一质点集，分多行列出

### 生成方式 `GENERATE`

> $setName$, `GENERATE`, $nd_1$, $nd_2$, $increment$

- 根据初始质点$nd_1$，终止质点$nd_2$，增量$increment$，生成质点集<br>
- 要求$nd_2>nd_1$, 且$(nd_2-nd_1)\mid increment$

---

## 示例

```C++
/PARTICLE/
1, ...
...
5, ...
##

/PARTICLE_SET/
nset1, ENUMERATE, 1, 3, 5
nset1, ENUMERATE, 2, 4
nset2, GENERATE, 1, 5, 2
##
```