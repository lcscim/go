#

#11.21
##Go 语言结构
- Go 语言的基础组成有以下几个部分：

    包声明
    引入包
    函数
    变量
    语句 & 表达式
    注释

    示例：
        package main    
        #第一行代码 package main 定义了包名。你必须在源文件中非注释的第一行指明这个文件属于哪个包，如：package main。package main表示一个可独立执行的程序，每个 Go 应用程序都包含一个名为 main 的包。
        import "fmt"
        #告诉 Go 编译器这个程序需要使用 fmt 包（的函数，或其他元素），fmt 包实现了格式化 IO（输入/输出）的函数。
        func main() {
        /* 这是我的第一个简单的程序（这句是注释） */
            fmt.Println("Hello, World!")
        }