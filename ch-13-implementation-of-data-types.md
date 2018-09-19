## Реализация типов данных в Rust

Мы уже многое знаем, умеем - создавать переменные, знаем о видах памяти, операторы. Теперь настала пора узнать подробнее о реализации
изученные типов данных, чтобы лучше понять как они работают. Это интересно.

### Размеры типов и переменных
Для получения данных о размере типа данных используется функция `std::mem::size_of`. Для получения размера переменной в байтах используется `std::mem::size_of_val`.
Рассмотрим их применение на примере.
```rust
fn main() {
    print!("{} ", std::mem::size_of::<u8>());
    print!("{} ", std::mem::size_of::<u16>());
    print!("{} ", std::mem::size_of::<u32>());
    println!("{} ", std::mem::size_of::<u64>());

    print!("{} ", std::mem::size_of::<i8>());
    print!("{} ", std::mem::size_of::<i16>());
    print!("{} ", std::mem::size_of::<i32>());
    println!("{} ", std::mem::size_of::<i64>());

    print!("{} ", std::mem::size_of::<bool>());
    println!("{} ", std::mem::size_of::<char>());

    print!("{} ", std::mem::size_of::<String>());
    print!("{} ", std::mem::size_of::<Vec<u8>>());
    print!("{} ", std::mem::size_of::<Vec<u16>>());
    print!("{} ", std::mem::size_of::<Vec<u32>>());
    println!("{} ", std::mem::size_of::<Vec<u64>>());

    print!("{} ", std::mem::size_of_val(&12u8));
    print!("{} ", std::mem::size_of_val(&12u16));
    print!("{} ", std::mem::size_of_val(&12u32));
    println!("{} ", std::mem::size_of_val(&12u64));
    
}

```
Обратите внимание на синтаксис вызова этих функций. 

#### Домашнее задание
Напишите свои версии использования данных функций.

