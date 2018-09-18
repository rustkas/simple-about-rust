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
    resut_char: &char,
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
        &resut_char,
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
        &resut_char,
    );
}

```
[Rust Playground](https://play.rust-lang.org/?gist=4f0d45838421a5b550dda0dcfe8a9850&version=stable&mode=debug&edition=2015)

Обратите внимание, как обобщенные функции могут упростить код, который без их использования многократно увеличил бы код программы.
Параметр <T> в шаблоне функции описывает то, что в методе будет использоваться какой-то тип данных (в момент написания функции неизвестный)
Во время компиляции программы, если данная функция используется, она используется с конкретными данными определённого типа. Засчёт этого происходит ускорение как написания кода, 
так и работы программы. 

