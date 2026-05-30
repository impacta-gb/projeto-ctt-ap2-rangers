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