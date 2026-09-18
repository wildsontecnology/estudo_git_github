# Meu Laborat�rio Git 
Estou aprendendo Git e GitHub. 

1 - Instalar git

2 - Criar conta no GitHub

3 - Criar pasta do repositório

_________________________________

Comandos iniciais:

a) Iniciar Repositório
    git init

b) Adicionar alterações ou inclusões de arquivos para área de esperado do commit

c) Comitar alterações: 
    git commit -m "Descricao das alteracoes realizadas"

d) Vincular repositório local com o repositório remoto (GitHub)
    git remote add origin <vincular_chave_ssh ou http>

e) Subir alterações para o repositório remoto:
    git push -u origin main (Primeira vez) -> depois: git pus (para as próximas comitações)git branche

_______________________________________________________________________________________________________

Trabalhando com Branches:

-> Comandos:
    a) Clonar repositório remoto: git clone https://github.com/usuario/repositorio.git 
    b) visualiza branches existes a partir do repositório: git branch
    c) visualiza branches vinculadas aos repositórios remotos:  git branch -r
    d) Cria uma nova branch e já muda para ela: git switch -c <nome-branch>
    e) Publica a branch e estabelece seu upstream: git push -u origin <nome-branch>
    f) No github é criado um PR (Pull Request) para que seja analisado e depois aceito seguindo para o merge
    g) Busca informações/commits do remoto e atualiza referências como origin/main, sem integrar essas alterações à branch atual: git fetch
    h) Busca alterações e as integra à branch atual, conforme a configuração de pull: git pull


    

