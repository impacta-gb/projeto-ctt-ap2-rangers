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
