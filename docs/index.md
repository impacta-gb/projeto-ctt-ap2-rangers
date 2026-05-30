---
icon: lucide/rocket
---

# Linguagem Go
A linguagem Go, também conhecida como Golang, tem se consolidado como linguagem padrão para sistemas de nuvem e microsserviços de alta escala. Ela foi criada pelo Google para superar a complexidade e a lentidão de linguagens como C++, sendo uma linguagem que prioriza simplicidade, segurança e desempenho.
### Descubra mais sobre a linguagem Golang!

## Instalando a linguagem Go
### Pré-requisitos

!!! info "Antes de começar você precisa ter:"
    - Acesso à internet
    - Permissão de administrador no sistema
    - Terminal (Linux/macOS) ou PowerShell (Windows)

---

### Passo 1 — Baixe o instalador

Acesse o site oficial da linguagem e baixe o instalador para o seu sistema:

**[https://go.dev/dl/](https://go.dev/dl/)**

| Sistema   | Arquivo    |
|-----------|------------|
| Windows   | `.msi`     |
| macOS     | `.pkg`     |
| Linux     | `.tar.gz`  |

---

### Passo 2 — Instale o Go

=== "Windows"

    1. Execute o arquivo `.msi` baixado
    2. Siga o assistente (Next → Next → Finish)
    3. O Go será instalado em `C:\Program Files\Go`

=== "macOS"

    1. Abra o arquivo `.pkg` baixado
    2. Siga o assistente de instalação
    3. O Go será instalado em `/usr/local/go`

=== "Linux"

    No terminal, execute:

    ```bash
    # Remova versão antiga (se houver)
    sudo rm -rf /usr/local/go

    # Extraia o arquivo (ajuste o nome conforme a versão baixada)
    sudo tar -C /usr/local -xzf go1.22.0.linux-amd64.tar.gz
    ```

---

### Passo 3 — Configure o PATH

Para que o terminal reconheça o comando `go`, adicione o Go ao PATH do sistema.

=== "Windows"

    !!! success "Automático"
        O instalador `.msi` configura o PATH automaticamente. Nenhuma ação necessária.

=== "macOS / Linux"

    Abra o arquivo de configuração do seu shell:

    ```bash
    # Para bash
    nano ~/.bashrc

    # Para zsh (padrão no macOS)
    nano ~/.zshrc
    ```

    Adicione a linha ao final do arquivo:

    ```bash
    export PATH=$PATH:/usr/local/go/bin
    ```

    Salve e aplique as mudanças:

    ```bash
    source ~/.bashrc
    # ou
    source ~/.zshrc
    ```

---

### Passo 4 — Verifique a instalação

Feche e reabra o terminal, depois execute:

```bash
go version
```

Se a instalação foi bem-sucedida, você verá algo como:

```
go version go1.22.0 linux/amd64
```

---

### Passo 5 — Teste com um programa simples

Crie um arquivo chamado `hello.go`:

```go
package main

import "fmt"

func main() {
    fmt.Println("Olá, mundo!")
}
```

Execute o programa:

```bash
go run hello.go
```

Saída esperada é:

```
Olá, mundo!
```

---
### Solução de problemas

!!! warning "`go: command not found`"
    O PATH não foi configurado corretamente. Revise o **Passo 3**.

!!! warning "Versão desatualizada"
    Repita o processo com o instalador mais recente do site oficial.

!!! warning "Permissão negada (Linux)"
    Use `sudo` antes dos comandos de instalação.

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

## Arrays, Slices e Maps

Para guardar grupos de informações, o Go usa três estruturas fundamentais: Arrays, Slices e Maps.

| Estrutura | Como funciona por dentro | Por que é bom? |
| :--- | :--- | :--- |
| **Array** | Lista com tamanho que nunca muda  |Muito rápido, mas pouco flexível. |
| **Slice** | Uma visão dinâmica de um array  | Fácil de passar para funções sem gastar memória. |
| **Map (Novo)** | Baseado em Swiss Tables e grupos de 16  | A busca é extremamente veloz e gasta menos CPU. |

---

### Arrays vs. Slices (Arrays Dinâmicos)

Os Arrays têm tamanho fixo e são pouco usados no dia a dia. O que usamos mesmo são os **Slices**, que funcionam como listas que crescem sozinhas conforme você adiciona itens. Por trás das câmeras, um Slice é apenas uma "janela" para un Array real, guardando o endereço dos dados, o tamanho atual e a capacidade total.

```go
package main

import "fmt"

func main() {
    // Criando um Slice dinâmico
    numeros := []int{1, 2, 3}
    numeros = append(numeros, 4)
    fmt.Println(numeros)
}
```
### Maps (Chave e Valor)
```go
capital := make(map[string]string)
capital["SP"] = "São Paulo"
capital["RJ"] = "Rio de Janeiro"
```

## Structs e Métodos

O Go não usa "classes" nem herança tradicional como o Java ou C++. Em vez disso, adotamos uma abordagem baseada em composição e estruturas limpas.

| Conceito | Como funciona | Diferencial do Go |
| :--- | :--- | :--- |
| **Structs** | Agrupam diferentes variáveis  | Não têm herança chata, só composição. |
| **Interfaces** | Definem o que um tipo deve saber fazer  | O Go descobre sozinho se o tipo obedece à regra de forma implícita. |
| **Métodos** | Funções grudadas em uma struct | Podem alterar os dados se usarem ponteiros. |

---

### Exemplo de Struct e Métodos

Usamos structs (estruturas) para agrupar dados e métodos para dar comportamento a esses dados. O Go prefere a **composição** (onde monta objetos complexos juntando peças menores) em vez de criar longas linhagens de herança que costumam dar problemas no futuro

```go
package main

import "fmt"

// Aluno agrupa diferentes variáveis relacionadas
type Aluno struct {
    Nome  string
    Idade int
}

// Exemplo de método ligado à struct Aluno
func (a Aluno) Saudar() {
    fmt.Printf("Olá, meu nome é %s\n", a.Nome)
}

func main() {
    a := Aluno{Nome: "Thais", Idade: 21}
    a.Saudar()
}
```
## Tratamento de Erros (Error Handling)

No Go, os erros não são "exceções" (`try/catch`) que interrompem o programa do nada. Eles são tratados como valores comuns que a função devolve para você conferir. Isso torna o código previsível, pois você sabe sempre onde as falhas podem acontecer.

| Ferramenta | O que faz | Por que usar? |
| :--- | :--- | :--- |
| **errors.Is** | Compara um erro com um valor conhecido  | Bom para saber se o arquivo não existe. |
| **errors.As** | Tenta converter o erro para um tipo específico  | Usa reflexão, o que o torna um pouco lento. |
| **errors.AsType** | Versão moderna (1.26) para converter erros  | É **10 vezes mais rápida** que a anterior. |
| **fmt.Errorf** | Cria e embrulha erros com contexto  | Ajuda a entender onde a falha começou usando `%w`. |

---

### Padrão de Tratamento de Erros

Se algo correu mal, a função te entrega o erro e você decide o que fazer na hora. Veja o padrão mais utilizado no ecossistema Go:

```go
package main

import (
    "fmt"
    "log"
)

func FazerCalculo() (int, error) {
    // Exemplo de retorno de erro comum
    return 0, fmt.Errorf("falha na conexão")
}

func main() {
    resultado, err := FazerCalculo()
    if err != nil {
        log.Println("Erro ao calcular:", err)
        return
    }
    
    fmt.Println("Sucesso:", resultado)
}
```

## Concorrência I: Goroutines

A concorrência nativa e eficiente é um dos pilares mais fortes da linguagem Go, sendo o principal motivo de sua adoção em massa no desenvolvimento de microsserviços modernos que processam milhões de requisições paralelas com latência mínima.

| Mecanismo de Execução | Como funciona por baixo dos panos | Modelo de Alocação de Memória |
| :--- | :--- | :--- |
| **Goroutine** | Linhas de execução lógicas gerenciadas pelo runtime do Go | Inicializam com apenas 2KB de pilha (stack) que cresce e encolhe sob demanda. |
| **Threads do S.O.** | Unidades de execução pesadas gerenciadas pelo Kernel | Fixas e custosas, alocando geralmente de 1MB a 2MB fixos por thread. |

---

### Modelo de Concorrência e Goroutines

Diferente de linguagens tradicionais (como Java ou C++) que mapeiam cada tarefa diretamente para uma Thread pesada do sistema operacional, o Go adota o modelo **M:N Scheduler**. O próprio ecossistema de execução da linguagem multiplexa milhares de Goroutines em cima de poucas threads reais do processador.

```go
package main

import (
    "fmt"
    "time"
)

func exibirMensagem() {
    fmt.Println("Executando de dentro de uma Goroutine assíncrona!")
}

func main() {
    // A palavra-chave 'go' dispara a função em uma thread lógica paralela
    go exibirMensagem()
    
    // Pequena pausa apenas para dar tempo do runtime processar a Goroutine
    time.Sleep(100 * time.Millisecond)
    fmt.Println("Função Main finalizada.")
}
```

## Concorrência II: Channels

Quando evoluímos para cenários de alta complexidade, o tráfego simples de mensagens síncronas precisa de ferramentas adicionais. O Go disponibiliza canais com memória temporária e primitivos de hardware para evitar condições de corrida (*Data Races*).

| Ferramenta Avançada | Mecanismo Técnico | Cenário Ideal de Aplicação |
| :--- | :--- | :--- |
| **Buffered Channels** | Canais com um espaço interno de armazenamento | Controle de fluxo, limitação de taxa (Rate Limiting) e filas de tarefas. |
| **sync.WaitGroup** | Contador seguro para sincronização de fluxos | Aguardar a conclusão em lote de várias Goroutines órfãs. |
| **sync.Mutex** | Trava binária de exclusão mútua de memória | Proteger estruturas compartilhadas (ex: Mapas) contra escrita simultânea. |

---

### Canais com Buffer (Buffered Channels)

Um canal com buffer permite o envio de um número determinado de dados sem bloquear a Goroutine remetente, funcionando como uma fila assíncrona temporária.

```go
package main

import "fmt"

func main() {
    // Canal com capacidade para 2 mensagens antes de bloquear
    canalBuffer := make(chan int, 2)
    
    canalBuffer <- 10
    canalBuffer <- 20 // Não bloqueia a linha de execução
    
    fmt.Println(<-canalBuffer)
    fmt.Println(<-canalBuffer)
}
```
## Gereciamento de pacotes (Go modules)

O Go organiza o código de forma modular e limpa. Todo arquivo fonte obrigatoriamente pertence a um pacote (diretório), e o sistema oficial e descentralizado para controle de dependências externas é o **Go Modules** (introduzido através do arquivo `go.mod`), abolindo antigos padrões complexos como o `GOPATH`.

| Comando no Console | Função Principal no Projeto | Objetivo de Engenharia |
| :--- | :--- | :--- |
| **go mod init** | Instancia as configurações básicas do módulo | Define o caminho oficial do módulo e a versão base do Go. |
| **go mod tidy** | Varre o código, baixa importações e limpa órfãs | Remove bibliotecas que não estão sendo usadas, mantendo o build leve. |
| **go build** | Compila todos os pacotes em um arquivo único | Cria um binário estático isolado e pronto para deploy sem dependências externas. |

---

### Inicializando um Projeto Técnico

Para criar um novo módulo no seu terminal de desenvolvimento local e garantir que o compilador rastreie corretamente suas pastas internas, execute os seguintes passos estruturais:

```bash
# Inicializa o módulo com o namespace ou repositório do seu projeto
go mod init meu-projeto-go

# Faz a varredura automática do código para puxar dependências reais
go mod tidy
```

## Testes automatizados

O Go foi planejado para possuir um ecossistema autossuficiente e robusto de testes integrado nativamente na ferramenta padrão de linha de comando. Não há necessidade de instalar frameworks ou bibliotecas de terceiros para realizar validações unitárias simples, monitorar performance ou injetar estresse algorítmico.

| Ferramenta / Função | Alvo de Validação Técnica | Diferencial Estrutural |
| :--- | :--- | :--- |
| **go test** | Roda os testes unitários tradicionais da aplicação | Execução ultra-rápida nativa e paralela. |
| **go test -fuzz** | Realiza testes de estresse estocásticos aleatórios | Injeta entradas caóticas para encontrar bugs ocultos. |
| **pprof** | Realiza a coleta de perfis de desempenho | Mapeia gargalos de memória e CPU via interface gráfica. |
| **testing/cryptotest** | Valida códigos e algoritmos de segurança | Permite criar testes determinísticos em fluxos de criptografia. |

---

### Estrutura Prática de um Teste Unitário

Para que o compilador do Go reconheça as suas rotinas de teste, duas regras fundamentais de nomenclatura devem ser seguidas à risca:
1. O arquivo deve terminar obrigatoriamente com o sufixo `_test.go`.
2. As funções de teste devem começar com a palavra `Test` maiúscula e receber o ponteiro `(t *testing.T)`.

```go
package calculadora

import "testing"

// Função simples a ser validada
func Soma(a, b int) int {
    return a + b
}

// TestSoma valida o comportamento da função Soma
func TestSoma(t *testing.T) {
    resultado := Soma(2, 3)
    esperado := 5
    
    if resultado != esperado {
        t.Errorf("Validação inválida! Obteve %d, mas esperava %d", resultado, esperado)
    }
}
```
