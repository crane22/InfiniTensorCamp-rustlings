# Rust基本语法备忘录

## 输出

### 常用宏

- println! 和 print!

    println!：输出带换行的字符串。

    print!：输出不带换行的字符串。

```rust
println!("Hello, world!");
print!("Hello, world!");
```

- eprintln! 和 eprint!

    eprintln!：向标准错误输出带换行的字符串。

    eprint!：向标准错误输出不带换行的字符串。

```rust
eprintln!("Error: something went wrong!");
eprint!("Error: something went wrong!");
```

- format!

    返回一个格式化后的字符串。

```rust
let s = format!("Hello, {}!", "world");
```

### 格式化输出标记

- {}

    默认格式化输出，要求类型实现 Display trait。

```rust
println!("Hello, {}", "world");
```

- {:?}

    调试格式化输出，要求类型实现 Debug trait。

```rust
println!("Debug output: {:?}", some_variable);
```

- {:#?}

    格式化调试输出，使其更具可读性，特别适用于结构体和其他复杂类型。

```rust
println!("Pretty Debug output: {:#?}", some_variable);
```

- {:x} 和 {:X}

    将整数格式化为小写或大写的十六进制。

```rust
println!("Hex (lowercase): {:x}", 255); // 输出: ff
println!("Hex (uppercase): {:X}", 255); // 输出: FF
```

- {:b}

    将整数格式化为二进制。

```rust
println!("Binary: {:b}", 5); // 输出: 101
```

- {:o}

    将整数格式化为八进制。

```rust
println!("Octal: {:o}", 8); // 输出: 10
```

- {:p}

    格式化输出指针的内存地址。

```rust
let x = 42;
let x_ptr = &x as *const i32;
println!("Pointer address: {:p}", x_ptr);
```

- 对齐和宽度

    :<width>：左对齐，宽度为 width。

    :^width>：中间对齐，宽度为 width。

    :>width>：右对齐，宽度为 width。

```rust
println!("{:<10} | {:^10} | {:>10}", "left", "center", "right");
```

- 填充字符

    使用指定的字符填充空白。

```rust
println!("{:*<10}", "left");    // 输出: left******
println!("{:^*10}", "center");  // 输出: **center**
println!("{:*>10}", "right");   // 输出: *****right
```

- 数值精度

    格式化浮点数时指定小数点后的位数。

```rust
let pi = 3.141592;
println!("Pi is approximately {:.2}", pi); // 输出: Pi is approximately 3.14
```

- 位置参数和命名参数

    - 位置参数

        使用位置参数指定插值的顺序。
```rust
println!("{0}, {1}, {0}", "first", "second"); // 输出: first, second, first
```

- 命名参数

    使用命名参数指定插值。
```rust
println!("{name} is {age} years old.", name = "Alice", age = 30);
```
- 示例总结

```rust
fn main() {
    let x = 42;
    let y = 255;
    let z = 5;
    let name = "Alice";
    let age = 30;
    let pi = 3.141592;
    let point = (1, 2);
    
    println!("Default: {}", name);
    println!("Debug: {:?}", point);
    println!("Pretty Debug: {:#?}", point);
    println!("Hex (lowercase): {:x}", y);
    println!("Hex (uppercase): {:X}", y);
    println!("Binary: {:b}", z);
    println!("Octal: {:o}", y);
    println!("Pointer address: {:p}", &x);
    println!("{:<10} | {:^10} | {:>10}", "left", "center", "right");
    println!("{:*<10}", "left");
    println!("{:*^10}", "center");
    println!("{:*>10}", "right");
    println!("Pi is approximately {:.2}", pi);
    println!("{0}, {1}, {0}", "first", "second");
    println!("{name} is {age} years old.", name = name, age = age);
}
```

    输出结果：

```
Default: Alice
Debug: (1, 2)
Pretty Debug: (
    1,
    2,
)
Hex (lowercase): ff
Hex (uppercase): FF
Binary: 101
Octal: 377
Pointer address: 0x7ffd2bd074c4
left       |   center   |      right
left******
**center**
*****right
Pi is approximately 3.14
first, second, first
Alice is 30 years old.
```