## Анонимные функции

Ститические функции в Rust не могут иметь доступ к локальным переменным.
```rust
fn main() {
    let three = 3;
    fn print_triple(x: u8) {
        print!("{}", x * three);
    }
    print_triple(7);
}
```

Для только внешние ститические переменные и костанты могут использоваться.

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

### Пример анонимной функции
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
