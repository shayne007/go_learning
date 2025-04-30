## 初始化顺序
- 依赖包按“深度优先”的次序进行初始化；
- 每个包内按以“常量 -> 变量 -> init 函数”的顺序进行初始化；
- 包内的多个 init 函数按出现次序进行自动调用。

## 空导入
空导入一个包后，虽然没有调用任何包内的方法，但是包内的静态变量和静态代码块会被执行。

```go
import (
    "database/sql"
    _ "github.com/lib/pq"
)

func main() {
    db, err := sql.Open("postgres", "user=pqgotest dbname=pqgotest sslmode=verify-full")
    if err != nil {
        log.Fatal(err)
    }
    
    age := 21
    rows, err := db.Query("SELECT name FROM users WHERE age = $1", age)
    ...
}
```
empty import "github.com/lib/pq" 会执行init函数

```go
func init() {
    sql.Register("postgres", &Driver{})
}
```