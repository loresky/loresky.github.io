---
title: go常量、变量、枚举
date: 2018-01-06 12:38:30
categories: golang
tags: golang
---

# 常量
### 1. 常量使用关键字 const 定义，用于存储不会改变的数据。
### 2. 存储在常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型。
### 3. 在 Go 语言中，你可以省略类型说明符 [type]，因为编译器可以根据变量的值来推断其类型。
``` go
* 显式类型定义： const b string = "abc"
* 隐式类型定义： const b = "abc"
```

**常量还可以用作枚举：**
``` go
const (
    Unknown = 0
    Female = 1
    Male = 2
)
```

# 枚举
#### 第一个 iota 等于 0，每当 iota 在新的一行被使用时，它的值都会自动加 1；所以 a=0, b=1, c=2 可以简写为如下形式：
``` go
const (
    a = iota
    b
    c
)
```
#### 一周中每天的名称
``` go
const (
    Sunday = iota
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
)
```
#### 使用某个类型作为枚举常量的类型：
``` go
type Color int

const (
    RED Color = iota // 0
    ORANGE // 1
    YELLOW // 2
    GREEN // ..
    BLUE
    INDIGO
    VIOLET // 6
)
```

# 变量
``` go
var a = 15
var b = false
var str = "Go says hello to the world!"
//或：
var (
    a = 15
    b = false
    str = "Go says hello to the world!"
    numShips = 50
    city string
)
```