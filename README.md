# rust-games
Experimentos com Rust - Como fazer um game

# baralho

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

# loop 

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

# jogo da vida

```
let
    let mut vec = vec![vec!['⬜'; 3]; 3];
    let mut counting:u8 = 1;
