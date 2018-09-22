## Строка
### Статические строки - литералы `&str`
Строка в Rust - является неизменяемой последовательностью литералов. Тип этих данных - `&str`.

```rust
fn main() {
    let item1: &str = "";
    let item2: &str = "0123456789";
    let item3: &str = "абвгд";
    print!("{} {} {}", item1, item2, item3);
}

```

Важной особенностью данных ссылочных функций является, то, что доступ к при попытке получить доступ к значениям будет является ошибкой при компиляции. Кроме того, в данной ссылке храниться как сама ссылка так и размер данных,  которые можно получить по 
ссылке.

В следующем примере кода ни одна строчка не скомпилируется, т.к. значение переменной `str` неизвестно в момент компиляции. Следовательно конкретное значение памяти для хранения значения не может быть выделено.
```rust
fn main() {
  // let a: str;
  //  fn f(a: str) {}
  //  print!("{}", std::mem::size_of::<str>());
}
```
Изучим размеры этого типа данных на примере. Пожалуйста, сами поэкспериментируйте со значениями.

```rust
fn main() {
    let item1: &str = "";
    let item2: &str = "012345678914";
    let item3: &str = "абвгд";
    println!("{} {} {}", item1, item2, item3);

    use std::mem::size_of_val;

    println!(
        "{}:{}:{}; {}:{}:{}; {}:{}:{};",
        size_of_val(item1),size_of_val(&item1),size_of_val(&&item1),
        size_of_val(item2),size_of_val(&item2),size_of_val(&&item2),
        size_of_val(item3),size_of_val(&item3),size_of_val(&&item3)
    );
}

```

### Динамические строки - `String`
Для работы с динамическими строками используется структура `String`. Одним из способов создания экземпляра `String` - вызвать
метод `to_string` у статического литерала. Для добавления символа к динамической строке `String` используйте метод `push`:
```rust
fn main() {
    let mut string: String = "Привет".to_string();
    string.push(',');
    string.push(' ');
    string.push('R');
    string.push('u');
    string.push('s');
    string.push('t');
    string.push('!');
    println!("{}", string);
}
```
[Rust Playground](https://play.rust-lang.org/?gist=e5598cec41a441f77dddc03ce8f49cde&version=stable&mode=debug&edition=2015)

Также как и для вектора `Vec` в динамических строках можно использовать тоже методы, чтобы менять её содержимое:
```rust
fn main() {
    let mut a: String = "Привет".to_string();
    a.remove(0);
    a.insert(0, 'П');
    a.pop();
    a.push('т');
    print!("{}", a);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=5640d7e8a0e25b59bccdb5ffeee68ec2&version=stable&mode=debug&edition=2015)

Рассмотрим пример получения значений ёмкости и длинны строки:
```rust
fn create_empty_stirng() -> String {
    "".to_string()
}
fn add_char(string: &mut String, char_value: char) -> &String {
    string.push(char_value);
    string
}
fn main() {
    let mut s1 = create_empty_stirng();
    add_char(&mut s1, 'e');
    
    let mut s2 = create_empty_stirng();
    add_char(&mut s2, 'è');
    
    let mut s3 = create_empty_stirng();
    add_char(&mut s3, '€');
    
    print!("{} {}; {} {}; {} {};", 
    s1.capacity(), s1.len(), 
    s2.capacity(), s2.len(),
    s3.capacity(), s3.len()
    );
}

```
В этом примере мы приминили свои знания из предыдущий глав  (работа с функциями).

### Способы создания новой строки
В стандартной библиотеке Rust есть несколько способом создать новую строку. 
```rust
fn main() {
    let string1 = String::new();
    let string2 =String::from("");
    let string3 = "".to_string();
    let string4 = "".to_owned();//cloning
    let string5 = format!("");
    println!("{}", string1 == string2);
    println!("{}", string1 == string3);
    println!("{}", string1 == string4);
    println!("{}", string1 == string5);
}

```
#### Способы конвертации статической строки в динамическую
```rust
fn main() {
    let static_string = "Hello!=>";
    let string1 = String::from(static_string);
    let string2 = static_string.to_string();
    let string3 = static_string.to_owned();
    // let _s4 = format!(static_string);
    
    let string5 = format!("{}", static_string);
    print!("({}{}{}{})", string1, string2, string3, string5);
}
```
#### Домашнее задание
Напишите программу, в которой вы покажите варианты объединения статических строк в динамический и комбинации объединения строк.
Используйте макрос `format!`, метод `push_str`.

### Получение значения указателя на String в куче
Для того чтобы получить значение указателя в куче используйте функцию `as_prt`:
```rust
fn main() {
    //let mut s = "".to_string();
    let mut s = vec![];
    for _ in 0..10 {
        println!("{:?} {} {}",
            s.as_ptr(), s.capacity(), s.len());
        s.push(55);
    }
    println!("{:?} {} {}: {:?}",
        s.as_ptr(), s.capacity(), s.len(), s);
}
```
Обратите внимание, что работа с строкой `String` аналогична работе с вектором.




















