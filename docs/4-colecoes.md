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