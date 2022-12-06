# 包
包 go 源码文件的集合(文件夹) 方便于文档管理

## 可导入函数
一个包中的函数如果对其他包可见她需要配置成大写开头 约定俗成的

## init 函数
go中的每个包都可以有一个init 函数，该函数没有参数和返回类型
```
  func init() {
  }
```
可以在init函数里面完成项目初始化或者是程序正确性

## 初始包的先后顺序
首先包级别的变量优先先初始化
然后是init函数 一个包可以有多个init函数，一个文件或者多个文件中

如果一个包导入了其他包中的函数，这个被导入的包会先被初始化
一个包只会被初始化一次.

在～/Documents/learnpackage下创建一个simpleinsterest文件编写一个simpleinterst.go，输入以下内容
```
  package simpleinterest

  import (
    "fmt"
  )

  func init() {
    fmt.Println("Simple interest package initialized!")
  }

  func Calculate(p float64, r float64, t float64) float64 {
    interest := p * (r / 100) * t
    return interest
  }
```

main.go中输入以下内容
```
  package main

  import (
    "fmt"
    "learnpackage/simpleinterest"
    "log"
  )

  var p, r, t = 500.0, 10.0, 1.0 //包级别的变量

  func init() {
    println("Main package initialized")
    if p < 0 {
      log.Fatal("Principal is less than zero")
    }
    if r < 0 {
      log.Fatal("Rate of interest is less than zero")
    }
    if t < 0 {
      log.Fatal("Duration is less than zero")
    }
  }

  func main() {
    fmt.Println("Simple interest calculation")
    si := simpleinterest.Calculate(p, r, t)
    fmt.Println("Simple interst is", si)
  }

```
输入如下：
```
  Simple interest package initialized! //被导入包
  Main package initialized
  Simple interest calculation
  Simple interst is 50
```
把p的值改成负数，程序会直接在init终止。输出如下：
```
  Simple interest package initialized!
  Main package initialized
  2022/12/06 09:26:50 Principal is less than zero
```

导入包但是在在文件中不使用是非法的。这是因为这会加长加载时间
但是我们可以用_符号来代替导入防止这种非法，因为
`var _ = simpleinterest.Calculate`

假如我们只需要导入某个包，而不需要使用它。那么我们可以在import中这么写
```
  import (
    _ "learnpackage/simpleinterest" //这样就不会报错了
    "log"
  )
```
