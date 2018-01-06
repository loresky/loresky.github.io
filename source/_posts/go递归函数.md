---
title: go递归函数
date: 2018-01-06 20:08:49
categories: golang
tags: golang
---
### 当一个函数在其函数体内调用自身，则称之为递归。最经典的例子便是计算斐波那契数列，即每个数均为前两个数之和
1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89
``` go
package main

import "fmt"

func main() {
    result := 0
    for i := 0; i <= 10; i++ {
        result = fibonacci(i)
        fmt.Printf("fibonacci(%d) is: %d\n", i, result)
    }
}

func fibonacci(n int) (res int) {
    if n <= 1 {
        res = 1
    } else {
        res = fibonacci(n-1) + fibonacci(n-2)
    }
    return
}
//输出：
fibonacci(0) is: 1
fibonacci(1) is: 1
fibonacci(2) is: 2
fibonacci(3) is: 3
fibonacci(4) is: 5
fibonacci(5) is: 8
fibonacci(6) is: 13
fibonacci(7) is: 21
fibonacci(8) is: 34
fibonacci(9) is: 55
fibonacci(10) is: 89
```