# 模式匹配

## match 匹配

Rust **不支持 switch 语法**，有一个类似的替代方案就是通过 match。

首先写出`match` 通用形式：

```rust
#![allow(unused)]
fn main() {
match target {
    模式1 => 表达式1,
    模式2 => {
        语句1;
        语句2;
        表达式2
    },
    _ => 表达式3
}
}

```

该形式清晰的说明了何为模式，**何为模式匹配：将模式与 `target` 进行匹配，即为模式匹配**，而模式匹配不仅仅局限于 `match`

match必知：

- `match` 的匹配必须要穷举出所有可能，因此这里用 `_` 来代表未列出的所有可能性
- `match` 的每一个分支都必须是一个表达式，且所有分支的表达式最终返回值的类型必须相同
- **X | Y**，类似逻辑运算符 `或`，代表该分支可以匹配 `X` 也可以匹配 `Y`，只要满足一个即可

  


先看一个例子：

```rust
enum Direction {
    East,
    West,
    North,
    South,
}

fn main() {
    let dire = Direction::South;
    match dire {
        Direction::East => println!("East"),
        Direction::North | Direction::South => {
            println!("South or North");
        },
        _ => println!("West"),
    };
}
```

Rust 对 match 的要求是，所有情况要做到完整的、无遗漏的匹配，若漏掉了某些情况，无法编译通过。这个特性叫 **exhaustive**，意味着无遗漏的、穷尽的、全面的。但假如上述 match 表达式漏掉了 Direct::North 的情况，并不会影响编译，因为最后有一个默认情况 “_”下划线，它的含义是**“已经列出来的情况之外的其他情况”**，类似 switch 中的 default。



再来一个复杂一点的：

```rust

#[allow(dead_code)]
// 枚举类型 
enum Direction {
	East,
	West,
	North,
	South,
}
#[allow(dead_code)]
#[derive(Debug)]
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter,
}
#[allow(dead_code)]
fn value_in_cents(coin:Coin) -> u8 {
	match coin {
		Coin::Penny =>  {
            println!("Lucky penny!");
            1
        },
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
	}
}

fn main() {

	let dire = Direction::South;
	match dire {
		Direction::South => println!("South"),
		_=>println!("West"),
	}

    let penny = Coin::Penny;
	println!("penny {:?}",penny);
	
	println!("{:?}",value_in_cents(penny));
	dbg!(value_in_cents(penny));
}

```

#### 使用 match 表达式赋值

还有一点很重要，`match` 本身也是一个表达式，因此可以用它来赋值：

```
#[allow(dead_code)]
enum IpAddr {
	Ipv4,
	Ipv6,
}

fn main(){
	let ip1 = IpAddr::Ipv6;
	let ip_str = match ip1 {
		IpAddr::Ipv4 => "127.0.0.1",
		_ =>"::1",
	};

	println!("{}", ip_str);
}
```

因为这里匹配到 `_` 分支，所以将 `"::1"` 赋值给了 `ip_str`。

#### 模式绑定

模式匹配的另外一个重要功能是从模式中取出绑定的值，用上面的例子改一改实现：

```
#[allow(dead_code)]
#[derive(Debug)]
// 枚举类型 
enum Direction {
	East,
	West,
	North,
	South,
}
#[derive(Debug)]
#[allow(dead_code)]
enum UsState {
    Alabama, 
    Alaska,
    // --snip--
}
#[allow(dead_code)]
#[derive(Debug)]
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),  
}
fn value_in_cents(coin:Coin) -> u8 {
	match coin {
		Coin::Penny =>  {
            println!("Lucky penny!");
            1
        },
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter(state) => {    // 绑定值
            println!("State quarter from {:?}!", state);  // 使用值
            25
        }, 
	}
}
fn main() {

	let dire = Direction::South;
	match dire {
		Direction::South => println!("South"),
		_=>println!("West"),

	}

	let penny = Coin::Quarter(UsState::Alabama);
	println!("penny {:?}",penny);
	
	println!("{:?}",value_in_cents(penny));
	//dbg!(value_in_cents(penny));
}

```

#### match guards

**匹配守卫** 听起来挺酷炫，其实就是在匹配的时候加入判断，如 if 条件判断。

```rust
#[allow(dead_code)]
enum MyInt {
    Value(i8),
    Uvalue(u8)
}



fn main() {
	let x = MyInt::Value(10);
	    match x {
	    MyInt::Value(i) if i > 5 => println!("{} greater than 5",i),
	    _ => println!("smaller than 5 or not signed Integer"),
	   };
}
```



```rust
enum Action {
    Say(String),
    MoveTo(i32, i32),
    ChangeColorRGB(u16, u16, u16),
}

fn main() {
    let actions = [
        Action::Say("Hello Rust".to_string()),
        Action::MoveTo(1,2),
        Action::ChangeColorRGB(255,255,0),
    ];
    for action in actions {
        match action {
            Action::Say(s) => {
                println!("{}", s);
            },
            Action::MoveTo(x, y) => {
                println!("point from (0, 0) move to ({}, {})", x, y);
            },
            Action::ChangeColorRGB(r, g, _) => {
                println!("change color into '(r:{}, g:{}, b:0)', 'b' has been ignored",
                    r, g,
                );
            }
        }
    }
}

```

#### ref 和 mut

若我们要绑定的是被匹配对象的引用，可以使用 ref 关键字。

*关于取引用，我们已经有了 取引用符号 &，为啥还需要 ref ？或者说 & 和 ref 的区别是什么？*

ref 是模式的一部分，它只能出现在**赋值号（=）的左边**，而 & 是表达式的一部分，只能出现在**赋值号的右边**。

```rust
#[allow(dead_code)]

fn print_type_of<T>(_: T) {
    println!("{}", std::any::type_name::<T>())
}

fn main() {

    let x = 12;
	match x {
	     r => print_type_of(r),    // 此时 r 类型是 i32
	}

	match x {
	    ref r =>print_type_of(r),  // 此时 r 类型是 &i32
	}
}
```

关于 mut，主要想讨论的是 mut 和 &mut 的区别。对于 mut，它代表变量本身是可变的，即可以重新绑定到另一个变量上去；而 &mut，修饰的是指针，代表该指针对于所指向的内存有修改能力，如可以通过 *x = 1; 改变内存中的值。

#### 穷尽匹配

在文章的开头，我们简单总结过 `match` 的匹配必须穷尽所有情况，下面来举例说明，例如：

```rust
enum Direction {
    East,
    West,
    North,
    South,
}

fn main() {
    let dire = Direction::South;
    match dire {
        Direction::East => println!("East"),
        Direction::North | Direction::South => {
            println!("South or North");
        },
    };
}

```

我们没有处理 `Direction::West` 的情况，因此会报错（上面已提供正确编写答案）

#### `_` 通配符

当我们不想在匹配时列出所有值的时候，可以使用 Rust 提供的一个特殊**模式**，例如，`u8` 可以拥有 0 到 255 的有效的值，但是我们只关心 `1、3、5 和 7` 这几个值，不想列出其它的 `0、2、4、6、8、9 一直到 255` 的值。那么, 我们不必一个一个列出所有值, 因为可以使用特殊的模式 `_` 替代：

```rust

#![allow(unused)]
fn main() {
let some_u8_value = 0u8;
match some_u8_value {
    1 => println!("one"),
    3 => println!("three"),
    5 => println!("five"),
    7 => println!("seven"),
    _ => (),
}
}

```

**除了`_`通配符，用一个变量来承载其他情况也是可以的。**

```rust
#[derive(Debug)]
enum Direction {
    East,
    West,
    North,
    South,
}

fn main() {
    let dire = Direction::South;
    match dire {
        Direction::East => println!("East"),
        other => println!("other direction: {:?}", other),
    };
}

```

执行结果如下：

```shell
(base) PS E:\demo> rustc hello.rs
(base) PS E:\demo> ./hello
other direction: South
```

然而，在某些场景下，我们其实只关心**某一个值是否存在**，此时 `match` 就显得过于啰嗦。

## if let 匹配

有时会遇到只有一个模式的值需要被处理，其它值直接忽略的场景，如果用 `match` 来处理就要写成下面这样：

```rust

    let v = Some(3u8);
    match v {
        Some(3) => println!("three"),
        _ => (),
    }
```

我们只想要对 `Some(3)` 模式进行匹配, 不想处理任何其他 `Some<u8>` 值或 `None` 值。但是为了满足 `match` 表达式（穷尽性）的要求，写代码时必须在处理完这唯一的成员后加上 `_ => ()`，这样会增加不少无用的代码。

俗话说“杀鸡焉用牛刀”，我们完全可以用 `if let` 的方式来实现：

```rust
if let Some(3) = v {
    println!("three");
}
```

这两种匹配对于新手来说，可能有些难以抉择，但是只要记住一点就好：**当你只要匹配一个条件，且忽略其他条件时就用 `if let` ，否则都用 `match`**。

完整代码：

```rust
fn main () {
	let v = Some(3u8);
	match v {
        Some(3u8) => println!("three"),
        _ => (),
    }

	if let Some(6) = v {
		println!("three");
	}
}
```



## matches!宏

Rust 标准库中提供了一个非常实用的宏：`matches!`，它可以将一个表达式跟模式进行匹配，然后返回匹配的结果 `true` or `false`。

例如，有一个动态数组，里面存有以下枚举：

```rust
 #[derive(Debug)]
enum MyEnum {
	Foo,
	Bar,
}

fn main () {
	let v = vec![MyEnum::Foo,MyEnum::Bar,MyEnum::Foo];
	let p = v.iter().filter(|x| matches!(x, MyEnum::Foo));
	println!("{:?}",v);
	println!("{:?}",p);

	let foo = 'a';
	assert!(matches!(foo, 'A'..='Z' | 'a'..='z'));

	let bar = Some(12);
	assert!(matches!(bar, Some(x) if x > 2));

}
```

其实就是我们常用到的`match`表达式，只是在使用`matches!`宏表达起来更简洁。

我们将上面的列子单拆出来说下，大家可能就一目了然了。

**例子1**

如果我们想表达这段匹配的模式，

```
'A'..='Z' | 'a'..='z' | '0'..='9'
```

分别使用`match` 和 `matches!`该怎么描述呢? 

代码如下：

```rust

fn main () {
	let foo = 'f';
	println!("{}",get_foo(foo));

	println!("{}",matches!(foo, 'A'..='Z' | 'a'..='z'));
}

fn get_foo(c:char) ->bool {
	match c {
		'A'..='Z' | 'a'..='z' =>true,
		_=>false
	}
}
```

`get_foo`匹配到其中一个模式后，返回`true`,未匹配到返回`fasle`

答案：

```shell
true
true
```

**例子2**

匹配到**`Some(x) if x > 2`**的值代码如下，其中这里的匹配模式:**匹配守卫** **if x > 2**

- **`Some(x)`**是**`pattern`**匹配模式

- **`if x > 2`**` 表示`**`guard`**的匹配守卫(**`match guard`**)

- 关于匹配守卫的详细请参考链接：

  https://doc.rust-lang.org/stable/book/ch18-03-pattern-syntax.html#extra-conditionals-with-match-guards

```rust

fn main () {
	let bar = Some(12);
	println!("{}",get_bar(bar));


	println!("{}",matches!(bar, Some(x) if x>2));
}

fn get_bar(o:Option<usize>) ->bool {
	match o {
		Some(x) if x>2  =>true,
		_=>false
	}
}
```

这里的**`get_bar `****匹配**其中一个模式后，返回`true`,未匹配到返回`fasle`

好了，我们看了上面两个例子后，大概就能明白`matches!`宏的大致使用了。

> ```
> matches!(expr,pattern)
> ```

- **`expr`**:是指条件判断的入参
- **`pattern`** 是期待为`true`的匹配模式。



**演进**

知道了`matches!`宏的原理，那我们自己推导一个类似该`matches!`宏的自定义`matche_map`函数。

接收一个闭包，返回bool类型函数，代码大致如下：

```rust

fn main () {
	let bar = match_map(|x| {
		if let Some(x) = x {return x >2;}
		false
	});

	println!("{}",bar(Some(4))); // true 

}

pub fn match_map<I,F>(f:F) -> impl Fn(I) ->bool where F:Fn(I) ->bool
{
	move |input: I| f(input)
}
```

## **matches! 实现**

我们来看下`matches!`的实现

```
#[macro_export]
macro_rules! matches {
    ($expression:expr, $($pattern:tt)+$(if $guard:expr)?) => {
        match $expression {
            $($pattern)| + $(if $guard)? => true,
            _ => false
        }
    }
}
```

源码来源：[Rust每周一库: matches!](https://colobu.com/2019/10/22/rust-lib-per-week-matches/) ,感兴趣可以查看详情。

- match匹配`expression`表达式
- `pattern`为匹配模式
- `guard`用`？`表示可能存在
- match 匹配上的模式返回`true`,其他返回`false`

## 变量遮蔽

无论是 `match` 还是 `if let`，这里都是一个新的代码块，而且这里的绑定相当于新变量，如果你使用同名变量，会发生变量遮蔽:

```
fn main() {
	let age = Some(30);

	println!("在匹配前，age是{:?}",age);

	if let Some(age) = age {
		println!("匹配出来的age是{}",age);
	}

	println!("在匹配后，age是{:?}",age);
}
```

运行后输出如下：

```
(base) PS E:\demo> rustc hello.rs
(base) PS E:\demo> ./hello
在匹配前，age是Some(30)
匹配出来的age是30
在匹配后，age是Some(30)
```

可以看出在 `if let` 中，`=` 右边 `Some(i32)` 类型的 `age` 被左边 `i32` 类型的新 `age` 遮蔽了，该遮蔽一直持续到 `if let` 语句块的结束。因此第三个 `println!` 输出的 `age` 依然是 `Some(i32)` 类型。

对于 `match` 类型也是如此:

```
fn main() {
	let age = Some(30);

	println!("在匹配前，age是{:?}",age);

	match age 
	{
		Some(age) => println!("匹配出来的age是{}",age),
		_ =>()
	}

	println!("在匹配后，age是{:?}",age);
}
```

需要注意的是，**`match` 中的变量遮蔽其实不是那么的容易看出**，因此要小心！其实这里最好不要使用同名，避免难以理解，如下。

```
fn main() {
   let age = Some(30);
   println!("在匹配前，age是{:?}", age);
   match age {
       Some(x) =>  println!("匹配出来的age是{}", x),
       _ => ()
   }
   println!("在匹配后，age是{:?}",age);
}
```

#### while let 条件循环

```rust
// Vec是动态数组
let mut stack = Vec::new();

// 向数组尾部插入元素
stack.push(1);
stack.push(2);
stack.push(3);

// stack.pop从数组尾部弹出元素
while let Some(top) = stack.pop() {
    println!("{}", top);
}
```

这个例子会打印出 `3`、`2` 接着是 `1`。`pop` 方法取出动态数组的最后一个元素并返回 `Some(value)`，如果动态数组是空的，将返回 `None`，对于 `while` 来说，只要 `pop` 返回 `Some` 就会一直不停的循环。一旦其返回 `None`，`while` 循环停止。我们可以使用 `while let` 来弹出栈中的每一个元素。

你也可以用 `loop` + `if let` 或者 `match` 来实现这个功能，但是会更加啰嗦。

#### for 循环

```

#![allow(unused)]
fn main() {
let v = vec!['a', 'b', 'c'];

for (index, value) in v.iter().enumerate() {
    println!("{} is at index {}", value, index);
}
}
```

这里使用 `enumerate` 方法产生一个迭代器，该迭代器每次迭代会返回一个 `(索引，值)` 形式的元组，然后用 `(index,value)` 来匹配。

#### let 语句

```rust
let PATTERN = EXPRESSION;
```

是的， 该语句我们已经用了无数次了，它也是一种模式匹配：

```rust
let x = 5;
```

这其中，`x` 也是一种模式绑定，代表将**匹配的值绑定到变量 x 上**。因此，在 Rust 中,**变量名也是一种模式**，只不过它比较朴素很不起眼罢了。

```rust
let (x, y, z) = (1, 2, 3);
```

上面将一个元组与模式进行匹配(**模式和值的类型必需相同！**)，然后把 `1, 2, 3` 分别绑定到 `x, y, z` 上。

模式匹配要求两边的类型必须相同，否则就会导致下面的报错：

```rust
let (x, y) = (1, 2, 3);
```

对于元组来说，元素个数也是类型的一部分！



#### 函数参数

函数参数也是模式：

```rust
fn foo(x: i32) {
    // 代码
}
```

其中 `x` 就是一个模式，你还可以在参数中匹配元组：

```rust
fn print_coordinates(&(x, y): &(i32, i32)) {
    println!("Current location: ({}, {})", x, y);
}

fn main() {
    let point = (3, 5);
    print_coordinates(&point);
}
```

`&(3, 5)` 会匹配模式 `&(x, y)`，因此 `x` 得到了 `3`，`y` 得到了 `5`。

#### let 和 if let

对于以下代码，编译器会报错：

```rust
let Some(x) = some_option_value;
```

因为右边的值可能不为 `Some`，而是 `None`，这种时候就不能进行匹配，也就是上面的代码遗漏了 `None` 的匹配。

类似 `let` , `for`和`match` 都必须要求完全覆盖匹配，才能通过编译( 不可驳模式匹配 )。

但是对于 `if let`，就可以这样使用：

```rust
if let Some(x) = some_option_value {
    println!("{}", x);
}
```

因为 `if let` 允许匹配一种模式，而忽略其余的模式( 可驳模式匹配 )。

## 练习题

练习原题：https://zh.practice.rs/pattern-match/match-iflet.html

这里只是附上有答案版：

1.

```rust
enum Direction {
    East,
    West,
    North,
    South,
}

fn main() {
    let dire = Direction::South;
    match dire {
        Direction::East => println!("East"),
        Direction::South | Direction::North  => { // matching South or North here
            println!("South or North");
        },
        _ => println!("West"),
    };
}
```

2.

```rust
fn main() {
    let boolean = true;

    // fill the blank with an match expression:
    //
    // boolean = true => binary = 1
    // boolean = false =>  binary = 0
    let binary = match boolean {
        true => 1,
        false => 0
    };

    assert_eq!(binary, 1);
}
```

3.

```rust
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}

fn main() {
    let msgs = [
        Message::Quit,
        Message::Move{x:1, y:3},
        Message::ChangeColor(255,255,0)
    ];

    for msg in msgs {
        show_message(msg)
    }
} 

fn show_message(msg: Message) {
    match msg {
        Message::Move{x: a, y: b} => { // match  Message::Move
            assert_eq!(a, 1);
            assert_eq!(b, 3);
        },
        Message::ChangeColor(_, g, b) => {
            assert_eq!(g, 255);
            assert_eq!(b, 0);
        }
        _ => println!("no data in these variants")
    }
}
```

4.

```rust
fn main() {
    let alphabets = ['a', 'E', 'Z', '0', 'x', '9' , 'Y'];

    // fill the blank with `matches!` to make the code work
    for ab in alphabets {
        assert!(matches!(ab, 'a'..='z' | 'A'..='Z' | '0'..='9'))
    }
} 
```

5.

```rust
enum MyEnum {
    Foo,
    Bar
}

fn main() {
    let mut count = 0;

    let v = vec![MyEnum::Foo,MyEnum::Bar,MyEnum::Foo];
    for e in v {
        if matches!(e , MyEnum::Foo) { // fix the error with changing only this line
            count += 1;
        }
    }

    assert_eq!(count, 2);
}
```

6.

```rust
fn main() {
    let o = Some(7);

    if let Some(i) = o {
        println!("This is a really long string and `{:?}`", i);
    }
}
```

7.

```rust
enum Foo {
    Bar(u8)
}

fn main() {
    let a = Foo::Bar(1);

    if let Foo::Bar(i) = a {
        println!("foobar holds the value: {}", i);
    }
}
```

8.

```rust
enum Foo {
    Bar,
    Baz,
    Qux(u32)
}

fn main() {
    let a = Foo::Qux(10);

    match a {
        Foo::Bar => println!("match foo::bar"),
        Foo::Baz => println!("match foo::baz"),
        _ =>  println!("match others")
    }
}
```

9.

```rust
fn main() {
    let age = Some(30);
    if let Some(age) = age { // create a new variable with the same name as previous `age`
       assert_eq!(age, 30);
    } // the new variable `age` goes out of scope here
    
    match age {
        // match can also introduce a new shadowed variable
        Some(age) =>  println!("age is a new variable, it's value is {}",age),
        _ => ()
    }
 }
```