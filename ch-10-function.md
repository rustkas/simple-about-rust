## Функция (fn)

### Объявление и вызов функций
Функцией называется синтаксическая конструкция языка Rust, у которой есть имя, блок входных параметров и блок кода.
```rust
#[allow(dead_code)]
fn funcion_name(_param: ()) {}
fn main() {
    #[allow(dead_code)]
    fn funcion_name(_param: ()) {}

    {
        #[allow(dead_code)]
        fn funcion_name(_param: ()) {}

        {
            #[allow(dead_code)]
            fn funcion_name(_param: ()) {}

            // #[allow(dead_code)]
            // fn funcion_name(_param: ()) {}
        }
    }
}


```
[Rust Playground](https://play.rust-lang.org/?gist=16737ecfcbcd4c4a35a90df327669153&version=stable&mode=debug&edition=2015)

Обратите внимание, что функции могут быть вложены в другие функции. Определение функция с одним и тем же именем не может 
встречаться более одного раза в одном блоке кода.

Как и у констант, область видимости функции является блок, в котором она определена а также дочерние блоки. Поэтому доступ к ней может быть раньше, чем её определение:

```rust
fn main() {
    funcion_name(());

    fn funcion_name(_param: ()) {}
}

```
[Rust Playground](https://play.rust-lang.org/?gist=e5fd5a975ce4d6d0625616f25299c8bd&version=stable&mode=debug&edition=2015)

### Скрытие функций (переопределение функций)
Как и переменные, константы, функции в дочерних блоках могут быть переопределены. Такое их свойство помогает заменять поведение функций с одним и тем же именем во вложенных блоках. Для того чтобы вызвать функции корневого блока используйте `::` перед
именем функции. 
```rust
fn funcion_name(_param: ()) {
    println!("outside");
}
fn main() {
    funcion_name(()); //call 1

    fn funcion_name(_param: ()) {
        println!("inside");
    }
    fn funcion_name2(_param: ()) {
        println!("inside2");
    }
    {
        funcion_name(());
        fn funcion_name(_param: ()) {
            println!("inside inside"); //call 2
            ::funcion_name(()); // call 3
            funcion_name2(()); // call 4
        }
    }
    ::funcion_name(()); // call 5
    funcion_name(()); // call 6
}

```
[Rust Playground](https://play.rust-lang.org/?gist=cada866284d5bb0daa2ebd52e17b16bb&version=stable&mode=debug&edition=2015)


#### Домашнее задание
Попробуйте вызвать функцию из родительского блока дочернюю функцию. Получится ли это у вас? Подумайте над сообщением компилятора.

### Использование аргументов функции
Функции будет делать больше полезной работы, если будет возможность добавлять входные параметры. В этом случае блок кода функции
будет представлять собой шаблон (подобно текстовому шаблону знакомого нам макроса `println!`. При этом работа внутри блока кода
может зависеть от входных параметров функции.
```rust
fn main() {
    fn sum_i8(addend1: i8, addend2: i8) {
        println!("{} + {} = {}", addend1, addend2, addend1 + addend2);
    }

    fn sum_f64(addend1: f64, addend2: f64) {
        println!("{} + {} = {}", addend1, addend2, addend1 + addend2);
    }
    fn sum_f32(addend1: f32, addend2: f32) {
        println!("{} + {} = {}", addend1, addend2, addend1 + addend2);
    }
    sum_f64(3.2, 5.1);
    sum_f32(3.2, 5.1);
    sum_i8(3, 5);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=d9892b6c37c8f988a0b0ccb236b8d820&version=stable&mode=debug&edition=2015)

Рабата входных аргументов функции аналогична работе с переменными. К параметрам функции более строгие требования чем к переменным. При их определении указание типа данных переменной обязательна. 

При передаче аргументов в функцию значений, эти значения копируются.

```rust
fn multiply_2(mut value: f32) {
    value *= 2.;
    println!("{}", value);
}
fn main() {
    let value = 4.;
    multiply_2(value);
    println!("{}", value);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=76985aacb79c77bcbcb4ce2d5fb834bc&version=stable&mode=debug&edition=2015)

Обратите внимание, что переменная может изменяться только при наличии маркера `mut`. Пожалуйста, проверьте это утверждение на 
практике, закомментировав `mut`.

Такое поведение аргументов функции называется `передача аргументов по значению`. Чтобы передать аргументов по ссылке и не копировать его содержимое - используйте ссылки в описании аргументов функции.
```rust
fn multiply_2(value: &mut f32) {
    *value *= 2.;
    println!("{}", value);
}
fn main() {
    let mut value = 4.;
    multiply_2(&mut value);
    println!("{}", value);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=14e1dd199800765a535a6839429b0883&version=stable&mode=debug&edition=2015)

```rust
fn main() {
    {
        fn change_char(a: &mut char) {
            *a = 'b'
        }
        let mut char_value = 'a';
        change_char(&mut char_value);
        println!("{}", char_value);
    }
    {
        fn change_i8(a: &mut i8) {
            *a = 5;
        }
        let mut value_i8 = 8;
        change_i8(&mut value_i8);
        println!("{}", value_i8);
    }
}
```

### Возвращение значения функцией
Кроме принятия входных данных функция может возвращать значения. Для описание выходного значения функции в Rust используется особый синтаксис.
```rust
fn multiply_2(value: f32) -> f32 {
    value * 2.
}
fn main() {
    let value = 4.;
    let resutl = multiply_2(value);
    println!("{}", resutl);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=cc855b367bed4b393a06499b021929ae&version=stable&mode=debug&edition=2015)

По умолчанию возвращаемое значение функции является `пустым кортежем` `()`. Проверим.
```rust
fn function1() {}
fn function2() -> () {}
fn main() {
    println!("{}", function1() == function2());
    println!("{:?}; {:?}", function1(), function2());
}

```
[Rust Playground](https://play.rust-lang.org/?gist=283f255bc213870e6bf913332e2d8d05&version=stable&mode=debug&edition=2015)

Обратите внимание, что возвращение значения из функции подробно возвращению значения из выражения языковых конструкций изученных ранее. И именно такой стиль программирования приветствуется в Rust. Для раннего выхода из функции помимо стандартного решения, 
в функции может использоваться ключевое слово `return`. Благодаря ему из функции может быть возвращено выходное значение в любом
месте функции.
```rust
fn function(x: f32) -> f64 {
    if x + 1. <= 0. {
        return 0. as f64;
    }
    (x + 3.) as f64
}

fn main() {
    print!("{} {}", function(18.), function(-3.));
}

```
[Rust Playground](https://play.rust-lang.org/?gist=af44e20b33a2f72a3f0087dd294b437f&version=stable&mode=debug&edition=2015)

### Возвращение нескольких значений из функции одновременно

Для целей возвращения нескольких значений разных типов из функции, весьма удобно использовать кортежи.

```rust
enum Enum {
    Enum1,
    Enum2,
}
struct Structura {
    value_i32: i32,
    value_boolean: bool,
}
struct TupleStructura(f64, f32, i8, u32, char);
fn function_enum1() -> Enum {
    Enum::Enum1
}
fn function_enum2() -> Enum {
    Enum::Enum2
}
fn f2() -> Structura {
    Structura {
        value_i32: 32,
        value_boolean: true,
    }
}
fn f3() -> TupleStructura {
    TupleStructura(4.7, 2., 3, 5, 'w')
}
fn f4() -> [u8; 4] {
    [7, 2, 0, 19]
}
fn f5() -> Vec<u8> {
    vec![120]
}

fn main() {
    println!(
        "{} {}",
        match function_enum1() {
            Enum::Enum1 => 10,
            Enum::Enum2 => 20,
            
        },
        match function_enum2() {
            Enum::Enum1 => true,
            Enum::Enum2 => false,
            
        }
    );
    println!("{} ", f2().value_i32);
    println!("{} ", f2().value_boolean);
    println!("{} ", f3().0);
    println!("{} ", f4()[0]);
    println!("{} ", f5()[0]);
}


```
[Rust Playground](https://play.rust-lang.org/?gist=19cdc7436791b2559baf8736cc9f3794&version=stable&mode=debug&edition=2015)

### Домашнее задание
Изучите тему работу со ссылочными переменными в функция более подробно. Напишите свои примеры их использования.
Найдите ограничения в вашей системе по использованию вложенных ссылок `&&`. Экспериментальным путём выясните предельно уровень
их вложенности.

### Изменение ссылок на переменную
В Rust очень важно как может изменяться переменная и кто может иметь ссылку на неё. Проблема ссылочной целостности - весьма важная и является источником явных и неявных проблемы. В Rust может быть так: или одна переменная изменяет другую и больше никакая переменная не может иметь доступ к ней, или есть множество переменных, которые могут читать значение этой переменной. Третьего не дано.

Приведём пример:
```rust
fn main() {
    let mut value1: char = 'a';
    let mut value2: char = '1';
    {
        let mut link: &mut char = &mut value1;
        println!("{} ", *link);
        *link = 'f';
        println!("{} ", *link);
        link = &mut value2;
        println!("{} ", *link);
        *link = '6';
        println!("{} ", *link);

        // let mut link2: &mut char = &mut value1;
        // println!(" {} ", *link2);
        // *link2 = 'k';
    }

    {
        let mut link: &mut char = &mut value1;
        println!(" {} ", *link);
        *link = 'k';
        println!(" {} ", *link);
        link = &mut value2;
        println!(" {} ", *link);
        *link = '5';
        println!(" {} ", *link);
    }
    {
        let link1: &char = &value1;
        let link2: &char = &value1;
        println!(" {} ", *link1);
        println!(" {} ", *link2);

        //  let mut link3: &mut char = &mut value1;
        //  println!(" {} ", *link3);
    }
}

```
[Rust Playground]( https://play.rust-lang.org/?gist=6e77747bce219ecef2550fbade7e62bc&version=stable&mode=debug&edition=2015)

#### Домашнее задание
Придумайте свои примеры с использованием изменений значений ссылочных переменных.
