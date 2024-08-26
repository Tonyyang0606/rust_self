# error handling

 `Result` enum is defined as having two variants, `Ok` and `Err`, as follows:

```rust
enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

The `T` and `E` are generic type parameters



**`s.parse()`**:This attempts to parse the string `s` into a specific type (e.g., `i32`, `f64`).

**`unwrap()`**:

The `unwrap()` method is called on a `Result`. If the `Result` is `Ok(T)`, `unwrap()` returns the value `T`. If it’s `Err(E)`, `unwrap()` causes the program to panic and terminate with an error message.



**？**



another kind of main function

```rust


use std::error::Error;
use std::fs::File;

fn main() -> Result<(), Box<dyn Error>> {
    let greeting_file = File::open("hello.txt")?;

    Ok(())
}
```

