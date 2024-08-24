# References and Borrowing

When we need to pass a mutable reference to a function, we need to add `mut`.

传入可变引用，一定要加上`mut`关键字

```rust
fn main() {
    let mut vec0 = Vec::new();

    fill_vec(&mut vec0);
	//please notice that it is&mut vec0，cannot use &vec0
    println!("{} has length {}, with contents: `{:?}`", "vec0", vec0.len(), vec0);
    
    vec0.push(88);

    println!("{} has length {}, with contents `{:?}`", "vec1", vec0.len(), vec0);
}

fn fill_vec(vec: &mut Vec<i32>)  {
    vec.push(22);
    vec.push(44);
    vec.push(66);
}

```

