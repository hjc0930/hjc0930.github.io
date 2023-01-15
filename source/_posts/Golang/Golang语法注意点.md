编写一个简单的Golang程序

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello Go")
}

```

注意点：

- Golang中每行代码结尾可以加分号也可以不加

- 函数的`{`必须和函数名在同一行，否则报错

- import语法不同的写法：
```go
import "fmt"
import "time"

import (
  "fmt"
  "time"
)
```

## 声明变量的四种方式

```go
package main

import "fmt"

func main() {
  // 声明变量的四种方式

  // 方法一 声明一个变量 指定数据类型
  var a int
  fmt.Println(a)

  // 方法二 声明一个变量 初始化一个值
  var b int = 100
  fmt.Println(b)

  // 方法三：声明一个变量，不指定数据类型(Go可以自动推导类型)
  var c = 100
  fmt.Println(c)

  // 方法四：省去var关键字 直接自动匹配(推荐)
  // := 声明的方式只能够在函数体内使用
  d := 100

  fmt.Println(d)
}
```