## Типаж
*Типажём* называют контейнер, в котором находятся описания функций. Эти функции могут быть реализованы для любых типов данных. 
Эта реализация должна быть соответствующим образом описана.

Пример:
```rust
trait MakesSquareRoot {
    fn sq_root(self) -> Self;
}
impl MakesSquareRoot for f32 {
    fn sq_root(self) -> Self {
        f32::sqrt(self)
    }
}
impl MakesSquareRoot for f64 {
    fn sq_root(self) -> Self {
        f64::sqrt(self)
    }
}
fn quartic_root<Number>(x: Number) -> Number
where
    Number: MakesSquareRoot,
{
    x.sq_root().sq_root()
}

fn main() {
    print!("{} {} {}", quartic_root(1000f64), quartic_root(1000f32));
}

```
Обратите внимание, на синтаксис описания функции `quartic_root`.В ней есть описание параметров и ограничений. В частности тут указано,
что тип `Number` должен обязательно реализовать типаж HasSquareRoot.

### Домашнее задание
Попробуйте видоизменить пример и внесите в него ошибки, доказывающее вышеизложенное. Постарайтесь преодолеть ограничения входных данных
и добавьте реализации типажа для известных вам типов данных.

Например:
```rust
impl HasSquareRoot for i32 {
    fn sq_root(self) -> Self {
       (self as f64).sqrt() as i32
    }
}
```
### Реализация нескольких типажей
Для реализации нескольких типажей в описании `where` нужно написать наименования типажей, объединив названия знаком `+`.
```rust

fn main() {
    trait HasSquareRoot {
        fn sqrt(self) -> Self;
    }
    impl HasSquareRoot for f32 {
        fn sqrt(self) -> Self { f32::sqrt(self) }
    }
    impl HasSquareRoot for f64 {
        fn sqrt(self) -> Self { f64::sqrt(self) }
    }
    trait HasAbsoluteValue {
        fn abs(self) -> Self;
    }
    impl HasAbsoluteValue for f32 {
        fn abs(self) -> Self { f32::abs(self) }
    }
    impl HasAbsoluteValue for f64 {
        fn abs(self) -> Self { f64::abs(self) }
    }
    fn abs_quartic_root<Number>(x: Number) -> Number
    where Number: HasSquareRoot + HasAbsoluteValue {
        x.abs().sqrt().sqrt()
    }
    print!("{} {}",
        abs_quartic_root(-100f64),
        abs_quartic_root(-100f32));
}

```
Обратите внимание на строчку `where Number: HasSquareRoot + HasAbsoluteValue {`.

### Методы
Весьма интересно и можно сказать необычно реализована концепция добавления функциональности (методов).
Например, мы хотим увеличивать на 10 число, вызвав метод. Для этого нам понадобиться написать достаточно много кода - 
написать типаж, реализовать метод. Но, возможно, это всё-таки не так уже важно, если всё-таки это нужно.
```rust
fn main() {
    trait CanBeX10 {
        fn multiple_to_ten(self) -> Self;
    }
    impl CanBeX10 for i32 {
        fn multiple_to_ten(self) -> Self{
        // fn multiple_to_ten(self) -> i32 {
        // fn multiple_to_ten(self: Self) -> i32 {
        // fn multiple_to_ten(self: i32) -> i32 {
            self *10
        }
    }

    print!("{}", 7i32.multiple_to_ten());
}
```

#### Домашнее задание 
Придумайте, как можно испортить работу этого кода. Приведите ещё пять вариантов реализации метода `multiple_to_ten`.





