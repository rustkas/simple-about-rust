## Хранилища однотипных данных

 
В стандартной библиотеке Rust существует множество различных хранилищ последовательностей данных. Рассмотрим два наиболее часто используемых.
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

### Инициализация массива
В Rust инициализировать массив можно разными способами:
- можно задать последовательность значений `[1,2,3,4]`, 
- можно задать значение и количество:
```rust
fn main() {
    let array1 = [1, 2, 3, 4];
    let array2 = [1.; 20];
    
    print!("{}, {}", array1.len(), array2.len());
}
```
[Rust Playground](https://play.rust-lang.org/?gist=a35db6b1950b95072da232c4f26359b1&version=stable&mode=debug&edition=2015)

### Многомерные массивы
Многомерные массивы можно задать также, как и одномерные. Разница лишь во вложенности объявления массивов:
```rust
fn main() {
    let mut x = [[[[223; 4]; 1]; 1]; 1];
    x[0][0][0][1] = 56;
    print!("{}", x[0][0][0][0]);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=4408104ca949db098ba94b8bbb79b5da&version=stable&mode=debug&edition=2015)

## Векторы
Основное отличие векторов от массивом - это изменяемость длинны вектора. Она может быть переменой в отличии от массива (это постоянная величина).

Объявление вектора может осуществляться с помощью макроса `vec`. 
```rust
fn main() {
    let x = vec![1, 2, 3, 4];

    for i in 0..x.len() {
        print!("{} ", x[i]);
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=448f76f3812508a110e1d4a9be629f82&version=stable&mode=debug&edition=2015)

Для того, чтобы вносить изменения в содержание вектора используются функции:
```rust
fn main() {
    let mut x = vec![1, 2, 3, 4];
    x.insert(1, 45);
    x.insert(2, 33);
    x.remove(3);
    x.push(200);
    x.pop();
    for i in 0..x.len() {
        print!("{} ", x[i]);
    }
}


```
[Rust Playground](https://play.rust-lang.org/?gist=947ccc2b6fe186c11ea64aabaa62b68b&version=stable&mode=debug&edition=2015)

### Домашнее задание
Пожалуйста, изучите методы вектора и их применение самостоятельно.

## Вывод на консоль векторов и массивов
Возможно, вы уже обратили внимание, что массив и вектор - это уже более сложный тип данных. Следовательно для отображения их содержания нужны более сложные (дополнительные действия). И вы совершенно правы. Для этого в макросе `print`, который мы активно используем в наших примерах необходимо сделать дополнительные пояснения. Необходимо в фигурные скобки добавить текст `:?`. Эта синтаксическая конструкция сообщает макросу, что для отображения данные необходим другой механизм - так называемый механизм отладки - `Debug`.

```rust
fn main() {
    println!("{:?} {:?}", ['1', '2', '3'], vec![54, 45]);
    println!("{:?} {:?}", ["'1'", "'2'", "'3'"], vec![54., 45.]);
    println!("{:?} {:?}", ["'1'", "'2'", "'3'"], vec![true, false]);
}

```
[Rust Playground](https://play.rust-lang.org/?gist=c0e26ef94345fec6e15eb9a33129fee0&version=stable&mode=debug&edition=2015)

## Копирование

При копировании массива нужно, чтобы тип и размерности переменных совпадали.
При копировании вектора, так как его длинна может бить переменной величиной, нужно только чтобы типы данные переменных совпадали.



```rust
fn main() {
    {
        let mut a1 = [48, 566, -72];
        let a2 = [74, 871, 1250];
        println!("{:?} {:?}", a1, a2);
        a1 = a2;
        //println!("{:?} {:?}", a1, a2);
        println!("{:?}", a1);
    }
    {
        let mut a1 = vec![4, 56, -2];
        let a2 = vec![7, 81];
        println!("{:?} {:?}", a1, a2);
        a1 = a2;
        //println!("{:?} {:?}", a1, a2);
        println!("{:?}", a1);
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=559f37eb39f194955e344a78ec65a456&version=stable&mode=debug&edition=2015)

## Домашнее задание
Напишите программы с использованием массивов и векторов. Передавай данные между объектами, меняйте их, добавляйте и удаляйте.


