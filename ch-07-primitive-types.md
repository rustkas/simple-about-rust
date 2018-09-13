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


Для удобства написания длинных чисел используется символ-разделитель `_`. Оно помогает разделять разряды в числах и лучше 
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


| Тип |Количество байт | Минимальное значение | Максимальное значение | 
| --- | :-: | --- | --- |
| i8 | 1 | -128 | 127 | 
| i16 | 2 | -32768 | 32767 |
| i32 | 4 | -2_147_483_648 | 2_147_483_647 |
| i64 | 8 | -2<sup>63</sup> | 2<sup>63</sup> - 1 |
| u8 | 1 | 0 | 255 | 
| u16 | 2 | 0 | 65_535 |
| u32 | 4 | 0 | 4_294_967_295 |
| u64 | 8 | 0 | 2<sup>64</sup> - 1 |


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
Обратите, пожалуйста, внимание, что конвертация с помощью `as` приминима только к примитивным типам данных. 

#### Домашнее задание
Напишите программу, в которой будут приводиться все известные вам примитивные данные в другие. Постарайтесь составить все возможные комбинации форматов. Попробуйте провести конвертации в более сложные типы - познакомьтесь с сообщениями компилятора.

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

## Пустой кортеж ()
Кроме полезных типов данных - числовые, символьные, логические в Rust есть и "бесполезные", т.е. такие которые не выполняют никакой работы: не хранят данных, не изменяются, а несут в себе декоративные и можно даже сказать философский, концептуальный смысл. Таким особенным типом является пустой кортеж. Это недостающее звено, тип по умолчанию. Мы уже с ним неоднократно работали.
Рассмотрим примеры:

```rust
fn main() {
    let empty_tupel: () = ();
    let array_isize = {
        0b1;
        0b1;
        0b1
    };
    let array_isize_empty_tupel = {
        0x12;
        0x77;
        0o273;
    };
    let block = {};
    let if_block = if false {};
    let for_block = for _i in 0..1 {};
    let while_block = while false {};
    let loop_block = loop {
        break;
    };
    println!(
        "{:?} {:?} {:?} {:?} {:?} {:?} {:?} {:?}",
        empty_tupel,
        array_isize,
        array_isize_empty_tupel,
        block,
        if_block,
        for_block,
        while_block,
        loop_block
    );
    //println!("empty tupel size = {}", () as usize);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=c51df68030ca7010fb4ad335bdfc13f8&version=stable&mode=debug&edition=2015)


### Домашнее задание
Попробуйте применить к пустому кортежу математические, логические, какие-нибудь ещё другие операции. Напишите программу-исследование постового кортежа. К какие вы выводам придёте? Какие свои правила выработаете?

Пример исследования
```rust
fn main() {
    let empty_tupel:() = ();
    
    println!("empty tupel = {:?}", empty_tupel);
    println!("empty tupel = {:#?}", empty_tupel);
    
    while () == () {
        break;
    }
    
    // for _i in 0..(() as isize) { }
    if () != (){}else {}
    if () == (){} else if () == () {}
    // let _value_1 = () + ();
    // let _value_1 = () - ();
    // let _value_1 = () * ();
    // let _value_1 = () / ();
    // let _value_1 = () % ();
    // let _value_1 = () && ();
    // let _value_1 = () || ();
    // let _value_1 = () ^ ();
}

```
[Rust Playground](https://play.rust-lang.org/?gist=3ecae5cf30dc95b9d236cfe777b2d8c2&version=stable&mode=debug&edition=2015)



## Описание типов данных массивов и векторов
Для предотвращения явной или неявной ошибки при работе с массивами, векторами или другими типами данных - необходимо, чтобы как 
можно меньше "умный" компилятор предполагал. Для этого, если конечно же такая возможность есть, нужно указывать типы данных переменных при их объявлении.

Чтобы объявить тип данных массива необходимо после двоеточия указать тип данных и размер массива:
```rust
fn main() {
    let _empty_array: [u8; 0] = [];
    let _empty_array: [i16; 0] = [];
    let _empty_array: [usize; 0] = [];
    let _empty_array: [isize; 0] = [];
    let _empty_array: [char; 0] = [];
    let _empty_array: [bool; 0] = [];
    let _empty_array: [(); 0] = [];
}

```
[Rust Playground](https://play.rust-lang.org/?gist=e50b7a06a035e934cec4081fca6ae487&version=stable&mode=debug&edition=2015)


Чтобы объявить тип данных вектора необходимо после двоеточия указать тип данных в угловых скобках (тут мы стакиваемся с описанием ещё более сложных типов данных, чем массив и пустой кортеж):
```rust
fn main() {
    let _vector: Vec<u8> = vec![0, 0, 0, 0, 1];
    let _vector: Vec<u16> = vec![0, 0, 0, 0, 1];
    let _vector: Vec<u32> = vec![0, 0, 0, 0, 1];
    let _vector: Vec<u64> = vec![0, 0, 0, 0, 1];
    let _vector: Vec<i8> = vec![0, 0, 0, 0, 1];
    let _vector: Vec<isize> = vec![0, 0, 0, 0, 1];
    let _vector: Vec<isize> = vec![0; 19];
    let _vector: Vec<usize> = vec![0; 1];
    let _vector: Vec<char> = vec!['a', 'b', 'c', 'd', 'f'];
    let _vector: Vec<()> = vec![(); 1];
}

```
[Rust Playground](https://play.rust-lang.org/?gist=96b3fc5eb439b6b73bb2db3fd5867fba&version=stable&mode=debug&edition=2015)

#### Домашнее задание
Напишите свои объявления массивов и векторов.

### Константы
В коде программы существует возможность объявить константное значение. Его особенностью является то, что во время компиляции 
необходимо указать его тип и значение. Без этой информации константа не будет считаться описанной правильным образом. Помимо этих необходимых условий содержания, компилятор также следить за правильностью формы. Поэтому стиль программирования Rust требует от констант быть написанными символами верхнего регистра. Важной особенностью константы является его область действия. Вы можете вызвать константу в начале блока, а объявить её после. Rust не будет вам об этом сообщать, но лучше всё-таки объявлять 
константы до их использования.

```rust
fn main() {
    println!("{}", CONST1);
    const CONST1: i8 = 0;
    {
        println!("{}", CONST1);
        const CONST1: i8 = 1;
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=5010895a08a85d4a970162f774b8e58f&version=stable&mode=debug&edition=2015)

#### Домашнее задание 
Напишите объявление констант разных типов и используйте их в различных комбинациях синтаксических конструкций.


