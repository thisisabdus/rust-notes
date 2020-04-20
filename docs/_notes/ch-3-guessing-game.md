---
title: Guessing Game
date: 2020-04-20 10:51:15.518646319 +0530
---

# Guessing Game

```rs
use rand::Rng;
use std::cmp::Ordering;
use std::io;

fn main() {
    println!("Guess the Number!!");

    loop {
        println!("Please input your guess");

        let mut guess = String::new();
        let secret_number = rand::thread_rng().gen_range(1, 200);

        io::stdin()
            .read_line(&mut guess)
            .expect("Faild to Read Line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => {
                println!("Invalid Input.");
                continue;
            }
        };

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too Small!"),
            Ordering::Greater => println!("Too Big!"),
            Ordering::Equal => {
                println!("You win!");
                break;
            }
        }
    }
}
```

## Explanation

### 1. The `use` statement

```rs
use rand::Rng;
use std::cmp::Ordering;
use std::io;
```