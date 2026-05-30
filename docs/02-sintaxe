## Sintaxe básica e váriaveis

Go foi projetado para ser simples e legível. Por isso sua sintaxe é limpa, sem muitos símbolos desnecessários. Assim tornando o código fácil de escrever e entender.

### Estrutura de um programa Go

Todo programa Go segue esta estrutura básica:

```go
package main  // (1)

import "fmt"  // (2)

func main() { // (3)
    fmt.Println("Olá, mundo!")
}
```

1. Todo arquivo Go pertence a um **pacote**. O pacote `main` indica que este é o ponto de entrada do programa.
2. `import` carrega pacotes externos. O pacote `fmt` oferece funções de entrada e saída.
3. A função `main()` é obrigatória — é onde a execução começa.

---

### Comentários

```go
// Comentário de uma linha

/*
   Comentário
   de múltiplas linhas
*/
```

---

### Ponto e vírgula

!!! info "Não é necessário!"
    Diferentemente do C ou Java, o Go **não exige ponto e vírgula** ao final das linhas. Já que o compilador os insere automaticamente.

---

### Variáveis

As variáveis são espaços na memória usados para armazenar valores. No Go, toda variável tem um **tipo definido**.

#### Declaração com `var`

A forma mais explícita de declarar uma variável:

```go
var nome string = "Alice"
var idade int = 25
var ativo bool = true
```

O tipo pode ser omitido quando o valor já deixa claro qual é:

```go
var nome = "Alice"   // Go infere que é string
var idade = 25       // Go infere que é int
```

---

#### Declaração curta com `:=`

Dentro das funções, você pode usar a sintaxe curta, que é a mais comum no dia a dia:

```go
func main() {
    nome := "Alice"
    idade := 25
    ativo := true
}
```

!!! warning "Atenção"
    O operador `:=` só pode ser usado **dentro de funções**. Para variáveis no escopo global, você deve usar `var`.

---

#### Declaração múltipla

Você pode declarar várias variáveis de uma vez usando:

```go
var (
    nome   string = "Alice"
    idade  int    = 25
    cidade string = "São Paulo"
)
```

Ou usando a sintaxe curta:

```go
x, y, z := 10, 20, 30
```

---

### Tipos de dados

#### Numéricos

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| `int` | Inteiro (tamanho depende do sistema) | `42` |
| `int8`, `int16`, `int32`, `int64` | Inteiro com tamanho fixo | `int64(1000)` |
| `uint` | Inteiro sem sinal (positivo) | `100` |
| `float32` | Número decimal (precisão simples) | `3.14` |
| `float64` | Número decimal (precisão dupla) | `3.14159265` |

```go
var inteiro int = 42
var decimal float64 = 3.14
var grande int64 = 1000000
```

#### Texto

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| `string` | Cadeia de caracteres | `"Olá"` |
| `rune` | Caractere Unicode (`int32`) | `'A'` |
| `byte` | Byte (`uint8`) | `'x'` |

```go
var saudacao string = "Olá, Go!"
var letra rune = 'A'
```

#### Lógico

| Tipo | Descrição | Valores |
|------|-----------|---------|
| `bool` | Verdadeiro ou falso | `true`, `false` |

```go
var ligado bool = true
var desligado bool = false
```

---

### Valor zero

!!! info "Variáveis sempre têm valor inicial"
    No Go, toda variável declarada sem valor recebe automaticamente o **valor zero** do seu tipo:

| Tipo | Valor zero |
|------|------------|
| `int`, `float64` | `0` |
| `string` | `""` (string vazia) |
| `bool` | `false` |
| ponteiros, slices, maps | `nil` |

```go
var numero int     // vale 0
var texto string   // vale ""
var ativo bool     // vale false
```

---

### Constantes

Constantes são valores que **não podem ser alterados** depois da declaração. Use `const`:

```go
const Pi = 3.14159
const Linguagem = "Go"
const MaxTentativas = 3
```

Ou em bloco:

```go
const (
    StatusOk    = 200
    StatusErro  = 500
    Versao      = "1.0.0"
)
```

!!! tip "Quando usar constantes?"
    Use `const` para valores que nunca mudam: configurações, limites, códigos de status, etc.

---

### Conversão de tipos

O Go **não faz conversão automática** entre tipos. Você precisa converter explicitamente:

```go
var inteiro int = 42
var decimal float64 = float64(inteiro) // converte int → float64

var x float64 = 9.7
var y int = int(x) // converte float64 → int (trunca, vira 9)
```

!!! warning "Cuidado ao truncar"
    Converter `float64` para `int` **remove a parte decimal** sem arredondar.
