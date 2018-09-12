### Выражение if

Синтаксическая конструкция `if` служит для логическогой проверки и выполнения блока кода при определённом условии. 
В языке Rust в этой коснтрукции постарались исключить многие потенциальные явные и скрытые ошибки. 

```rust
fn main() {
    if 2 + 2 == 4 {
        println!("{}", 4);
    }
    if 2 + 2 != 5 {
        println!("{}", 5);
    }
    if '2' > '1' {
        println!("{}", 2);
    }
    if true {
        println!("{}", true);
    }
    if false {
        println!("{}", false);
    }
}
```
[Rust Playground](https://play.rust-lang.org/?gist=6a883c18c215cc0b4eee1038181020ba&version=stable&mode=debug&edition=2015)

Обратите внимание, что условное выражение не заключается в скобки, а фигурные скобки обязательные. Пожалуйста проверьте эти слова, 
написав проверочные программы, в результате работы которые будут получены сообщения об ошибках синтаксиса конструкции `if`.
#### Домашнее задание
Используя синтаксическую конструкцию `if true {}` создайте условия для ошибки - переполнения стека (`thread 'main' has overflowed its stack
fatal runtime error: stack overflow`). Вариант правильного ответа (не подглядывайте! - напишите свой) 
[Rust Playground](https://play.rust-lang.org/?gist=233e25f77722d8020df0e8b1904b78bd&version=stable&mode=debug&edition=2015)

### Выражение if else else if

Условные варажения могут описывать различные условия и быть вложенными. Хороший стиль программирования, а также [технические ограничения](https://play.rust-lang.org/?gist=077855bdf79a6a1e72f4baba2d095cb2&version=stable&mode=debug&edition=2015) 
и здравый смысл - всё это рекомендует делать эти конструкции как можно компактнее и проще.
```rust
fn main() {
     let n = 0;
    // let n = 1;
    // let n = 10 * 1000;
    // let n = -1;
    if n > 5000 {
        print!("Это число большое");
    } else if n > 0 {
        print!("А это числон небольшое");
    } else if n < 0 {
        print!("А это число отрицательное");
    } else {
        print!("А это ноль.");
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=f812ddc126ea8e45a6e55771fce1511e&version=stable&mode=debug&edition=2015)

### Условная инициализация переменной 

Существует возможность условной инициализации переменной при помощи конструкции `if`. Эта коснтрукция является скокращенной записью
более длинного выражения. Обратите внимание, что два следующих блока кода эквивалентны:
```rust
fn main() {
    {
        let a;
        if 2 + 2 == 4 {
            let b = 2 + 2 + 2;
            a = b;
        } else {
            let b = 20 + 20 + 20;
            a = b;
        }
        println!("{}", a);
    }
    {
        let a = if 2 + 2 == 4 {
            let b = 2 + 2 + 2;
            b
        } else {
            let b = 20 + 20 + 20;
            b
        };
        println!("{}", a);
    }
}
```
[Rust Playground](https://play.rust-lang.org/?gist=ed08f47ee6000ab7cb0ede9776c27361&version=stable&mode=debug&edition=2015)

## Цикл `while`

В языке Rust существует цикл с предусловием `while`. Благодаря ему можно многократно выполнять содержание блока кода.

```rust
fn main() {
    let mut j = 0;
    while j <= 256 {
        print!("{} ", j * j);
        j += 1;
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=9e312f74c4c1978b98350f2772b44ebb&version=stable&mode=debug&edition=2015)

### Домашнее задание.
Попробуйте произвести инициализацию переменной с помощью цикла `while`. Какой результат у вас получится? Если у вас появятся вопросы
без ответа - это хорошо. На последующих занятиях мы найдем на них ответы.

Пример решения. [Rust Playground](https://play.rust-lang.org/?gist=eb79d95da6f133fd968b8bf4a12b4d4e&version=stable&mode=debug&edition=2015)



