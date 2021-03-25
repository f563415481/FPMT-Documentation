| Element Type | TYPE   | SUBTYPE | D1   | D2    | D3    | D4    | D5   | D6   |

| ------------ | ------ | ------- | ---- | ----- | ----- | ----- | ---- | ---- |

| Combin       | `SPRG` | `AXLK`  | K    | -     | -     | -     | -    | -    |

| Combin       | `SPRG` | `CUPK`  | K    | Axisx | Axisy | Axisz |      |      |

| Combin       | `SPRG` | `SPDP`  | Kx   | Ky    | Kz    | Cx    | Cy   | Cz   |



---

# **示例**

```c
/REAL_CONSTANT/
1, prestress_cable_1, PRES, SIG,   6e4
2, prestress_cable_2, PRES, FN,    8e5
3, prestress_cable_3, PRES, L0,    3.0
4, prestress_mem_1,   PRES, SIG,   2e7
5, prestress_mem_2,   PRES, PROJ,  2e7, 2e7, 1.0, 0.0, 0.0, 0.0, 1.0, 0.0 
```