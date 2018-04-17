---
title: go结构for
date: 2018-01-06 16:26:28
---
## 1. 基于计数器的迭代
`for 初始化语句; 条件语句; 修饰语句 {}`
``` go
package main

import "fmt"

func main() {
    for i := 0; i < 5; i++ {
        fmt.Printf("This is the %d iteration\n", i)
    }
}
```
循环中同时使用多个计数器：
### **for i, j := 0, N; i < j; i, j = i+1, j-1 {} **

## 2. 基于条件判断的迭代
for 结构的第二种形式是没有头部的条件判断迭代（类似其它语言中的 while 循环），基本形式为：for 条件语句 {}。
您也可以认为这是没有初始化语句和修饰语句的 for 结构，因此 ;; 便是多余的了。
``` go
package main

import "fmt"

func main() {
    var i int = 5

    for i >= 0 {
        i = i - 1
        fmt.Printf("The variable i is now: %d\n", i)
    }
}
输出：
The variable i is now: 4
The variable i is now: 3
The variable i is now: 2
The variable i is now: 1
The variable i is now: 0
The variable i is now: -1
```

## 3. for-range 结构
``` go
for pos, char := range str {
...
}
 str := "Go is a beautiful language!"
    fmt.Printf("The length of str is: %d\n", len(str))
    for pos, char := range str {
        fmt.Printf("Character on position %d is: %c \n", pos, char)
    }
```