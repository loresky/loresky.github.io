---
title: go追踪和defer
date: 2018-01-06 19:04:21
---

**关键字 defer 允许我们推迟到函数返回之前（或任意位置执行 return 语句之后）一刻才执行某个语句或函数（为什么要在返回之后才执行这些语句？因为 return 语句同样可以包含一些操作，而不是单纯地返回某个值）。
关键字 defer 的用法类似于面向对象编程语言 Java 和 C# 的 finally 语句块，它一般用于释放某些已分配的资源。**

``` go
package main
import "fmt"

func main() {
    function1()
}

func function1() {
    fmt.Printf("In function1 at the top\n")
    defer function2()
    fmt.Printf("In function1 at the bottom!\n")
}

func function2() {
    fmt.Printf("function2: Deferred until the end of the calling function!")
}
//输出：
In Function1 at the top
In Function1 at the bottom!
Function2: Deferred until the end of the calling function!
//去掉输出:
In function1 at the top
function2: Deferred until the end of the calling function!
In function1 at the bottom!
```
当有多个 defer 行为被注册时，它们会以逆序执行
``` go
func f() {
    for i := 0; i < 5; i++ {
        defer fmt.Printf(“%d “, i)
    }
}
//输出：
4 3 2 1 0
```

###使用 defer 语句实现代码追踪
``` go 
package main

import "fmt"

func trace(s string)   { fmt.Println("entering:", s) }
func untrace(s string) { fmt.Println("leaving:", s) }

func a() {
    trace("a")
    defer untrace("a")
    fmt.Println("in a")
}
func b() {
    trace("b")
    defer untrace("b")
    fmt.Println("in b")
    a()
}
func main() {
    b()
}
//输出：
entering: b
in b
entering: a
win a
leaving: a
leaving: b
```
上面的代码还可以修改为更加简便的版本
``` go
package main

import "fmt"

func trace(s string) string {
    fmt.Println("entering:", s)
    return s
}

func un(s string) {
    fmt.Println("leaving:", s)
}

func a() {
    defer un(trace("a"))
    fmt.Println("in a")
}

func b() {
    defer un(trace("b"))
    fmt.Println("in b")
    a()
}

func main() {
    b()
}
```
**defer un(trace("a")) ** 先执行**trace("a") ** 然后进入** fmt.Println("in b") ** 在到defer

###使用 defer 语句来记录函数的参数与返回值
``` go
package main

import (
    "io"
    "log"
)

func func1(s string) (n int, err error) {
    defer func() {
        log.Printf("func1(%q) = %d, %v", s, n, err)
    }()
    return 7, io.EOF
}

func main() {
    func1("Go")
}
//输出：
Output: 2011/10/04 10:46:11 func1(“Go”) = 7, EOF
```