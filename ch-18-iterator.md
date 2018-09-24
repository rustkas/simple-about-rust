## Итератор
Для упрощения и удобства в стандартную библиотеку были добавлены *итераторы*. Итераторы помогают перебрать наборы, 
как простых (примитивных данных), так и сложных структур (таких, как unicode characters). Это спецификация - то есть должны
быть соблюдены определенные условия. Одно из них = все итераторы должны иметь метод `next()`.

```rust
fn print_nth_char(s: &str, n: u32) {
    let mut iterator: std::str::Chars = s.chars();
    let n_item = n-1;
    let mut index = 0;
    loop {
        let item: Option<char> = iterator.next();
        match item {
            Some(c) => 
             if n_item == index
            {
               println!("{}: {}", c, c as u32)
            },
            None => {
                break;
            }
        }
        index += 1;
    }
}

fn main() {
    let string = "€èe";
    print_nth_char(string, 1);
    print_nth_char(string, 2);
    print_nth_char(string, 3);
}
```

### Домашнее задание
Попробуйте упростить данное решение

## Использование цикла `for` при работе с итераторами
Предыдущий пример можно упростить.
```rust
fn print_nth_char(s: &str, n: u32) {
    let mut index = 0;
    let target_index = n -1;
    for char_item in s.chars() {
        if target_index == index {
            println!("{}: {}", char_item, char_item as u32);
            break;
        }
        index += 1;
    }
}

fn main() {
    let string = "€èe";
    print_nth_char(string, 1);
    print_nth_char(string, 2);
    print_nth_char(string, 3);
}
```

### Метод `iter()`
Строки, массивы, векторы и срезы имеют метод, для получения итератаора - метод `iter()`:
```rust
fn main() {
    for ref_item in vec!['a', 'b', 'c'].iter() {
        println!("vector. {} ", ref_item);
    }
    // for ref_item in format!("Hello, Rust!").iter() {
    //     println!("string. {} ", ref_item);
    // }
    for ref_item in (&[11u8, 22, 33]).iter() {
        println!("slice. {} ", ref_item);
    }
    for ref_item in [44, 55, 66].iter() {
        println!("array. {} ", ref_item);
    }
    
}
```

Для внесения изменений при итерациях есть метод `iter_mut`:
```rust
fn main() {
    let mut_slice = &mut ['a', 'a', 'a'];
    println!("{:?}", mut_slice);
    {
        let mut_iterator: std::slice::IterMut<char> = mut_slice.iter_mut();

        for ref_item in mut_iterator {
            *ref_item  = (((*ref_item) as u32) as u8) as char;
            
        }
    }
    println!("{:?}", mut_slice);
}

```
### Вспомогательные функции стандартной библиотеки для работы с итераторами
####`filter`
Для получения среза данных удовлетворяющих определённому условию весьма удобно использовать `filter`:

```rust
fn main() {
    {
        let array = [-86, -98, -0, -1, 0, 31];
        for item in array.iter() {
            if *item < 0 {
                print!("{} ", item);
            }
        }
        println!();
    }
    {
        
            let array = [-86, -98, -0, -1, 0, 31];
            for item in array.iter().filter(|x| **x < 0) {
                print!("{} ", item);
            }
       
    }
}

```
Обратити внимание, что аргуметов функции `filter` является анонимная функция. Такой способ использования анонимных функций 
поведение множеству весьма распространёт в стандартной библиотеке. 
В данном примере в анонимной функции используется два символа `*` (сначала получаем доступ к последовательности, потом к значению (которое, последовательно, передаётся в анонимную функцию)).

