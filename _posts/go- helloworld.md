# do hello world
- 创建一个文件夹`mkdir learngo`
- 在`learngo` 目录下使用`go mod init learngo` 得到`go.mod`文件
  如下图所示：  
  <img width="148" alt="image" src="https://user-images.githubusercontent.com/42528183/205439960-db265d7e-9bbd-47f7-abc0-89288c6899cf.png">
- 在`learngo`文件夹下创建`main.go`文件，输入以下内容：  
  ```
    package main # 所有.go文件的开头都应该有这句package name main函数总在main包里面

    import "fmt" # 导入fmt包，fmt主要是把文本转换成标准输出

    func main() { # func表示函数的开始，程序都从main入口 包名 函数名()是调用某个包中函数的语法。
          fmt.Println("hello world")
    }
  ```
- 执行`go install`命令
- 执行`~/go/bin/learngo`命令输出hello world
- 最好是将go path 通过`export PATH=$PATH:~/go/bin`追加到系统变量中，就可以直接通过运行`learngo`运行命令。
- 另外一种运行go 程序的方式是使用`go build`命令。`go build` 和 `go install`的区别在于前者不会将二进制文件拷贝至`~/go/bin/`,而是直接将二进制文件创建在
  `go build`命令所在文件夹。
  ```
    xusu@xusudeMacBook-Pro learngo % go build
    xusu@xusudeMacBook-Pro learngo % ./learngo # 执行命令
    hello world
  ```
- 程序运行的第三种方式`go run`命令, 这个和前两个命令的区别在于`go run`需要`.go`文件作为参数。它不是将程序编译并安装到当前目录，而是将文件编译到临时位置并从该位置运行文件。可以通过指定参数--work来看临时位置是什么。
  ```
    xusu@xusudeMacBook-Pro learngo % go run main.go 
    hello world
    
    go run --work main.go
  ```
  `go install`会比较好，可以在任何位置运行程序，因为它将所有程序编译到标准 `~/go/bin/`路径。
  
