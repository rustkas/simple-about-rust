## Функция (fn)

### Объявление и вызов функций
Функцией называется синтаксическая конструкция языка Rust, у которой есть имя, блок входны параметров и блок кода.
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





