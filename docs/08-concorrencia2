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