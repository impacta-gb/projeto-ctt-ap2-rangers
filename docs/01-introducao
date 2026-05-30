---
icon: lucide/rocket
---

# Linguagem Go
A linguagem Go, também conhecida como Golang, tem se consolidado como linguagem padrão para sistemas de nuvem e microsserviços de alta escala. Ela foi criada pelo Google para superar a complexidade e a lentidão de linguagens como C++, sendo uma linguagem que prioriza simplicidade, segurança e desempenho.
### Descubra mais sobre a linguagem Golang!

## Instalando a linguagem Go
### Pré-requisitos

!!! info "Antes de começar você precisa ter:"
    - Acesso à internet
    - Permissão de administrador no sistema
    - Terminal (Linux/macOS) ou PowerShell (Windows)

---

### Passo 1 Baixe o instalador

Acesse o site oficial da linguagem e baixe o instalador para o seu sistema:

**[https://go.dev/dl/](https://go.dev/dl/)**

| Sistema   | Arquivo    |
|-----------|------------|
| Windows   | `.msi`     |
| macOS     | `.pkg`     |
| Linux     | `.tar.gz`  |

---

### Passo 2 Instale o Go

=== "Windows"

    1. Execute o arquivo `.msi` baixado
    2. Siga o assistente (Next → Next → Finish)
    3. O Go será instalado em `C:\Program Files\Go`

=== "macOS"

    1. Abra o arquivo `.pkg` baixado
    2. Siga o assistente de instalação
    3. O Go será instalado em `/usr/local/go`

=== "Linux"

    No terminal, execute:

    ```bash
    # Remova versão antiga (se houver)
    sudo rm -rf /usr/local/go

    # Extraia o arquivo (ajuste o nome conforme a versão baixada)
    sudo tar -C /usr/local -xzf go1.22.0.linux-amd64.tar.gz
    ```

---

### Passo 3 Configure o PATH

Para que o terminal reconheça o comando `go`, adicione o Go ao PATH do sistema.

=== "Windows"

    !!! success "Automático"
        O instalador `.msi` configura o PATH automaticamente. Nenhuma ação necessária.

=== "macOS / Linux"

    Abra o arquivo de configuração do seu shell:

    ```bash
    # Para bash
    nano ~/.bashrc

    # Para zsh (padrão no macOS)
    nano ~/.zshrc
    ```

    Adicione a linha ao final do arquivo:

    ```bash
    export PATH=$PATH:/usr/local/go/bin
    ```

    Salve e aplique as mudanças:

    ```bash
    source ~/.bashrc
    # ou
    source ~/.zshrc
    ```

---

### Passo 4 Verifique a instalação

Feche e reabra o terminal, depois execute:

```bash
go version
```

Se a instalação foi bem-sucedida, você verá algo como:

```
go version go1.22.0 linux/amd64
```

---

### Passo 5 Teste com um programa simples

Crie um arquivo chamado `hello.go`:

```go
package main

import "fmt"

func main() {
    fmt.Println("Olá, mundo!")
}
```

Execute o programa:

```bash
go run hello.go
```

Saída esperada é:

```
Olá, mundo!
```

---
### Solução de problemas

!!! warning "`go: command not found`"
    O PATH não foi configurado corretamente. Revise o **Passo 3**.

!!! warning "Versão desatualizada"
    Repita o processo com o instalador mais recente do site oficial.

!!! warning "Permissão negada (Linux)"
    Use `sudo` antes dos comandos de instalação.
