## Использование простых типов данных в Rust

В Rust целые числа могут быть представлены в различных системах счисления: десятичной, двоичной, восьмеричной и шестнадцатеричной.
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

Кроме этих форматов существуют ещё `usize`, `isize` - это специальный формат данный, который наиболее удобен и в идеальном 
случае должен совпадать с разрядностью той операционной системы, на которой должна запускаться программа. Благодаря этим типам
данных минимизируется количество внутренних вычислений наиболее подходящего формата данных. Кроме того, если формат числовых 
данных не задан явно, компилятор использует наиболее подходящий по его мнению формат. Для дробных чисел также существует такой формат. Но он является внутренней реализацией и задаваться явным образом не может.

Приведем пример:

```rust
fn main() {
    let array = [110, -122, 373];
    let i: usize = 2;
    // let i: isize = 2;

    print!("{}", array[i]);
}
```
[Rust Playground](https://play.rust-lang.org/?gist=082b64fbd9db36e9c7d9a321f4c76a99&version=stable&mode=debug&edition=2015)

### Домашнее задание
- Попробуйте получить доступ к элементу массива и/или вектора с помощью различных числовых типов данных индекса `i`.
- Инициируйте переменную и укажите её тип, создайте ещё одну переменную другого типа и попробуйте присвоить первому значению 
второе. Что получится? Множено ли добиться успеха и как? Найдите решение.

### Явное приведение типа
В языке Rust есть ключевое слово для явного приведения типа одного значения к другому. Это `as`.

```rust
fn main() {
    let value_i8 = 5 as i8;
    let value_u16 = 256 as u16;
    let value_u32 = 10_000 as u32;
    print!("{} {} {}", value_i8, value_u16, value_u32);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=03d0c96af5b43449db5ed1f7dd757afd&version=stable&mode=debug&edition=2015)

#### Домашнее задание
Напишите программу, в которой будут приводиться все известные вам примитивные данные в другие. Постарайтесь составить все возможные комбинации форматов.

### Числа с суффиксом
Для краткости описания данных, информативности и оптимизации существует возможность при объявлении числового значения в коде программы, указать его тип:
```rust
fn main() {
    let value_i8 = 5i8;
    let value_u16 = 256u16;
    let value_u32 = 10_000u32;
    print!("{} {} {}", value_i8, value_u16, value_u32);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=487a79ad106f9903fc35c58ccaa3cbd7&version=stable&mode=debug&edition=2015)












