## Срез
Срезом является ссылка на последовательность однотипных данных.
```rust
fn main() {
    fn max(arr: &[i16]) -> i16 {
        if arr.len() == 0 {
           return 0;
        }
        let mut max = arr[0];
        for i in 1..arr.len() {
            if arr[i] > max { max = arr[i]; }
        }
        max
    }
    println!("{}", max(&[283, 107, 152, 116, 195, 208, 173, 310]));
    println!("{}", max(&[]));
}
```
[Rust Playground](https://play.rust-lang.org/?gist=4ea3306371e51a7489c974c95f26dede&version=stable&mode=debug&edition=2015)

