## Диапазон
Рассмотрим ещё один тип данных стандартной библиотеки Rust - диапазоны (ranges). Диапазоном является отрезок значений,
в котом последний элемент не включается этот отрезок. Так как это тип данных, он может быть присвоен переменной и быть входным и 
выходных параметром функции.

```rust
fn main() {
    
    use std::ops::Range;
    
    let range: Range<isize> = -1..10;
    
    println!("[{:?}]; start = {}; end = {}; length = {}.", range, range.start, range.end-1, range.len());
    
    for i in range {
        print!("{}; ", i);
    }
}

```
Диапазоны могут быть различных типов данных:
```rust
fn main() {
    let _range = false .. true;
    let _range = true .. false;
    let _range = "hello" .. "world";
    let _range = "world" .. "hello";
    let _range = 45.12 .. 27.94;
    let _range = 'a' .. 'A';
    let _range = 'B' .. 'k';
    let _range = &'B' .. &'k';
    let _range = format!("{}",'B') .. format!("{}",'k');
    let _range = String::from("B") .. String::from("t");
    
}
```
### Домашнее задание
Попробуйте создать диапазоны различных типов: символов, перечислений, структур.
