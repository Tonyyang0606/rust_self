# Common Collections

### Hash maps

Two ways to create Hash maps (store on heap)

1. use new

   ```rust
   use std::collections::HashMap;
   
   let mut my_gems = HashMap::new();
   my_gems.insert(" red gem", 1);
   my_gems.insert("blue gem", 2);
   my_gems.insert("broken stone", 18);
   ```

   Type: `HashMap<&str,i32>`

 2. collect and iterator

    Vec -> iterator -> collect -> Hash map

    ```rust
    fn main() {
        use std::collections::HashMap;
    
        let teams_list = vec![
            ("CHN".to_string(), 100),
            ("USA".to_string(), 10),
        ];
    
        let teams_map: HashMap<_,_> = teams_list.into_iter().collect();
        
        println!("{:?}",teams_map)
    }
    ```

    

**Adding a Key and Value Only If a Key Isn’t Present**

```rust
    use std::collections::HashMap;

    let mut scores = HashMap::new();
    scores.insert(String::from("Blue"), 10);

    scores.entry(String::from("Yellow")).or_insert(50);
    scores.entry(String::from("Blue")).or_insert(50);

    println!("{scores:?}");
```



**Updating a Value Based on the Old Value**

```rust

use std::collections::HashMap;

// A structure to store the goal details of a team.
struct Team {
    goals_scored: u8,
    goals_conceded: u8,
}

fn build_scores_table(results: String) -> HashMap<String, Team> {
    // The name of the team is the key and its associated struct is the value.
    let mut scores: HashMap<String, Team> = HashMap::new();

    for r in results.lines() {
        let v: Vec<&str> = r.split(',').collect();
        let team_1_name = v[0].to_string();
        let team_1_score: u8 = v[2].parse().unwrap();
        let team_2_name = v[1].to_string();
        let team_2_score: u8 = v[3].parse().unwrap();
        let team_1=scores.entry(team_1_name).or_insert(Team{goals_scored:0,goals_conceded:0});
        team_1.goals_scored+=team_1_score;
        team_1.goals_conceded+=team_2_score;
        let team_2=scores.entry(team_2_name).or_insert(Team{goals_scored:0,goals_conceded:0});
        team_2.goals_scored+=team_2_score;
        team_2.goals_conceded+=team_1_score;
        // TOD: Populate the scores table with details extracted from the
        // current line. Keep in mind that goals scored by team_1
        // will be the number of goals conceded from team_2, and similarly
        // goals scored by team_2 will be the number of goals conceded by
        // team_1.
    }
    scores
}
```

### Vector

one problem that meets in the rustlings

```rust
// options2.rs
//
// Execute `rustlings hint options2` or use the `hint` watch subcommand for a
// hint.



#[cfg(test)]
mod tests {
    #[test]
    fn simple_option() {
        let target = "rustlings";
        let optional_target = Some(target);

        // TODO: Make this an if let statement whose value is "Some" type
      if let Some(word) = optional_target {
            assert_eq!(word, target);
        }
    }

    #[test]
    fn layered_option() {
        let range = 10;
        let mut optional_integers: Vec<Option<i8>> = vec![None];

        for i in 1..(range + 1) {
            optional_integers.push(Some(i));
        }

        let mut cursor = range;

        // TODO: make this a while let statement - remember that vector.pop also
        // adds another layer of Option<T>. You can stack `Option<T>`s into
        // while let and if let.
       while let Some(Some( integer ))= optional_integers.pop() {
            assert_eq!(integer, cursor);
            cursor -= 1;
        }

        assert_eq!(cursor, 0);
    }
}

```

notice that in the Struct [std](https://doc.rust-lang.org/std/index.html)::[vec](https://doc.rust-lang.org/std/vec/index.html)::Vec

`pub fn [pop](&mut self) -> Option<T>`

Removes the last element from a vector and returns it, or [`None`](https://doc.rust-lang.org/std/option/enum.Option.html#variant.None) if it is empty.

##### Examples

```
let mut vec = vec![1, 2, 3];
assert_eq!(vec.pop(), Some(3));
assert_eq!(vec, [1, 2]);
```

it return a option<T>, so integer need to be nested twice

