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

## Structs

## Métodos

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
## Channels

## Gereciamento de pacotes (Go modules)

## Testes automatizados
