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
