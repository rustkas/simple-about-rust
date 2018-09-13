## Использование простых типов данных в Rust

В Rust целые числа могут быть представлены в различных системах счисления: десятичной, двоичной, восмеричной и шестнадцатиричной.
```rust
fn main() {
    let hexadecimal = 0x10;
    let decimal = 10;
    let octal = 0o10;
    let binary = 0b10;
    print!("{} {} {} {}", hexadecimal, decimal, octal, binary);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=ee23d23b45b036e44ad9c74c4640aeda&version=stable&mode=debug&edition=2015)


Для удобства написания длинных чисел используется символ-разделитель `_`. Оно помогает разделять разрадя в числах и лучше 
ориентироваться в них.
```rust
fn main() {
    let hexadecimal = 0x_01FF_F7B3;
    let decimal = 9_837_557;
    let octal = 0o_673_551_703;
    let binary = 0b_1111_0000_1111_0000;
    print!("{} {} {} {}", hexadecimal, decimal, octal, binary);
}


```
[Rust Playground](https://play.rust-lang.org/?gist=95f73e120b2b697d1d7ab1e4a7c496e3&version=stable&mode=debug&edition=2015)

Дробные числа могут быть представлены в экспоненциальной форме.
```rust
fn main() {
    let one_thousand = 1e3;
    let one_million = 1e6;
    let thirteen_billions_and_half = 13.5e9;
    let twelve = 12e-6;
    print!(
        "{} {} {} {}",
        one_thousand, one_million, thirteen_billions_and_half, twelve
    );
}


```
[Rust Playground](https://play.rust-lang.org/?gist=ff4b19277a8cdf4bc3a61acb721be467&version=stable&mode=debug&edition=2015)

Для эффективности расходования памяти в Rust введено несколько типов числовых типов данных. Для целый числе (`i8`, `i16`, `i32`, `i64`), для дробных чисел (`f32`, `f64`). Из названия видно, что каждый из этих типов данных имеет свою разрядность. Кроме того для целых чисел есть и аналогичные беззнаковые типы данных (`u8`, `u16`, `u32`, `u64`).
```rust
fn main() {
    let value_u8 = 1;
    let value_u16 = 1;
    let value_u32 = 1;
    let value_u64 = 1;
    
    let value_i8 = 1;
    let value_i16 = 1;
    let value_i32 = 1;
    let value_i64 = 1;
    
    let value_f32 = 1;
    let value_f64 = 1;
    
    print!(
        "{} {} {} {}\n{} {} {} {}\n{} {}",
        value_i8, value_i16, value_i32, value_i64,
        value_u8, value_u16, value_u32, value_u64,
        value_f32, value_f64,
    );
}


```
[Rust Playground](https://play.rust-lang.org/?gist=dac256d2d1c14f9d8a615d49e496269a&version=stable&mode=debug&edition=2015)


