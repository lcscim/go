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
        import "fmt"
        func main() {
        /* 这是我的第一个简单的程序（这句是注释） */
            fmt.Println("Hello, World!")
        }
	- package main 定义了包名。你必须在源文件中非注释的第一行指明这个文件属于哪个包，如：package main。package main表示一个可独立执行的程序，每个 Go 应用程序都包含一个名为 main 的包。

	- import "fmt" 告诉 Go 编译器这个程序需要使用 fmt 包（的函数，或其他元素），fmt 包实现了格式化 IO（输入/输出）的函数。

	- func main() 是程序开始执行的函数。main 函数是每一个可执行程序所必须包含的，一般来说都是在启动后第一个执行的函数（如果有 init() 函数则会先执行该函数）。

	- /*...*/ 是注释，在程序执行时将被忽略。单行注释是最常见的注释形式，你可以在任何地方使用以 // 开头的单行注释。多行注释也叫块注释，均已以 /* 开头，并以 */ 结尾，且不可以嵌套使用，多行注释一般用于包的文档描述或注释成块的代码片段。

	- fmt.Println(...) 可以将字符串输出到控制台，并在最后自动增加换行字符 \n。 
	使用 fmt.Print("hello, world\n") 可以得到相同的结果。 
	Print 和 Println 这两个函数也支持使用变量，如：fmt.Println(arr)。如果没有特别指定，它们会以默认的打印格式将变量 arr 输出到控制台。

	- 当标识符（包括常量、变量、类型、函数名、结构字段等等）以一个大写字母开头，如：Group1，那么使用这种形式的标识符的对象就可以被外部包的代码所使用（客户端程序需要先导入这个包），这被称为导出（像面向对象语言中的 public）；标识符如果以小写字母开头，则对包外是不可见的，但是他们在整个包的内部是可见并且可用的（像面向对象语言中的 protected ）。

- 执行 Go 程序
	代码
	
	打开命令行，并进入程序文件保存的目录中。

	输入命令 go run hello.go 并按回车执行代码。

	如果操作正确你将在屏幕上看到 "Hello World!" 字样的输出。
	
##Go 语言基础语法
- Go 标记

	Go 程序可以由多个标记组成，可以是关键字，标识符，常量，字符串，符号。如以下 GO 语句由 6 个标记组成：

	fmt.Println("Hello, World!")
		6 个标记是(每行一个)：

		1. fmt
		2. .
		3. Println
		4. (
		5. "Hello, World!"
		6. )
- 行分隔符	
	一行代表一个语句结束。每个语句不需要像 C 家族中的其它语言一样以分号 ; 结尾，因为这些工作都将由 Go 编译器自动完成。

	如果你打算将多个语句写在同一行，它们则必须使用 ; 人为区分，但在实际开发中我们并不鼓励这种做法。
- 注释
	// 单行注释
	
	/*
	 Author by 菜鸟教程
	 我是多行注释
	 */
 - 标识符
	标识符用来命名变量、类型等程序实体。一个标识符实际上就是一个或是多个字母(A~Z和a~z)数字(0~9)、下划线_组成的序列，但是第一个字符必须是字母或下划线而不能是数字。

	以下是有效的标识符：
		mahesh   kumar   abc   move_name   a_123
		myname50   _temp   j   a23b9   retVal
	以下是无效的标识符：

		1ab（以数字开头）
		case（Go 语言的关键字）
		a+b（运算符是不允许的）
- 关键字
	下面列举了 Go 代码中会使用到的 25 个关键字或保留字：

		break		default		func	interface	select
		case		defer		go		map			struct
		chan		else		goto	package		switch
		const		fallthrough	if		range		type
		continue	for			import	return		var
	除了以上介绍的这些关键字，Go 语言还有 36 个预定义标识符：

		append	bool	byte	cap		close	complex		complex64	complex128	uint16
		copy	false	float32	float64	imag	int			int8		int16		uint32
		int32	int64	iota	len		make	new			nil			panic		uint64
		print	println	real	recover	string	true		uint		uint8		uintptr
	程序一般由关键字、常量、变量、运算符、类型和函数组成。

	程序中可能会使用到这些分隔符：括号 ()，中括号 [] 和大括号 {}。

	程序中可能会使用到这些标点符号：.、,、;、: 和 …。
- Go 语言的空格
	Go 语言中变量的声明必须使用空格隔开，如：
		var age int;
	语句中适当使用空格能让程序更易阅读。
	无空格：
		fruit=apples+oranges;
	在变量与运算符间加入空格，程序看起来更加美观，如：
		fruit = apples + oranges; 
		
- Go 语言数据类型
##Go 语言数据类型
- Go 语言按类别有以下几种数据类型
	1. 布尔型
		布尔型的值只可以是常量 true 或者 false。一个简单的例子：var b bool = true。
	2. 数字类型
	整型 int 和浮点型 float32、float64，Go 语言支持整型和浮点型数字，并且原生支持复数，其中位的运算采用补码。
	3. 字符串类型:
	字符串就是一串固定长度的字符连接起来的字符序列。Go的字符串是由单个字节连接起来的。Go语言的字符串的字节使用UTF-8编码标识Unicode文本。
	4. 派生类型:
		包括：
		(a) 指针类型（Pointer）
		(b) 数组类型
		(c) 结构化类型(struct)
		(d) Channel 类型
		(e) 函数类型
		(f) 切片类型
		(g) 接口类型（interface）
		(h) Map 类型
- 数字类型
	Go 也有基于架构的类型，例如：int、uint 和 uintptr。

		序号	类型和描述
		1	uint8 		无符号 8 位整型 (0 到 255)
		2	uint16 		无符号 16 位整型 (0 到 65535)
		3	uint32 		无符号 32 位整型 (0 到 4294967295)
		4	uint64 		无符号 64 位整型 (0 到 18446744073709551615)
		5	int8 		有符号 8 位整型 (-128 到 127)
		6	int16 		有符号 16 位整型 (-32768 到 32767)
		7	int32 		有符号 32 位整型 (-2147483648 到 2147483647)
		8	int64 		有符号 64 位整型 (-9223372036854775808 到 9223372036854775807)
	浮点型：

		序号	类型和描述
		1	float32 	IEEE-754 32位浮点型数
		2	float64 	IEEE-754 64位浮点型数
		3	complex64 	32 位实数和虚数
		4	complex128 	64 位实数和虚数
	其他数字类型
	以下列出了其他更多的数字类型：

		序号	类型和描述
		1	byte 	类似 uint8
		2	rune 	类似 int32
		3	uint 	32 或 64 位
		4	int 	与 uint 一样大小
		5	uintptr 无符号整型，用于存放一个指针
##Go 语言变量
Go 语言变量名由字母、数字、下划线组成，其中首个字母不能为数字。

声明变量的一般形式是使用 var 关键字：

	var 变量名 变量类型
- 变量声明
	1. 指定变量类型，声明后若不赋值，使用默认值。

		var v_name v_type
		v_name = value
	2. 根据值自行判定变量类型。

		var v_name = value
	3. 省略var, 注意 :=左侧的变量不应该是已经声明过的，否则会导致编译错误。

		v_name := value

		// 例如
		var a int = 10
		var b = 10
		c := 10
	实例如下：

		package main
		var a = "菜鸟教程"
		var b string = "runoob.com"
		var c bool

		func main(){
			println(a, b, c)
		}
	以上实例执行结果为：

	菜鸟教程 runoob.com false
- 多变量声明
	//类型相同多个变量, 非全局变量
	var vname1, vname2, vname3 type
	vname1, vname2, vname3 = v1, v2, v3
	var vname1, vname2, vname3 = v1, v2, v3 //和python很像,不需要显示声明类型，自动推断
	vname1, vname2, vname3 := v1, v2, v3 //出现在:=左侧的变量不应该是已经被声明过的，否则会导致编译错误
	// 这种因式分解关键字的写法一般用于声明全局变量
	var (
		vname1 v_type1
		vname2 v_type2
	)
	
	实例如下：

		package main
		var x, y int
		var (  // 这种因式分解关键字的写法一般用于声明全局变量
			a int
			b bool
		)
		var c, d int = 1, 2
		var e, f = 123, "hello"
		//这种不带声明格式的只能在函数体中出现
		//g, h := 123, "hello"
		func main(){
			g, h := 123, "hello"
			println(x, y, a, b, c, d, e, f, g, h)
		}
	以上实例执行结果为：

		0 0 0 false 1 2 123 hello 123 hello
		
- 值类型和引用类型
	- 所有像 int、float、bool 和 string 这些基本类型都属于值类型，使用这些类型的变量直接指向存在内存中的值：
	- 当使用等号 = 将一个变量的值赋值给另一个变量时，如：j = i，实际上是在内存中将 i 的值进行了拷贝：
	可以通过 &i 来获取变量 i 的内存地址，例如：0xf840000040（每次的地址都可能不一样）。值类型的变量的值存储在栈中。

	内存地址会根据机器的不同而有所不同，甚至相同的程序在不同的机器上执行后也会有不同的内存地址。因为每台机器可能有不同的存储器布局，并且位置分配也可能不同。

	更复杂的数据通常会需要使用多个字，这些数据一般使用引用类型保存。

	一个引用类型的变量 r1 存储的是 r1 的值所在的内存地址（数字），或内存地址中第一个字所在的位置。
	这个内存地址为称之为指针，这个指针实际上也被存在另外的某一个字中。

	同一个引用类型的指针指向的多个字可以是在连续的内存地址中（内存布局是连续的），这也是计算效率最高的一种存储形式；也可以将这些字分散存放在内存中，每个字都指示了下一个字所在的内存地址。

	当使用赋值语句 r2 = r1 时，只有引用（地址）被复制。

	如果 r1 的值被改变了，那么这个值的所有引用都会指向被修改后的内容，在这个例子中，r2 也会受到影响。
- 简短形式，使用 := 赋值操作符
	我们知道可以在变量的初始化时省略变量的类型而由系统自动推断，声明语句写上 var 关键字其实是显得有些多余了，因此我们可以将它们简写为 a := 50 或 b := false。

	a 和 b 的类型（int 和 bool）将由编译器自动推断。

	这是使用变量的首选形式，但是它只能被用在函数体内，而不可以用于全局变量的声明与赋值。使用操作符 := 可以高效地创建一个新的变量，称之为初始化声明。
- 注意事项
	1. 如果在相同的代码块中，我们不可以再次对于相同名称的变量使用初始化声明，例如：a := 20 就是不被允许的，编译器会提示错误 no new variables on left side of :=，但是 a = 20 是可以的，因为这是给相同的变量赋予一个新的值。
	2. 如果你在定义变量 a 之前使用它，则会得到编译错误 undefined: a。
	3. 如果你声明了一个局部变量却没有在相同的代码块中使用它，同样会得到编译错误，例如下面这个例子当中的变量 a：
		package main
		import "fmt"
		func main() {
		   var a string = "abc"
		   fmt.Println("hello, world")
		}
		尝试编译这段代码将得到错误 a declared and not used。
		全局变量是允许声明但不使用
		
##Go 语言常量
常量是一个简单值的标识符，在程序运行时，不会被修改的量。

常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型。

常量的定义格式：

	const identifier [type] = value
你可以省略类型说明符 [type]，因为编译器可以根据变量的值来推断其类型。

	显式类型定义： const b string = "abc"
	隐式类型定义： const b = "abc"
多个相同类型的声明可以简写为：

	const c_name1, c_name2 = value1, value2
以下实例演示了常量的应用：

	package main
	import "fmt"
	func main() {
	   const LENGTH int = 10
	   const WIDTH int = 5   
	   var area int
	   const a, b, c = 1, false, "str" //多重赋值
	   area = LENGTH * WIDTH
	   fmt.Printf("面积为 : %d", area)
	   println()
	   println(a, b, c)   
	}
	
	运行结果为：

	面积为 : 50
	1 false str
常量还可以用作枚举：
	const (
		Unknown = 0
		Female = 1
		Male = 2
	)
	数字 0、1 和 2 分别代表未知性别、女性和男性。
常量可以用len(), cap(), unsafe.Sizeof()函数计算表达式的值。常量表达式中，函数必须是内置函数，否则编译不过：

	package main
	import "unsafe"
	const (
		a = "abc"
		b = len(a)
		c = unsafe.Sizeof(a)
	)
	func main(){
		println(a, b, c)
	}
以上实例运行结果为：

	abc 3 16
	
	字符串类型在 go 里是个结构, 包含指向底层数组的指针和长度,这两部分每部分都是 8 个字节，所以字符串类型大小为 16 个字节。
- iota，特殊常量，可以认为是一个可以被编译器修改的常量。
	iota 在 const关键字出现时将被重置为 0(const 内部的第一行之前)，const 中每新增一行常量声明将使 iota 计数一次(iota 可理解为 const 语句块中的行索引)。

	iota 可以被用作枚举值：

		const (
			a = iota
			b = iota
			c = iota
		)
	第一个 iota 等于 0，每当 iota 在新的一行被使用时，它的值都会自动加 1；所以 a=0, b=1, c=2 可以简写为如下形式：

		const (
			a = iota
			b
			c
		)
- iota 用法
	package main
	import "fmt"
	func main() {
		const (
				a = iota   //0
				b          //1
				c          //2
				d = "ha"   //独立值，iota += 1
				e          //"ha"   iota += 1
				f = 100    //iota +=1
				g          //100  iota +=1
				h = iota   //7,恢复计数
				i          //8
		)
		fmt.Println(a,b,c,d,e,f,g,h,i)
	}
	以上实例运行结果为：

		0 1 2 ha ha 100 100 7 8