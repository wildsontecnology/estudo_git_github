# Meu Laboratório Git

Estou aprendendo **Git** e **GitHub** e utilizando este repositório como laboratório para praticar os principais conceitos e comandos.

## Preparação

Antes de começar, é necessário:

1. Instalar o **Git**
2. Criar uma conta no **GitHub**
3. Criar uma pasta para o repositório local

## Comandos Iniciais

### Iniciar um repositório

```bash
git init
```

Inicializa um novo repositório Git dentro da pasta atual.

### Adicionar arquivos à Staging Area

```bash
git add .
```

Adiciona as alterações e os novos arquivos à **Staging Area**, deixando-os preparados para o próximo commit.

Também é possível adicionar um arquivo específico:

```bash
git add nome-do-arquivo
```

### Criar um commit

```bash
git commit -m "Descrição das alterações realizadas"
```

Registra as alterações que estavam na **Staging Area** no histórico do repositório.

### Vincular o repositório local ao repositório remoto

```bash
git remote add origin <URL_DO_REPOSITORIO>
```

Vincula o repositório local a um repositório remoto, como o GitHub.

Exemplo utilizando HTTPS:

```bash
git remote add origin https://github.com/usuario/repositorio.git
```

Exemplo utilizando SSH:

```bash
git remote add origin git@github.com:usuario/repositorio.git
```

### Enviar alterações para o repositório remoto

#### Primeiro envio

```bash
git push -u origin main
```

Envia a branch `main` para o repositório remoto e estabelece o **upstream** entre a branch local e a branch remota.

#### Próximos envios

Depois que o upstream foi configurado, normalmente é possível utilizar:

```bash
git push
```

## Trabalhando com Branches

Branches permitem desenvolver novas funcionalidades ou alterações de forma isolada, sem modificar diretamente a branch principal.

### Clonar um repositório remoto

```bash
git clone https://github.com/usuario/repositorio.git
```

Clona um repositório remoto para a máquina local.

### Visualizar as branches locais

```bash
git branch
```

Exibe as branches existentes no repositório local.

### Visualizar as branches remotas

```bash
git branch -r
```

Exibe as branches existentes no repositório remoto.

### Criar uma nova branch e mudar para ela

```bash
git switch -c <nome-branch>
```

Cria uma nova branch e muda automaticamente para ela.

Exemplo:

```bash
git switch -c feature/nova-funcionalidade
```

### Publicar a branch no GitHub

```bash
git push -u origin <nome-branch>
```

Envia a nova branch para o repositório remoto e estabelece seu **upstream**.

### Criar um Pull Request

Depois de publicar a branch no GitHub, pode-se criar um **Pull Request (PR)**.

O Pull Request permite que as alterações sejam analisadas antes de serem incorporadas à branch de destino por meio de um **merge**.

Fluxo básico:

```text
Branch de trabalho
       ↓
     commit
       ↓
     push
       ↓
Pull Request
       ↓
     revisão
       ↓
     merge
       ↓
Branch principal
```

### Buscar informações do repositório remoto

```bash
git fetch
```

Busca informações e commits do repositório remoto e atualiza as referências remotas, como:

```text
origin/main
```

O `git fetch` **não integra automaticamente** essas alterações à branch atual.

### Buscar e integrar alterações

```bash
git pull
```

Busca as alterações do repositório remoto e as integra à branch atual, conforme a configuração de `pull`.

De forma simplificada:

```text
git pull = git fetch + integração das alterações
```

## Fluxo Básico do Git

Um fluxo comum para trabalhar com Git é:

```text
Alterar arquivos
      ↓
   git add
      ↓
Staging Area
      ↓
  git commit
      ↓
Repositório local
      ↓
   git push
      ↓
Repositório remoto (GitHub)
```

### Fluxo com Branches

```text
main
 │
 └── feature/nova-funcionalidade
          ↓
       git add
          ↓
       git commit
          ↓
       git push
          ↓
    Pull Request
          ↓
        Merge
          ↓
         main
```

## Resumo dos Principais Comandos

| Comando      | Função                                     |
| ------------ | ------------------------------------------ |
| `git init`   | Inicializa um repositório Git              |
| `git clone`  | Clona um repositório remoto                |
| `git status` | Exibe o estado atual do repositório        |
| `git add`    | Adiciona alterações à Staging Area         |
| `git commit` | Registra alterações no histórico           |
| `git branch` | Lista branches locais                      |
| `git switch` | Troca de branch                            |
| `git remote` | Gerencia conexões com repositórios remotos |
| `git fetch`  | Busca alterações do remoto sem integrá-las |
| `git pull`   | Busca e integra alterações do remoto       |
| `git push`   | Envia commits para o repositório remoto    |

## Objetivo do Laboratório

Utilizar este repositório para praticar:

* Fundamentos do Git
* Repositórios locais e remotos
* Commits
* Staging Area
* Branches
* Pull Requests
* Merge
* `fetch` e `pull`
* Integração entre Git e GitHub
