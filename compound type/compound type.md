# compound type

### enum

```rust
enum Message {
    // TODO: implement the message variant types based on their usage below
    Move(Point),
    Echo(String),
    ChangeColor(u8,u8,u8),
    Quit,

}

struct Point {
    x: u8,
    y: u8,
}

struct State {
    color: (u8, u8, u8),
    position: Point,
    quit: bool,
    message: String
}

impl State {
    fn change_color(&mut self, color: (u8, u8, u8)) {
        self.color = color;
    }

    fn quit(&mut self) {
        self.quit = true;
    }
    
    fn echo(&mut self, s: String) { self.message = s }
    
    fn move_position(&mut self, p: Point) {
        self.position = p;
    }
    
    fn process(&mut self, message: Message) {
        match message{
            Message::Move(p)=>{self.move_position(p)},
            Message::Echo(s)=>{self.message=s},
            Message::ChangeColor(r,g,b)=>{self.change_color((r,g,b))},
            Message::Quit=>{self.quit()},
        }
        // TODO: create a match expression to process the different message
        // variants
        // Remember: When passing a tuple as a function argument, you'll need
        // extra parentheses: fn function((t, u, p, l, e))
    }

}
```



