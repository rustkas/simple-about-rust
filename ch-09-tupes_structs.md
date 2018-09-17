## Кортежи и структуры

### Кортежи
Кортежи помогают объединить в один набор значения разных типов. Они очень похожи на массивы за исключением некоторой отличии 
формы и состава содержания. Массивы в отличии от кортежей не могут содержать в себе данных разных типов.
Примеры объявления и вывода на консоль содержания кортежей:
```rust
fn main() {
    let data = (10_000_000, 183.19, 'й', 'Q', "Hello, Rust!", ());
    let copy_of_data = data;
    print!("{}, {}, {}, {}, {:?}", data.0, copy_of_data.1, data.3,data.4,data.5);
}
```

[Rust Playground](https://play.rust-lang.org/?gist=893a398973c3a8bfa07bdd1c223a99ad&version=stable&mode=debug&edition=2015)

Указания типа данных кортежа явным образом:

```rust
fn main() {
    let data: (u32, f32, char, char, &'static str, ()) = (10_000_000, 183.19, 'й', 'Q', "Hello, Rust!", ());
    let copy_of_data = data;
    print!(
        "{}, {}, {}, {}, {:?}",
        data.0, copy_of_data.1, data.3, data.4, data.5
    );
}

```
[Rust Playground](https://play.rust-lang.org/?gist=b750fd04cb84b9d579e744b28d4af0de&version=stable&mode=debug&edition=2015)

Также как и массивы (и другие переменные) кортеж для изменений должен содержать в своём объявлении ключевое слово `mut':
```rust
fn main() {
    let mut data: (u32, f32, char, char, &'static str, ()) = (10_000_000, 183.19, 'й', 'Q', "Hello, Rust!", ());
    
    data.0  = 1;
    data.1  = 1.1;
    data.2  = 'j';
    print!(
        "{}, {}, {}, {}, {}, {:?}",
        data.0, data.1,data.2, data.3, data.4, data.5
    );
}

```
[Rust Playground](https://play.rust-lang.org/?gist=d9b57a1a25b8d795deddbddb3752616f&version=stable&mode=debug&edition=2015)

Важным отличием кортежа от массива является то, что получить доступ по индексу, значение которой находится в переменной он не может.

```rust
fn main() {
    let array: [u16; 3] = [152, 133, 146];
    let _tuple: (u8, u16, u16) = (16, 153, 214);
    let i = 0;
    print!("{}", array[i]);
    //print!("{}", _tuple.i);
}
```
[Rust Playground](https://play.rust-lang.org/?gist=736b1c7dd2a119ac3385e71fb1b5854c&version=stable&mode=debug&edition=2015)

### Структура
Структурой является более сложная форма группировки значений разного типа. Каждому элементу структуры присваивается имя.
Благодаря этого элементы структуры легче объявить, получить доступ.
Пример объявления и инициализации структуры:

```rust
#[derive(Debug)]
struct Data {
    id: u16,
    text: &'static str,
    prefix: char,
}
fn main() {
    let data = Data {
        id: 405,
        text: "info",
        prefix: 'G',
    };

    print!("{:?}", data);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=7105f06f17612d276bb4e175dc8f078b&version=stable&mode=debug&edition=2015)


### Кортеж-Структура
В том случае если необходимо состав кортежа необходимо объявить заранее, тогда используют кортеж-структуру:

```rust
#[derive(Debug)]
struct Data(u16, &'static str, char, [i32; 5]);
fn main() {
    let data = Data(405, "info", 'G', [4555, 2334343, 65565]);

    println!("{:?}", data);
}

```

[Rust Playground](https://play.rust-lang.org/?gist=d72d3033f70d557fba32cc966cd3857e&version=stable&mode=debug&edition=2015)



