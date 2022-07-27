# rust-games
Experimentos com Rust - Como fazer um game

# Introdução

## loop 

Um loop básico de game

```Rust
    let board = criar_tela();
    loop {
        let estado = get_estado(&board);
        mover(&mut board, estado);
        renderizar(&board);
        if gameover {break;}
    };
```

# Exemplos

## baralho

Como sortear e embaralhar uma lista

```Rust
use rand::prelude::*;

let mut cartas: Vec<i32> = (1..= 42).collect();
cartas.shuffle(&mut rand::thread_rng());
println!("{:?}", cartas);

let mao = &cartas[0 .. 4];
println!("{:?}", mao);
```

No primeiro exemplo eu gerei uma lista com z cartas e embaralhei elas.
Em seguida eu escolho n cartas aleatórias, ‖ n <= z

## dando as cartas

```rust
use rand::prelude::*;

fn main() {

    //Cria um baralho de 42 cartas
    let mut baralho: Vec<i32> = (0..56).collect();
    
    //Embaralha
    baralho.shuffle(&mut rand::thread_rng());
    println!("{:?}", baralho);
    
    //Dá as cartas
    let mao = &baralho[0 .. 4];
    println!("{:?}", mao);
    
    //Desenha na tela
    for (i, carta) in baralho.iter().enumerate() {
        desenha( i + 1, (*carta).try_into().unwrap());
    }
}

fn desenha(indice: usize, id: u8) {
    let simbolos = vec!['♣','♠','♦','♥'];
    let simbolo: usize = (id % 4).into();
    let numero: usize = (id % 14).into();
    let temp =  &numero.to_string();
    let carta = match numero {
      0 =>  "A",
      11 => "D",
      12 => "J",
      13 => "K",
      _ => temp
    };
    
    println!("{:2} │ {:2} {}", indice, carta, String::from(simbolos[simbolo]));
    
}
```

## jogo da vida

```
let
    let mut vec = vec![vec!['⬜'; 3]; 3];
    let mut counting:u8 = 1;
