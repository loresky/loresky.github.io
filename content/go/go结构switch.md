---
title: go结构switch
date: 2018-01-06 15:48:00
---

### Go 语言中的 switch 结构使用上更加灵活。它接受任意形式的表达式：
``` go
switch var1 {
    case val1:
        ...
    case val2:
        ...
    default:
        ...
}
```
### 如果执行完每个分支的代码后，还希望继续执行后续分支的代码，可以使用 fallthrough 关键字来达到目的
``` go
switch i {
    case 0: fallthrough
    case 1:
        f() // 当 i == 0 时函数也会被调用
}
```
## switch 语句的第二种形式是不提供任何被判断的值（实际上默认为判断是否为 true）
``` go
package main

import "fmt"

func main() {
    var num1 int = 7
    switch {
        case num1 < 0:
            fmt.Println("Number is negative")
        case num1 > 0 && num1 < 10:
            fmt.Println("Number is between 0 and 10")
        default:
            fmt.Println("Number is 10 or greater")
    }
}
//Number is between 0 and 10
```
##  switch 语句的第三种形式是包含一个初始化语句：
``` go
switch result := calculate(); {
    case result < 0:
        ...
    case result > 0:
        ...
    default:
        // 0
}
```