# Module

It is better to use relative paths to call methods in the module, because it can reduce modification to the code

In rust, by default, all types are privatized.

So the following code cannot compile

```rust
mod front_of_house {
    mod hosting {
        fn add_to_waitlist() {}
    }
}

pub fn eat_at_restaurant() {
    // absolute path
    crate::front_of_house::hosting::add_to_waitlist();

    // relative path
    front_of_house::hosting::add_to_waitlist();
}
```

We need to add `pub` to both `mod hosting` and `fn add_to_waitlist()`, like this.

```rust
mod front_of_house {
   pub mod hosting {
       pub fn add_to_waitlist() {}
    }
}

pub fn eat_at_restaurant() {
    crate::front_of_house::hosting::add_to_waitlist();

    front_of_house::hosting::add_to_waitlist();
}
```

