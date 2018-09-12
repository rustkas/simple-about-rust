## Хранилища однотипных данных

 
В стандартной библиотеке Rust сущесвует множество различных хранилищ последовательностей данных. Рассмотрим два наиболее часто используемых.
Это статические массивы или просто `массивы` и `вектора`.

### Массивы
Если нам необходимо сохранить в одной переменой несколько числовых, символьных, логических или тестовых значений, то для этого может 
подойти `массив`.
```rust
fn main() {
    let _array1 = [1, 2, 3, 4];
    let _array2 = [1., 2., 3., 4.];
    let _array3 = ['1', '2', '3', '4'];
    let _array4 = [true, true, true, false];
    let _array4 = ["true", "true", "true", "false"];
}


```
[Rust Playground](https://play.rust-lang.org/?gist=d7fd6960f64468556ada3a607815c92c&version=stable&mode=debug&edition=2015)


Для того чтобы узнать размер массивы можно использовать функцию `len`:
```rust
fn main() {
    let array1 = [1, 2, 3, 4];
    let array2 = [1., 2., 3., 4.];
    let array3 = ['1', '2', '3', '4'];
    let array4 = [true, true, true, false];
    let array5 = ["true", "true", "true", "false"];
    print!("{}, {}, {}, {}, {}", array1.len(), array2.len(), array3.len(), array4.len(), array5.len());
}


```
[Rust Playground](https://play.rust-lang.org/?gist=7e3b652c6fa10c59d2ed7906fee0104f&version=stable&mode=debug&edition=2015)




