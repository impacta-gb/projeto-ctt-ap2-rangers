## Estrutura de controles
Estruturas de controle determinam o **fluxo de execução** de um programa. Ou seja, quais instruções serão executadas, em qual ordem e quantas vezes. Ele oferece três estruturas principais: `if`, `for` e `switch`.

### If / Else

O `if` executa um bloco de código apenas se uma condição for verdadeira.

#### Sintaxe básica

```go
idade := 18

if idade >= 18 {
    fmt.Println("Maior de idade")
}
```

!!! info "Sem parênteses"
    No Go, a condição do `if` **não usa parênteses**, diferentemente do C, Java ou JavaScript.

---

#### If / Else

```go
idade := 15

if idade >= 18 {
    fmt.Println("Maior de idade")
} else {
    fmt.Println("Menor de idade")
}
```

---

#### If / Else if / Else

```go
nota := 75

if nota >= 90 {
    fmt.Println("Aprovado com distinção")
} else if nota >= 60 {
    fmt.Println("Aprovado")
} else {
    fmt.Println("Reprovado")
}
```

---

#### If com inicialização

O Go permite declarar uma variável **dentro do próprio `if`**. No entanto ela existirá apenas dentro do bloco:

```go
if x := 10; x > 5 { // (1)
    fmt.Println("x é maior que 5")
}
// x não existe aqui fora
```

1. A parte antes do `;` é a inicialização. A parte depois é a condição.

!!! tip "Quando usar?"
    Muito útil para verificar erros retornados por funções sem poluir o escopo externo.

    ```go
    if err := abrirArquivo("dados.txt"); err != nil {
        fmt.Println("Erro:", err)
    }
    ```

### For

O `for` é a **única estrutura de repetição do Go**, mas é flexível o suficiente para substituir o `while` e o `foreach` de outras linguagens.

#### For tradicional (estilo C)

```go
for i := 0; i < 5; i++ { // (1)
    fmt.Println(i)
}
```

1. Três partes separadas por `;`: **inicialização** → **condição** → **incremento**.

Saída:
```
0
1
2
3
4
```

---

#### For como While

Omitindo a inicialização e o incremento, o `for` se comporta como um `while`:

```go
contador := 0

for contador < 5 {
    fmt.Println(contador)
    contador++
}
```

---

#### Loop infinito

Omitindo tudo, o loop roda para sempre. Por isso é útil em servidores e processos contínuos:

```go
for {
    fmt.Println("Rodando...")
    // use break para sair
}
```

---

#### For com Range

O `range` percorre **slices, arrays, maps e strings** de forma simples:

```go
frutas := []string{"maçã", "banana", "laranja"}

for i, fruta := range frutas { // (1)
    fmt.Println(i, fruta)
}
```

1. `i` é o índice, `fruta` é o valor atual. Ambos podem ser usados dentro do bloco.

Saída:
```
0 maçã
1 banana
2 laranja
```

Se não precisar do índice, use `_` para ignorá-lo:

```go
for _, fruta := range frutas {
    fmt.Println(fruta)
}
```

---

#### Break e Continue

`break` interrompe o loop imediatamente. `continue` pula para a próxima iteração:

```go
for i := 0; i < 10; i++ {
    if i == 3 {
        continue // pula o 3
    }
    if i == 7 {
        break // para no 7
    }
    fmt.Println(i)
}
```

Saída:
```
0
1
2
4
5
6
```

### Switch

O `switch` compara um valor com múltiplos casos, sendo mais limpo que vários `else if` seguidos.

#### Sintaxe básica

```go
dia := "segunda"

switch dia {
case "segunda", "terça", "quarta", "quinta", "sexta":
    fmt.Println("Dia útil")
case "sábado", "domingo":
    fmt.Println("Final de semana")
default:
    fmt.Println("Dia inválido")
}
```

!!! info "Sem `break` necessário"
    No Go, cada `case` **para automaticamente** ao terminar. Ao contrário de C e Java, onde você precisa escrever `break` explicitamente.

---

#### Switch com inicialização

Assim como o `if`, o `switch` aceita uma inicialização antes da condição:

```go
switch hora := time.Now().Hour(); { // (1)
case hora < 12:
    fmt.Println("Bom dia!")
case hora < 18:
    fmt.Println("Boa tarde!")
default:
    fmt.Println("Boa noite!")
}
```

1. `hora` é declarada e usada somente dentro do `switch`.

---

#### Switch sem condição

Quando omitida a condição, o `switch` funciona como uma sequência de `if/else` — avaliando cada `case` como uma expressão booleana:

```go
nota := 85

switch {
case nota >= 90:
    fmt.Println("Excelente")
case nota >= 70:
    fmt.Println("Bom")
case nota >= 50:
    fmt.Println("Regular")
default:
    fmt.Println("Insuficiente")
}
```

---

#### Fallthrough

Se você quiser que a execução **continue para o próximo case**, use `fallthrough`:

```go
x := 1

switch x {
case 1:
    fmt.Println("Um")
    fallthrough
case 2:
    fmt.Println("Dois")
case 3:
    fmt.Println("Três")
}
```

Saída:
```
Um
Dois
```

!!! warning "Use com cautela"
    O `fallthrough` executa o próximo `case` **independente da condição**. Use apenas quando realmente necessário.

### Resumo

| Estrutura | Uso principal |
|-----------|---------------|
| `if / else` | Executar código com base em uma condição |
| `for` | Repetir código (loop, while e foreach em um só) |
| `switch` | Comparar um valor com múltiplos casos |