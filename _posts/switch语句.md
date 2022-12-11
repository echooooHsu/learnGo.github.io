## switch 语句
```
  func main() {
	// finger := 4
	// fmt.Printf("Finger %d is ", finger)
    switch finger := 8; finger {//分号分离，可以自己指定
    case 1:
      fmt.Println("Thumb")
    case 2:
      fmt.Println("Index")
    case 3:
      fmt.Println("Middle")
    case 4:
      fmt.Println("Ring")
    case 5:
      fmt.Println("Pinky")
    default: // 默认选项
      fmt.Println("incorrect finger number")
    }
}
```

## case 适配多个条件
```
  func main() {
	// finger := 4
	// fmt.Printf("Finger %d is ", finger)
    switch finger := 8; finger {//分号分离，可以自己指定
    case 1, 2, 3:
      fmt.Println("Thumb")
    case 4:
      fmt.Println("Ring")
    case 5:
      fmt.Println("Pinky")
    default: // 默认选项
      fmt.Println("incorrect finger number")
    }
}
```

## case 后续跟着表达式
```
  func main() {
    // finger := 4
    // fmt.Printf("Finger %d is ", finger)
    switch finger := 8; {//逗号必须加
    case finger > 9://case也可以是判断区间范围， case finger > 3 && finger < 6:
      fmt.Println("Thumb")
    case finger < 7:
      fmt.Println("Index")
    // case 3:
    // 	fmt.Println("Middle")
    // case 4:
    // 	fmt.Println("Ring")
    // case 5:
    // 	fmt.Println("Pinky")
    default: // 默认选项
      fmt.Println("incorrect finger number")
    }
  }
```
## Fallthrough
这个关键字会执行当前case后面的所有除去default的case 不管后面的case条件是不是true
但是fall through不能用在最后一个case里面
```
  func main() {
    // finger := 4
    // fmt.Printf("Finger %d is ", finger)
    switch finger := 8; {
    case finger > 9:
      fmt.Println("Thumb")
    case finger > 7:
      fmt.Println("Index")
      fallthrough
    case finger > 10:
      fmt.Println("Ring")
    // case 3:
    // 	fmt.Println("Middle")
    // case 4:
    // 	fmt.Println("Ring")
    // case 5:
    // 	fmt.Println("Pinky")
    default: // 默认选项
      fmt.Println("incorrect finger number")
    }
  }
```

## break 
break 语句可以将switch语句提前结束，如下所示
```
  func main() {
    switch num := -5; {
    case num < 50:
      if num < 0 {
        break
      }
      fmt.Printf("%d is lesser than 50\n", num)
      fallthrough
    case num < 100:
      fmt.Printf("%d is lesser than 100\n", num)
      fallthrough
    case num < 200:
      fmt.Printf("%d is lesser than 200\n", num)
      fallthrough
    default:
      fmt.Printf("is default")
    }
  }
```
使用break在for loop中中断switch
```
  func main() {
  randloop:
    for {
      switch i := rand.Intn(100); {
      case i%2 == 0:
        fmt.Printf("Generate even num %d", i)
        break randloop
      }
    }
  }
```
如果是只是用break那么for不会被跳出
```
  func main() {
    for {
      switch i := rand.Intn(100); {
      case i%2 == 0:
        fmt.Printf("Generate even num %d", i)
        break
      }
    }
  }
```
运行结果：
<img width="939" alt="image" src="https://user-images.githubusercontent.com/42528183/206897286-75c196bf-062c-4f63-abdc-15464c28faec.png">

