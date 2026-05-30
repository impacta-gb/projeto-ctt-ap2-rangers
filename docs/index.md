---
icon: lucide/rocket
---

# Documentação Técnica: Linguagem Go (Golang)

Bem-vindo ao repositório de documentação oficial do Roadmap de Go. Este espaço foi projetado para cobrir desde os conceitos fundamentais de sintaxe até tópicos avançados de engenharia de software, como concorrência e testes automatizados.

---

## 🗺️ Estrutura do Roadmap

Navega pelos módulos utilizando o menu lateral para explorar os seguintes tópicos:

1. **Introdução ao Go** — Apresentação da linguagem, instalação e configuração do ambiente (`PATH`).
2. **Sintaxe Básica e Variáveis** — Estrutura de um programa, tipos de dados e declarações.
3. **Estruturas de Controle** — Condicionais (`if/else`) e o loop universal (`for`).
4. **Arrays, Slices e Maps** — Gestão de coleções de dados dinâmicas e o algoritmo Swiss Tables.
5. **Structs e Métodos** — Programação baseada em composição e interfaces implícitas.
6. **Tratamento de Erros** — O modelo explícito do Go com valores de erro e o operador `%w`.
7. **Concorrência I: Goroutines** — Threads lógicas ultraleves e o modelo M:N Scheduler.
8. **Concorrência II: Channels** — Sincronização avançada, buffers e proteção de memória com `sync`.
9. **Gerenciamento de Pacotes** — Inicialização e controlo de dependências via Go Modules (`go.mod`).
10. **Testes Automatizados e Benchmarks** — Testes unitários, fuzzing e análise de performance com `pprof`.

---

## 🛠️ Ferramentas Utilizadas

* **Linguagem Base:** Go (foco nas especificações das versões recentes como Go 1.24 e Go 1.26).
* **Gerador de Site:** [Zensical](https://zensical.org/) (compilação de Markdown para HTML estático).
* **Hospedagem:** GitHub Pages (implantado automaticamente via GitHub Actions através do fluxo definido em `docs.yml`).