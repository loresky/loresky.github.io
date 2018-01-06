---
title: go标签与goto
date: 2018-01-06 16:50:02
categories: golang
tags: golang
---

for、switch 或 select 语句都可以配合标签（label）形式的标识符使用，即某一行第一个以冒号（:）结尾的单词（gofmt 会将后续代码自动移至下一行）。
**标签的名称是大小写敏感的，为了提升可读性，一般建议使用全部大写字母） **
``` go
package main

import "fmt"

func main() {

LABEL1:
    for i := 0; i <= 5; i++ {
        for j := 0; j <= 5; j++ {
            if j == 4 {
                continue LABEL1
            }
            fmt.Printf("i is: %d, and j is: %d\n", i, j)
        }
    }

}
```
``` go 
package main

func main() {
    i:=0
    HERE:
        print(i)
        i++
        if i==5 {
            return
        }
        goto HERE
}
```