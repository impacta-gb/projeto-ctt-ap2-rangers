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