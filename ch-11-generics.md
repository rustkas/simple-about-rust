## Обобщенные структуры и функции
Необходимость использования обобщенных функций и структур обусловлена желанием писать меньше кода и быстрее получать желанный результат, 
когда параметров и комбинаций входных значений, типов данных может быть сколь угодно много.
Пример:
```rust
fn function<T>(compare: char, value1: T, value2: T) -> T {
    if compare == 'a' {
        value1
    } else {
        value2
    }
}

fn print(
    resut_i8: &i8,
    resut_i16: &i16,
    resut_i32: &i32,
    resut_i64: &i64,
    resut_u8: &u8,
    resut_u16: &u16,
    resut_u32: &u32,
    resut_u64: &u64,
    resut_bool: &bool,
    resut_char: &char
) {
    print!(
        " {} {} {} {}  {} {} {} {}  {}  {}  ",
        resut_i8,
        resut_i16,
        resut_i32,
        resut_i64,
        resut_u8,
        resut_u16,
        resut_u32,
        resut_u64,
        resut_bool,
        resut_char
    );
}

fn main() {
    let mut resut_i8: i8 = function::<i8>('a', -1, -2);
    let mut resut_i16: i16 = function::<i16>('a', -1, -2);
    let mut resut_i32: i32 = function::<i32>('a', -1, -2);
    let mut resut_i64: i64 = function::<i64>('a', -1, -2);

    let mut resut_u8: u8 = function::<u8>('a', 1, 2);
    let mut resut_u16: u16 = function::<u16>('a', 1, 2);
    let mut resut_u32: u32 = function::<u32>('a', 1, 2);
    let mut resut_u64: u64 = function::<u64>('a', 1, 2);

    let mut resut_bool: bool = function::<bool>('a', true, false);

    let mut resut_char: char = function::<char>('a', 'w', 'v');
    print(
        &resut_i8,
        &resut_i16,
        &resut_i32,
        &resut_i64,
        &resut_u8,
        &resut_u16,
        &resut_u32,
        &resut_u64,
        &resut_bool,
        &resut_char
    );
    ///////////////////////////////////////////////
    resut_i8 = function::<i8>('b', -1, -2);
    resut_i16 = function::<i16>('b', -1, -2);
    resut_i32 = function::<i32>('b', -1, -2);
    resut_i64 = function::<i64>('b', -1, -2);

    resut_u8 = function::<u8>('b', 1, 2);
    resut_u16 = function::<u16>('b', 1, 2);
    resut_u32 = function::<u32>('b', 1, 2);
    resut_u64 = function::<u64>('b', 1, 2);

    resut_bool = function::<bool>('b', true, false);

    resut_char = function::<char>('b', 'w', 'v');

    print(
        &resut_i8,
        &resut_i16,
        &resut_i32,
        &resut_i64,
        &resut_u8,
        &resut_u16,
        &resut_u32,
        &resut_u64,
        &resut_bool,
        &resut_char
    );
}

```
[Rust Playground](https://play.rust-lang.org/?gist=4f0d45838421a5b550dda0dcfe8a9850&version=stable&mode=debug&edition=2015)

Обратите внимание, как обобщенные функции могут упростить код, который без их использования многократно увеличил бы код программы.
Параметр <T> в шаблоне функции описывает то, что в методе будет использоваться какой-то тип данных (в момент написания функции неизвестный)
Во время компиляции программы, если данная функция используется, она используется с конкретными данными определённого типа. Зачёт этого происходит ускорение как написания кода, 
так и работы программы. 
    
 ### Домашнее задание
 Проверьте, есть ли какие-либо ограничения для параметров функции (по количеству или ещё какие-либо).
 
 ## Использование обобщенных данных при определении структур, структур-кортежей, кортежей
 Также как и в функциях обобщенные типы данных могут использоваться в структурах, структурах-кортежах, кортежах.
 ```rust
#[derive(Debug)]
struct Structura<Type1, Type2> {
    value_char: char,
    type1_item1: Type1,
    type1_item2: Type1,
    type2_item1: Type2,
}

#[derive(Debug)]
struct StructuraEnum<Type1, Type2>(char, Type1, Type1, Type2);

#[derive(Debug)]
enum Enum<Type1, Type2> {
    Item1(Type1, Type2),
    Item2(Type1, Type2),
    Item3(Type1, Type2),
}

fn main() {
    let structura = Structura {
        value_char: 'a',
        type1_item1: 34,
        type1_item2: 782,
        type2_item1: 0.02,
    };
    println!("{:?}", structura);

    let structura_enum = StructuraEnum('j', 4, 555, 4.049);
    println!("{:?}", structura_enum);
    let enum_item1:Enum<i8,i8>= Enum::Item1(1, 1);
    let enum_item2:Enum<i8,i8> = Enum::Item2(1, 1);
    let enum_item3:Enum<i8,i8> = Enum::Item3(1, 1);
    println!("{:?};{:?};{:?};", enum_item1, enum_item2, enum_item3);
}

 ```
 [Rust Playground](https://play.rust-lang.org/?gist=e0bb152ea2bd3296ddb7e4d802461fcf&version=stable&mode=debug&edition=2015)
 
 При работе с перечислениями использование обобщений может выглядеть следующим образом:
 ```rust
 #[derive(Debug)]
#[allow(dead_code)]
enum Cat<Id, ColorCount> {
    Leopard(Id, ColorCount),
    Puma,
    Lion,
    Tiger,
    Manul,
}

fn main() {
    let cat1: Cat<char, i8> = Cat::Leopard::<char, i8>('d', 6);
    println!("{:?}", cat1);
}

 ```
[Rust Playground](https://play.rust-lang.org/?gist=c7081f651763c2dd1b389df1a1779d8a&version=stable&mode=debug&edition=2015)

### Использование обобщенных данных в стандартной библиотеке Rust
В стандартной библиотеке Rust обобщенные данные активно используются. Очень часто используется в enum `enum Option<T>`
```rust
enum Option<T> {
  Some(T),
  None,
}
```
Пример:
```rust
fn main() {
    let mut vector = vec![110, 922, 533];
    for _ in 0..5 {
        let item: Option<u16> = vector.pop();
        match item {
            Some(number) => print!("{}, ", number),
            None => print!("%, "),
        }
    }
}

```

Данное шаблонное решение наглядно показывается как использовать `enum Option<T>`. Если данные есть - возвращается `Some`. Если данных нет - возвращается `None`.

При невозможности вернуть данные определенного формата для описания значения используется `enum Result`:
```rust
fn main() {
    fn dividing(numerator: f32, denominator: f32) -> Result<f32, String> {
        if denominator == 0. {
            Err(format!("Divide by zero"))
        } else {
            Ok(numerator / denominator)
        }
    }
    print!("{:?}, {:?}", dividing(68., 0.), dividing(80., 29.) );
}

```

Использование функций стандартной библиотеки
Иногда бывает весьма удобно использовать уже проверенные решения стандартной библиотеки. Для задач проверки всё ли в порядке перед тем, как получить/передать данные в другую функции используются методы `is_err()`, `is_ok()` перечисления `Rusult`:
```rust
fn main() {
    fn dividing(numerator: f32, denominator: f32) -> Result<f32, String> {
        if denominator == 0. {
            Err(format!("dividing by zero"))
        } else {
            Ok(numerator / denominator)
        }
    }
    const result1 = dividing(57., 29.);
    const result2 = dividing(57., -90.);
    println!("{} {}", result1.is_ok(), result2.is_ok());
    println!("{} {}", result1.is_err(), result2.is_err());
    if result1.is_ok() { println!("{}", result1.unwrap()); }
    if result2.is_ok() { println!("{}", result2.unwrap()); }
    
}

```
Обратите внимание, что для создания данных типа `String` используется макрос `format!`.

