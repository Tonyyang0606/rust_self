# match and so on

### match

```rust
match target {
    pattern1 => expression1,
    pattern2 => {
        statement1;
        statement2;
        expression2
    },
    _ => expression3
}

```



the ownership of y moves to p in the match, and point do not implement copy,so we cannot use y after match

```rust
  let y: Option<Point> = Some(Point { x: 100, y: 200 });

    match y {
        Some(p) => println!("Co-ordinates are {},{} ", p.x, p.y),
        _ => panic!("no match!"),
    }
```

