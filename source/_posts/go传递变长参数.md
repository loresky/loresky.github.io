---
title: go传递变长参数
date: 2018-01-06 18:45:46
categories: golang
tags: golang
---

如果函数的最后一个参数是采用 ...type 的形式，那么这个函数就可以处理一个变长的参数，这个长度可以为 0，这样的函数称为变参函数。
`func myFunc(a, b, arg ...int) {}`
示例函数和调用：
``` go
func Greeting(prefix string, who ...string)
Greeting("hello:", "Joe", "Anna", "Eileen")
```
在 Greeting 函数中，变量 who 的值为 []string{"Joe", "Anna", "Eileen"}。
如果参数被存储在一个数组 arr 中，则可以通过 arr... 的形式来传递参数调用变参函数。
1. 使用结构
定义一个结构类型，假设它叫 Options，用以存储所有可能的参数：
``` go
  type Options struct {
      par1 type1,
      par2 type2,
      ...
  }
```
函数 F1 可以使用正常的参数 a 和 b，以及一个没有任何初始化的 Options 结构： F1(a, b, Options {})。如果需要对选项进行初始化，则可以使用 F1(a, b, Options {par1:val1, par2:val2})。
2. 使用空接口
如果一个变长参数的类型没有被指定，则可以使用默认的空接口 interface{}，这样就可以接受任何类型的参数。该方案不仅可以用于长度未知的参数，还可以用于任何不确定类型的参数。一般而言我们会使用一个 for-range 循环以及 switch 结构对每个参数的类型进行判断：
``` go 
  func typecheck(..,..,values … interface{}) {
      for _, value := range values {
          switch v := value.(type) {
              case int: …
              case float: …
              case string: …
              case bool: …
              default: …
          }
      }
  }
  ```