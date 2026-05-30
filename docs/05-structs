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