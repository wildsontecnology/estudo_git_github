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
_______________________________________________________________________________________________

🔐 Criar uma nova SSH para o GitHub no Windows

1. Verificar as chaves existentes

No PowerShell:

Get-ChildItem $env:USERPROFILE\.ssh -Force

Exemplo:

id_ed25519
id_ed25519.pub

A chave antiga deve ser preservada quando não sabemos sua passphrase.

2. Criar uma nova chave SSH

Execute:

ssh-keygen -t ed25519 -C "seu-email"

Quando aparecer:

Enter file in which to save the key:

informe um nome diferente da chave antiga, por exemplo:

C:\Users\SEU_USUARIO\.ssh\id_ed25519_github

Quando aparecer:

Enter passphrase:

Para criar a chave sem passphrase, pressione:

Enter

Depois, em:

Enter same passphrase again:

pressione Enter novamente.

Serão criados:

id_ed25519_github
id_ed25519_github.pub

3. Se a primeira chave nova estiver com problema

Se a nova chave tiver sido criada com uma passphrase que você não
consegue utilizar, exclua somente a nova chave problemática.

Remove-Item "$env:USERPROFILE\.ssh\id_ed25519_github"
Remove-Item "$env:USERPROFILE\.ssh\id_ed25519_github.pub"

Depois confirme:

Get-ChildItem $env:USERPROFILE\.ssh -Force

A chave antiga id_ed25519 deve continuar intacta.

Em seguida, crie novamente a nova chave seguindo o passo 2.

4. Copiar a chave pública

A chave que deve ser cadastrada no GitHub é a pública:

id_ed25519_github.pub

Para visualizar:

Get-Content "$env:USERPROFILE\.ssh\id_ed25519_github.pub"

Ou copiar diretamente para a área de transferência:

Get-Content "$env:USERPROFILE\.ssh\id_ed25519_github.pub" | Set-Clipboard

⚠️ Nunca compartilhe a chave privada id_ed25519_github.

5. Adicionar a chave ao GitHub

No GitHub, acesse:

Settings → SSH and GPG keys → New SSH key

Preencha:

Title:

PC WINDOWS II

Key type:

Authentication Key

Key:

Cole o conteúdo de:

id_ed25519_github.pub

Depois clique em:

Add SSH key

6. Criar o arquivo de configuração SSH

Crie o arquivo:

C:\Users\SEU_USUARIO\.ssh\config

No PowerShell:

notepad $env:USERPROFILE\.ssh\config

Coloque exatamente:

Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_github
    IdentitiesOnly yes

Salve e feche o Bloco de Notas.

⚠️ Atenção ao Windows

O arquivo precisa se chamar:

config

e não:

config.txt

Se o Bloco de Notas criar config.txt, renomeie:

Rename-Item "$env:USERPROFILE\.ssh\config.txt" "config"

7. Conferir o arquivo de configuração

Execute:

Get-Content "$env:USERPROFILE\.ssh\config"

O resultado esperado:

Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_github
    IdentitiesOnly yes

8. Testar a autenticação

Execute:

ssh -T git@github.com

Se estiver tudo correto, deverá aparecer algo semelhante a:

Hi SEU_USUARIO! You've successfully authenticated, but GitHub does not provide shell access.

Esse resultado confirma que o SSH está autenticando no GitHub.

📁 Estrutura final

A pasta .ssh deverá ficar aproximadamente assim:

C:\Users\SEU_USUARIO\.ssh\
│
├── id_ed25519                 ← chave antiga
├── id_ed25519.pub             ← chave pública antiga
│
├── id_ed25519_github          ← NOVA chave privada
├── id_ed25519_github.pub      ← NOVA chave pública
│
├── config                     ← configuração do SSH
├── known_hosts
└── known_hosts.old

🧠 Como funciona

A configuração:

Host github.com
    IdentityFile ~/.ssh/id_ed25519_github
    IdentitiesOnly yes

informa ao SSH:

Quando a conexão for com github.com, utilize especificamente a chave
id_ed25519_github.

Assim, a chave antiga:

id_ed25519

pode permanecer no computador sem interferir na autenticação do GitHub.

📌 Checklist rápido

# 1. Verificar chaves
Get-ChildItem $env:USERPROFILE\.ssh -Force

# 2. Criar nova chave
ssh-keygen -t ed25519 -C "seu-email"

# 3. Copiar chave pública
Get-Content "$env:USERPROFILE\.ssh\id_ed25519_github.pub" | Set-Clipboard

# 4. Criar configuração
notepad $env:USERPROFILE\.ssh\config

# 5. Conferir configuração
Get-Content "$env:USERPROFILE\.ssh\config"

# 6. Testar GitHub
ssh -T git@github.com

🎯 Resultado esperado

Computador
    │
    │ SSH
    ▼
~/.ssh/config
    │
    │ id_ed25519_github
    ▼
GitHub
    │
    │ autenticação
    ▼
Sua conta GitHub

Regra importante: a chave .pub é a chave pública e pode ser
cadastrada no GitHub. A chave sem .pub é privada e deve permanecer
protegida no computador.
  
