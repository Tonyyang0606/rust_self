# trait, generics,lifetime

- **`self`**:
  - Refers to the current instance of a type (like a struct or enum) and is used in method definitions to access or modify the instance's data.
  - Example usage: `self.radius`, `&self`, `&mut self`.
- **`Self`**:
  - Refers to the type itself within an implementation block. It's useful for constructors, returning the type, or referencing the type in a generic way.
  - Example usage: `Self::new()`, `Self { radius }`.

### generics in struct

```rust
struct Point<T> {
    x: T,
    y: T,
}
```



### lifetime

**三条消除规则**

I personally think the Chinese summary is very good, so I will put the Chinese here

编译器使用三条消除规则来确定哪些场景不需要显式地去标注生命周期。其中第一条规则应用在输入生命周期上，第二、三条应用在输出生命周期上。若编译器发现三条规则都不适用时，就会报错，提示你需要手动标注生命周期。

1. **每一个引用参数都会获得独自的生命周期**

   例如一个引用参数的函数就有一个生命周期标注: `fn foo<'a>(x: &'a i32)`，两个引用参数的有两个生命周期标注:`fn foo<'a, 'b>(x: &'a i32, y: &'b i32)`, 依此类推。

2. **若只有一个输入生命周期(函数参数中只有一个引用类型)，那么该生命周期会被赋给所有的输出生命周期**，也就是所有返回值的生命周期都等于该输入生命周期

   例如函数 `fn foo(x: &i32) -> &i32`，`x` 参数的生命周期会被自动赋给返回值 `&i32`，因此该函数等同于 `fn foo<'a>(x: &'a i32) -> &'a i32`

3. **若存在多个输入生命周期，且其中一个是 `&self` 或 `&mut self`，则 `&self` 的生命周期被赋给所有的输出生命周期**

   拥有 `&self` 形式的参数，说明该函数是一个 `方法`，该规则让方法的使用便利度大幅提升。