---
icon: lucide/rocket
---

# Linguagem Go

### Descubra mais sobre a linguagem Golang!

## Instalando a linguagem Go

* [`zensical new`][new] - Create a new project
* [`zensical serve`][serve] - Start local web server
* [`zensical build`][build] - Build your site

  [new]: https://zensical.org/docs/usage/new/
  [serve]: https://zensical.org/docs/usage/preview/
  [build]: https://zensical.org/docs/usage/build/

## Sintaxe básica

## Váriaveis

## Estrutura de controles
### If
### For
### Switch

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
