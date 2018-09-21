## Анонимные функции

Статические функции в Rust не могут иметь доступ к локальным переменным.
```rust
fn main() {
    let three = 3;
    fn print_triple(x: u8) {
        print!("{}", x * three);
    }
    print_triple(7);
}
```

Для только внешние статические переменные и константы могут использоваться.

Константа:
```rust
const THREE: u8 = 3;
fn print_triple(x: u8) {
    print!("{}", x * THREE);
}
fn main() {
    print_triple(7);
}

```

Статическая переменная:
```rust
static THREE: u8 = 3;
fn print_triple(x: u8) {
    print!("{}", x * THREE);
}
fn main() {
    print_triple(7);
}
```

### Примеры использования анонимной функции
Вызов анонимной функции может выглядеть следующим образом:
```rust
fn main() {
    let mut arr = [34, 708, 16, 160, 90, 0, 645, 512, 27];
    use std::cmp::Ordering;
    // let desc = |a: &i32, b: &i32| -> Ordering {
    //     if a < b { Ordering::Greater }
    //     else if a > b { Ordering::Less }
    //     else { Ordering::Equal }
    // };
    arr.sort_by(|a: &i32, b: &i32| -> Ordering {
        if a < b {
            Ordering::Greater
        } else if a > b {
            Ordering::Less
        } else {
            Ordering::Equal
        }
    });
    print!("{:?}", arr);
}

```
Или так:
```rust
fn main() {
    
    let multiply = |a| a * 6;
    
    print!("{}", multiply(14));
    
    let multiply_ref: &(Fn(i8) -> i8) = &multiply;
    print!(
        " {} {}",
        (*multiply_ref)(14),
        multiply_ref(14)
        );
}
```
[Rust Playground](https://play.rust-lang.org/?gist=8003830639c6deca1a25b4a473bd4630&version=stable&mode=debug&edition=2015)

Обратите внимание на выражение инициализации ссылки на объявление функции. Очень интересно! `&(Fn(i8) -> i8)`.

#### Домашнее задание
Пожалуйста, напишите объявление переменных различных функций и присвойте им значения.

Ещё примеры работы с анонимными функциями:
```rust
fn main() {
    {
        let anonimus = || -> () { println!("-----") };
        let ref_item: &(Fn() -> ()) = &anonimus;
        println!("{:?}", ref_item());
        anonimus();
        ref_item();
    }
    {
        fn main(){println!("main")}
        let main1 = || -> () {  };
        
        let anonimus:&(Fn()->()) = &main1;
        println!("{}", std::mem::size_of_val(&anonimus));
        main1();
        anonimus();
        let anonimus:&(Fn()->()) = &main;
        main();
        anonimus();
    }
}
```
