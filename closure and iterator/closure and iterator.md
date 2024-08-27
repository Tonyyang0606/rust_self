# closure and iterator

### closure

```rust
|param1, param2,...| {
    statements1;
    statement2;
    expression
}
```

example

```rust
fn main() {
   let x = 1;
   let sum = |y| x + y;

    assert_eq!(3, sum(2));
}
```

can be simplified like this if there in only the return expression

```rust
|param1| expression
```



### iterator

create an iterator

```rust
    let v1 = vec![1, 2, 3];

    let v1_iter = v1.iter();
```

**next() method**

```rust
 fn iterator_demonstration() {
        let v1 = vec![1, 2, 3];

        let mut v1_iter = v1.iter();

        assert_eq!(v1_iter.next(), Some(&1));
        assert_eq!(v1_iter.next(), Some(&2));
        assert_eq!(v1_iter.next(), Some(&3));
        assert_eq!(v1_iter.next(), None);
    }
```

next() returns option type

**three ways to turn array into iterator**

- `into_iter` takes away the ownership
- `iter` borrow
- `iter_mut` mutable borrow

**Iterator adaptors**

*Iterator adaptors* are methods defined on the `Iterator` trait that don’t consume the iterator. Instead, they produce different iterators by changing some aspect of the original iterator.

```rust
let v1: Vec<i32> = vec![1, 2, 3];

let v2: Vec<_> = v1.iter().map(|x| x + 1).collect();//map means return a new iterator

assert_eq!(v2, vec![2, 3, 4]);
```