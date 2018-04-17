---
title: go生成代码文档
date: 2018-01-06 12:02:56
---

go doc 工具会从 Go 程序和包文件中提取顶级声明的首行注释以及每个对象的相关注释，并生成相关文档。

## 一般用法

**go doc package **获取包的文档注释，例如：go doc fmt 会显示使用 godoc 生成的 fmt 包的文档注释。
**go doc package/subpackage **获取子包的文档注释，例如：go doc container/list。
**go doc package function **获取某个函数在某个包中的文档注释，例如：go doc fmt Printf 会显示有关 fmt.Printf() 的使用说明。