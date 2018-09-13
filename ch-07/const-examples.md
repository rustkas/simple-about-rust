```rust
fn main() {
    println!("{}", CONST1);

    {
        println!("{}", CONST1);
        const CONST1: i8 = 1;
    }
}
const CONST1: i8 = 0;
```

```rust
fn main() {
    println!("{}", CONST1);

    {
        println!("{}", CONST1);
        const CONST1: i8 = 1;
    }
}
// const CONST1: char = "'0'";
// const CONST1: &'static str = "'0'";
// const CONST1: str = *"'0'";
// const CONST1: bool = true;
const CONST1: bool = !false;
//const _CONST1: bool = true ^ false;
//const _CONST1: () = ();
const _CONST1: [i8; 1] = [1];
//const _CONST2: Vec<i8> = vec![1]; // - allocatioins are not allowed in constants

```