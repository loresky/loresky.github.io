---
title: go多返回值函数的错误
date: 2018-01-06 15:34:47
---

``` go
anInt, _ = strconv.Atoi(origStr)
```
**如果 origStr 不能被转换为整数，anInt 的值会变成 0 而 _ 无视了错误，程序会继续运行。**
``` go
package main

import (
    "fmt"
    "strconv"
)

func main() {
    var orig string = "ABC"
    // var an int
    var newS string
    // var err error

    fmt.Printf("The size of ints is: %d\n", strconv.IntSize)      
    // anInt, err = strconv.Atoi(origStr)
    an, err := strconv.Atoi(orig)
    if err != nil {
        fmt.Printf("orig %s is not an integer - exiting with error\n", orig)
        return
    } 
    // 未发生错误，继续执行：
    fmt.Printf("The integer is %d\n", an)
    an = an + 5
    newS = strconv.Itoa(an)
    fmt.Printf("The new string is: %s\n", newS)
}
```