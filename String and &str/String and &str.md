# String and &str

```rust
fn main() {
    let word = String::from("green"); // Try not changing this line :)
    if is_a_color_word(&word) {
        println!("That is a color word I know!");
    } else {
        println!("That is not a color word I know.");
    }
}

fn is_a_color_word(attempt: &str) -> bool {
    attempt == "green" || attempt == "blue" || attempt == "red"
}

```

The function `is_a_color_word`needs a  `&str`, but word is a `String` type. We can use & to do the conversion

***



```rust
fn main() {
// use + to Concatenation string
  let s1 = String::from("tic");
  let s2 = String::from("tac");
  let s3 = String::from("toe");
  let s = s1 + "-" + &s2 + "-" + &s3;

  println!("{},{},{}",s,s2,s3);

}
```

We cannot print s1, because s1's ownership is taken.

***



```rust
fn compose_me(input: &str) -> String {
    // TODO: Add " world!" to the string! There's multiple ways to do this!
    
    let mut result=String::from(" world!");
    result=input.to_string()+&result;//The + operator needs a string type on the left side,needs &str on the // right side
    // result=input+&result cannot compile.  result=input.to_string()+ result cannot compile,too
    result
}
```

***

functions about  &str and String

```rust
fn string_slice(arg: &str) {
    println!("{}", arg);
}
fn string(arg: String) {
    println!("{}", arg);
}

fn main() {
    string_slice("blue");  // &str 
    string("red".to_string());  // String 
    string(String::from("hi"));  // String 
    string("rust is fun!".to_owned());  // String 
    string("nice weather".into());  // String 
    string_slice(&format!("Interpolation {}", "Station"));  // &str 
    string_slice(&String::from("abc")[0..1]);  // &str 
    string_slice("  hello there ".trim());  // &str 
    string("Happy Monday!".to_string().replace("Mon", "Tues"));  // String 
    string("mY sHiFt KeY iS sTiCkY".to_lowercase());  // String 
}

```

