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


