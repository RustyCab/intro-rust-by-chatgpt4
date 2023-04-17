# Chapter 2 Rust基础

在这一部分，我们将讨论Rust的基础知识，包括变量和数据类型、基本运算符以及控制流程。

## 2.1 变量和数据类型

Rust是一种静态类型语言，这意味着变量的类型在编译时就已经确定。Rust具有类型推断功能，通常可以自动推断变量的类型，但在某些情况下，您可能需要显式地指定变量的类型。

### 2.1.1 变量

在Rust中，变量用于存储数据。Rust变量默认是不可变的，这意味着在声明后，您不能更改变量的值。要声明一个可变变量，需要使用mut关键字。例如：

```rust
let x = 5; // 不可变变量
let mut y = 10; // 可变变量
```

要声明变量，我们使用let关键字，后跟变量名称、变量类型（可选）和初始值。

### 2.1.2 数据类型

Rust有许多内置的数据类型，以下是一些常见的数据类型：

1. 整数类型：整数可以是有符号（i）或无符号（u），并具有不同的位大小（例如8、16、32、64）。有符号整数可以表示负值，无符号整数只能表示非负值。例如

    ```rust
    let a: i32 = -42;
    let b: u32 = 42;
    ```

2. 浮点类型：浮点数用于表示实数。Rust有两种浮点类型：单精度（f32）和双精度（f64）。双精度浮点数具有更高的精度和范围，但需要更多的存储空间。例如：

    ```rust
    let pi: f32 = 3.14;
    let e: f64 = 2.71828;
    ```

3. 布尔类型：布尔类型（bool）用于表示逻辑真（true）或假（false）。布尔类型通常在条件语句和逻辑运算中使用。例如：

    ```rust
    let is_true: bool = true;
    let is_false: bool = false;
    ```

4. 字符类型：字符类型（char）表示一个Unicode标量值。Rust的char类型占用4个字节，可以表示大多数Unicode字符。例如：

    ```rust
    let letter: char = 'A';
    let emoji: char = '😃';
    ```

5. 字符串类型：字符串是字符的集合。Rust有两种字符串类型：字符串切片（&str）和可增长的字符串（String）。字符串切片是不可变的，通常用于引用字符串字面量。可增长的字符串可以动态改变大小。例如：

    ```rust
    let static_str: &str = "Hello, World!";
    let mut dynamic_str: String = String::from("Hello, Rust!");
    dynamic_str.push_str(" It's great!");
    ```

6. 数组和切片：数组是具有固定长度的相同类型元素的集合。切片是数组的连续部分，允许您引用数组的一部分，而不需要创建新的数组。例如：
   
    ```rust
    // 定义一个包含5个整数的数组
    let numbers: [i32; 5] = [1, 2, 3, 4, 5];

    // 访问数组中的元素
    let first_number = numbers[0]; // 1
    let second_number = numbers[1]; // 2

    // 定义一个包含前三个元素的切片
    let slice: &[i32] = &numbers[0..3];
    ```

7. 元组：元组是具有固定长度的不同类型元素的集合。元组可以用于将多个值分组为一个复合值。例如：
   
    ```rust
    // 定义一个元组，包含一个字符串、一个整数和一个布尔值
    let person: (&str, i32, bool) = ("Alice", 30, true);

    // 访问元组中的元素
    let name = person.0; // "Alice"
    let age = person.1; // 30
    let is_student = person.2; // true
    ```

8. 自定义类型：除了内置类型，Rust还允许您创建自定义类型，如结构体（struct）和枚举（enum）。结构体用于将多个相关值组织到一个命名类型中，而枚举允许您定义一个类型，该类型可以具有多个变体。例如

    ```rust
    // 定义一个结构体表示一个点
    struct Point {
        x: f64,
        y: f64,
    }

    // 定义一个枚举表示一个颜色
    enum Color {
        Red,
        Green,
        Blue,
    }

    // 创建自定义类型的实例
    let origin = Point { x: 0.0, y: 0.0 };
    let red = Color::Red;
    ```

了解Rust的基本变量和数据类型将使您能够编写更强大和灵活的程序。

## 2.2 基本运算符

Rust支持许多基本运算符，包括算术运算符、比较运算符和逻辑运算符。以下是各类运算符的详细描述：

### 2.2.1 算术运算符

算术运算符用于对数字进行基本的数学运算。

- 加法（+）：将两个数相加。例如：5 + 3 结果为 8。
- 减法（-）：将一个数减去另一个数。例如：5 - 3 结果为 2。
- 乘法（*）：将两个数相乘。例如：5 * 3 结果为 15。
- 除法（/）：将一个数除以另一个数。例如：6 / 3 结果为 2。注意：整数除法会向下取整，例如：7 / 3 结果为 2。
- 取余（%）：求一个数除以另一个数的余数。例如：7 % 3 结果为 1。

### 2.2.2 比较运算符

比较运算符用于比较两个值，返回一个布尔值（true 或 false）。

- 等于（==）：检查两个值是否相等。例如：5 == 3 结果为 false。
- 不等于（!=）：检查两个值是否不相等。例如：5 != 3 结果为 true。
- 小于（<）：检查一个值是否小于另一个值。例如：5 < 3 结果为 false。
- 大于（>）：检查一个值是否大于另一个值。例如：5 > 3 结果为 true。
- 小于等于（<=）：检查一个值是否小于或等于另一个值。例如：5 <= 3 结果为 false。
- 大于等于（>=）：检查一个值是否大于或等于另一个值。例如：5 >= 3 结果为 true。

### 2.2.3 逻辑运算符

逻辑运算符用于对布尔值进行逻辑运算。

- 逻辑与（&&）：仅当两个布尔值都为 true 时，结果为 true。例如：true && false 结果为 false。
- 逻辑或（||）：如果至少有一个布尔值为 true，结果为 true。例如：true || false 结果为 true。
- 逻辑非（!）：对一个布尔值取反。例如：!true 结果为 false。

了解基本运算符将帮助您编写更复杂的表达式和实现更多功能。


## 2.3 控制流程：条件和循环

Rust提供了多种控制流程结构，包括条件语句（if和else）和循环（loop、while和for）。

### 2.3.1 条件语句

if和else关键字用于创建条件语句。例如：

```rust
let number = 5;

if number % 2 == 0 {
    println!("{} is even.", number);
} else {
    println!("{} is odd.", number);
}
```

在这个示例中，我们使用if语句检查一个数字是否为偶数。如果为偶数，输出一条消息；否则，输出另一条消息。您还可以使用else if来添加更多条件：

```rust
let number = 0;

if number > 0 {
    println!("{} is positive.", number);
} else if number < 0 {
    println!("{} is negative.", number);
} else {
    println!("{} is zero.", number);
}
```

### 2.3.2 循环

Rust提供了三种循环结构：loop、while和for。

1. loop：无条件循环，直到使用break关键字退出循环。
   
例如：

```rust
let mut count = 0;

loop {
    count += 1;
    println!("count: {}", count);

    if count >= 5 {
        break;
    }
}
```

2. while：只要条件为真，就会执行循环。

例如：

```rust
let mut count = 0;

while count < 5 {
    count += 1;
    println!("count: {}", count);
}
```

3. for：用于遍历范围、数组、迭代器等

```rust
// 遍历范围
for i in 1..6 {
    println!("Iteration: {}", i);
}

// 遍历数组
let numbers = [1, 2, 3, 4, 5];

for number in numbers.iter() {
    println!("Number: {}", number);
}
```

通过了解Rust的控制流程结构，您可以根据需要编写更复杂和灵活的程序。在接下来的章节中，我们将深入探讨Rust的高级概念和特性。
