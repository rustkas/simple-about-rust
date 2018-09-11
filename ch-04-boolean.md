## Логический тип данных

Логический тип данных в Rus представлен двумя константами `true` - истина, `false` - ложь.

### Операторы

В языке Rust используются следующие операторы сравнения:
- `==` равно
- `!=` не равно
- `<`  меньше
- `<=` меньше или равно
- `>`  больше
- `>=` больше или равно

Благодаря этим операторам можно сравнить два значения одно типа, например, целочисленные, дробные, логически, символьные и строковые
значения.

```rust
fn main() {
    println!("{}", true < false);
    println!("{}", true > false);
    
    println!("{}", 1 < 2);
    println!("{}", 1 == 1);
    println!("{}", 2 >= 1);
    
    println!("{}", 0.1 <        0.2);
    println!("{}", 0.11 <       0.12);
    println!("{}", 0.111 <      0.112);
    println!("{}", 0.1111 <     0.1112);
    println!("{}", 0.11111 <    0.11112);
    println!("{}", 0.111111 <   0.111112);
    println!("{}", 0.1111111 <  0.1111122);
    println!("{}", 0.11111111 < 0.11111122);
    
    println!("{}", 'a' < 'A');
    println!("{}", '1' == '1');
    
    println!("{}", "a" > "A");
    println!("{}", "aa" > "aA");
    
}

```

[Playground](https://play.rust-lang.org/?gist=46a9e4ffde8babaf21f50b438fda57ad&version=stable&mode=debug&edition=2015)

### Логические операторы

Логические значения могут быть связаны с помощью операторов логических связей. Это `&&` И, `||` ИЛИ, `!`Не.

```rust
fn main() {
    let false_variable = false;
    let true_variable = true;

    println!("{} {}", !true_variable, !false_variable);
    println!(
        "{} {} {} {}",
        false_variable || false_variable,
        false_variable || true_variable,
        true_variable || false_variable,
        true_variable || true_variable
    );
    println!(
        "{} {} {} {}",
        false_variable && false_variable,
        false_variable && true_variable,
        true_variable && false_variable,
        true_variable && true_variable
    );
}

```
[Playground](https://play.rust-lang.org/?gist=651caee0464e5e3f954d2210322f6545&version=stable&mode=debug&edition=2015)

Порядок операторов логических связей: `!`, `&&`, `||`. Изменить данный порядок можно с помощью круглых скобок.


```rust
fn main() {
    let false_variable = false;
    let true_variable = true;

    println!("{}", true_variable || false_variable && !true_variable);
    println!("{}", (true_variable || false_variable) && !true_variable);
}

```
[Playground](https://play.rust-lang.org/?gist=1d1b162a03861c6a79637dcd60ad0508&version=stable&mode=debug&edition=2015)

## Домашнее задание

Напишите цепочки логических вычислений с данными разных типов.


