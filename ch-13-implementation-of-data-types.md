## Реализация типов данных в Rust

Мы уже многое знаем, умеем - создавать переменные, знаем о видах памяти, операторы. Теперь настала пора узнать подробнее о реализации
изученные типов данных, чтобы лучше понять как они работают. Это интересно.

### Размеры типов и переменных
Для получения данных о размере типа данных используется функция `std::mem::size_of`. Для получения размера переменной в байтах используется `std::mem::size_of_val`.
Рассмотрим их применение на примере.
```rust
fn main() {
    print!("{} ", std::mem::size_of::<u8>());
    print!("{} ", std::mem::size_of::<u16>());
    print!("{} ", std::mem::size_of::<u32>());
    println!("{} ", std::mem::size_of::<u64>());

    print!("{} ", std::mem::size_of::<i8>());
    print!("{} ", std::mem::size_of::<i16>());
    print!("{} ", std::mem::size_of::<i32>());
    println!("{} ", std::mem::size_of::<i64>());

    print!("{} ", std::mem::size_of::<bool>());
    println!("{} ", std::mem::size_of::<char>());

    print!("{} ", std::mem::size_of::<String>());
    print!("{} ", std::mem::size_of::<Vec<u8>>());
    print!("{} ", std::mem::size_of::<Vec<u16>>());
    print!("{} ", std::mem::size_of::<Vec<u32>>());
    println!("{} ", std::mem::size_of::<Vec<u64>>());

    print!("{} ", std::mem::size_of_val(&12u8));
    print!("{} ", std::mem::size_of_val(&12u16));
    print!("{} ", std::mem::size_of_val(&12u32));
    println!("{} ", std::mem::size_of_val(&12u64));
    
}

```
[Rust Playground](https://play.rust-lang.org/?gist=ea0e72a140424378062357d86a059adc&version=stable&mode=debug&edition=2015)
Обратите внимание на синтаксис вызова этих функций. 

Размер типов данных isize, usize, &i8, &u32 (`&` - обозначает ссылку на тип, описание которого следует далее).
```rust
fn main() {
    use std::mem::*;
    print!("{} {} {} {}",
    size_of::<isize>(),
    size_of::<usize>(),
    size_of::<&i8>(),
    size_of::<&u32>());
}
```

#### Домашнее задание
Напишите свои версии использования данных функций.

### Использование use
Для уменьшения печати длинных ссылок на элементы сторонних библиотек удобно использовать концепцию описания импорта. В Rust
это реализуется с помощью ключевого слова `use`. Примеры использования:

Вариант №1:
```rust
fn main() {
    use std::mem;
    print!("{} ", mem::size_of::<u8>());
    print!("{} ", mem::size_of::<u16>());
}

```

##### Домашне задание
Изучите сообщение компилятора при работе следующего примера:
```rust
fn main() {
    use std::mem;
    print!("{} ", std::mem::size_of::<u8>());
    print!("{} ", std::mem::size_of::<u16>());
}

```

Вариант №2:
```rust
fn main() {
    use std::mem::size_of;
    use std::mem::size_of_val;
    print!("{} ", size_of::<u8>());
    println!("{} ", size_of_val(&12u64));
}

```
##### Домашне задание
Будет ли ошибкой оставить ссыку на `mem::size_of_val` при печати на консоль? Если да, то почему? Если нет, то почему?

Вариант №3:
```rust
fn main() {
    use std::mem::*;

    print!("{} ", size_of::<u8>());
    println!("{} ", size_of_val(&12u64));
}

```
[Rust Playground](https://play.rust-lang.org/?gist=52a9b014c50f8486525be195d4099c39&version=stable&mode=debug&edition=2015)
Обратите внимание, что при данном варианте ссылке на функции, вы можете использовать все функции, которые размещены в пространстве имён `std::mem::`.

```rust
#[allow(dead_code)]
fn main() {
    enum Enum1 {
        EnumItem1,
        EnumItem2,
    };
    enum Enum2 {
        EnumItem1,
        EnumItem2(f64),
        EnumItem3(i8, i16, i32, i64),
        EnumItem4(u8, u16, u32, u64),
    };

    use std::mem::size_of_val;
    println!("{}", size_of_val(&[0i8; 1]));
    println!("{}", size_of_val(&[0i16; 1]));
    println!("{}", size_of_val(&[0i32; 1]));
    println!("{}", size_of_val(&Enum1::EnumItem1));
    println!("{}", size_of_val(&Enum2::EnumItem4(0u8, 0u16, 0u32, 0u64)));
}

```
[Rust Playground](https://play.rust-lang.org/?gist=d1425abf4934f24d6ba109744b668009&version=stable&mode=debug&edition=2015)



