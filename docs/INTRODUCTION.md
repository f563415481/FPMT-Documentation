# 总说明

---

## 字符编码

字符编码统一使用 `UTF-8`

?> 建议：请尽可能减少中文使用

## 注释

注释以 `//` 开头，除注释外，不支持中文字符

```c
// this is a comment line
```

## 命令读取

FPMT文件根据命令关键词出现的顺序从上至下读取，不同建模命令按照关键词 `/KEYWORD/` 与完结符号`##` 进行分块

?> 注意：不同建模命令各自的前置条件

```c
// section for defining particles
/PARTICLE/
...
...
##
// section for defining elements
/ELEMENT/
...
...
##
```

## 命名规范

所有英文字符均不区分大小写,所有自定义名称，必须以字母开头

?> 建议：关键字使用大写字母，用户自定义名称使用小写字母；

```c
/MATERIAL/
1, material01, TYPE, LE     // 'material01' - material name (lower case)
1, material01, DENS, 7850   // 'DENS' - keyword (upper case)
##
```

## 量纲

- 所有单位采用无量纲，用户需自行统一量纲

?> 建议：采用国际单位制
