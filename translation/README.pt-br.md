<img
  src="/img/git.png"
  width="70"
  align="right"
/>
# Git Comandos Úteis

Voltar para versão em [Inglês ](/README.md)


## Sobre

Começou a usar Git recentemente? Esse documento deve lhe dar os principais comandos para comecar a usar o Git de uma forma básica  e simples. Caso não encontre algum comando que o julgue importante para o documento, não hesite, basta apenas [contribuir](#contribuir).


## Sumário

* [Instalando o Git](#instalando-o-git)
* [Configurando o Git](#configurando-o-git)
* [Aplicando cores ao Git](#aplicando-cores-ao-git)
* [Inicializando um repositorio em diretorio existente](#inicializando-um-repositorio-em-diretorio-existente)
* [Checkando o status dos arquivos](#checkando-o-status-dos-arquivos)
* [Staging Arquivos](#staging-arquivos)
* [Stashing Arquivos](#stashing-arquivos)
* [Commitando Arquivos](#commitando-arquivos)
* [Branch e Merge](#branch-e-merge)
* [Redefinindo](#redefinindo)
* [Git remote](#git-remote)
* [Git grep](#git-grep)
* [Git blame](#git-blame)
* [Git log](#git-log)
* [Checkando o que estou commitando](#checkando-o-que-estou-commitando)
* [Comandos úteis](#comandos-úteis)
* [Alias úteis](#alias-úteis)
* [Contribuição](#contribuir)

#### Git

Git e um sistema de controle de versão distribuído, muito fácil de aprender e super rápido!

#### Instalando o Git

Existem algumas maneiras diferentes de instalar git (da fonte ou pelo Linux) mas o objetivo desta página é se concentrar em comandos do git, por isso estou indo supor que você está instalando o git em um Mac.

Para ver outras maneiras de instalar o Git, visite a [Git site oficial](http://git-scm.com/book/en/v2/Getting-Started-About-Version-Control).

Clique [aqui](http://git-scm.com/download/mac) para baixar e instalar o Git.

#### Configurando o Git

```sh
$ git config --global user.name "User Name"

$ git config --global user.email "email"

```

#### Aplicando cores ao Git

```sh
$ git config --global color.ui true
```

#### Inicializando um repositorio em diretorio existente

Se você está começando a rastrear um projeto existente no Git, você precisa ir ao diretório e tipo do projeto:

```sh
$ git init
```

Isso cria um novo subdiretório .git que contém todos os seus arquivos do repositório necessárias - um esqueleto repositório Git. Neste ponto, não há nada em seu projeto que seja rastreado ainda.

Para comecar o versionamento nos arquivos existentes, você deve começar por rastrear os arquivos e fazer um commit inicial. Para conseguir isso, você deve começar com alguns `$ git add` que especifica os arquivos que você deseja acompanhar seguido por uma confirmação.

```sh
$ git add <file>
$ git add README
$ git commit -m 'Versão inicial do projeto'
```


#### Checkando o status dos arquivos


A principal ferramenta que você usa para determinar quais arquivos estão em qual estado é o comando `$ git status`. Se você executar esse comando diretamente após um clone, você deve ver algo como isto:

```sh
$ git status
# On branch master
nothing to commit (working directory clean)
```

Se você adicionar um novo arquivo ao seu projeto, e o mesmo não existia antes, quando você executar o comando `$ git status` você deve ver seu arquivos que não estão adicionados como este:

```sh
$ git status
# On branch master
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#   README
# nothing added to commit but untracked files present (use "git add" to track)
```

#### Staging Arquivos

Depois de inicializar um repositório git no diretório escolhido, todos os arquivos serão agora rastreados. Quaisquer alterações feitas a qualquer arquivo será exibido após o comando `$ git status`, sendo esses or arquivos que ainda não estão commitados.


Para stagear alteracoes para inserí-la em um commit, é necessário adicionar os arquivos. Em outras palavras, stagear arquivos.

Para 'Stagear' mudanças para commit você precisa adicionar o(s) arquivo(s) - ou em outras palavras, arquivo(s) estágio.

Para adicionar os arquivos na Stage Area, basta adicionar eles.

```sh
# Adicionando arquivo pelo nome
$ git add filename

# Adicionando todos os arquivos modificados
$ git add -A

# Adicionando todos os arquivos e diretorios modificados
$ git add .

# Seleciona o que muda para adicionar(essa vontade tem por todas as alterações e você pode 'Y' ou 'N' as mudanças)
$ git add -p
```

#### Stashing Arquivos
Git Stash é um comando muito útil, onde git vai "esconder" as mudanças em um diretório sujo - mas não se preocupe você pode re-aplicá-las mais tarde. O comando vai salvar suas alterações locais longe e reverter o diretório de trabalho para coincidir com o commit HEAD.

```sh
# Stash alteracoes locais
$ git stash

# Stash alteracoes locais com uma mensagem
$ git stash save "this is your custom message"

# Re-aplicar as alteracoes que foram salvar em um stash anterior
$ git stash apply

# Re-aplicar as alterações que você salvou em um determinado número do stash
$ git stash apply stash@{stash_number}

# Apagar qualquer stash pelo seu numero
$ git stash drop stash@{0}

# Aplicar o stash e logo em seguida retirá-lo do seu stack
$ git stash pop

# 'Release' um estoque especial da sua lista de stash`s
$ git stash pop stash@{stash_number}

# Listar todos os stash`s
$ git stash list

# Mostrar as últimas mudanças nos stash`s
$ git stash show

# Veja detalhes [diff] de um determinado número de stash
$ git diff stash@{0}
```

#### Commitando Arquivos

Depois de adicionar/staging os arquivos, o próximo passo é commitar os arquivos que estão na Stage:

```sh
# Commitar arquivos da stage
$ git commit -m 'mensagem do commit'

# Adicionar arquivo e commitar
$ git commit nomedoarquivo -m 'mesagem do commit'

# Adicionar arquivos na stage e comitar
$ git commit -am 'mensagem do commit'

# Alterar um Commit
$ git commit --amend 'mensagem do novo commit' ou nenhuma mensagem para manter a mensagem anterior

# Squashing commits juntos
$ git rebase -i
# Isto lhe dará uma interface em seu editor de núcleo:
# Comandos:
#  p, pick = use commit
#  r, reword = use commit, mas editar a mensagem do commit
#  e, edit = use commit, mas parar para alterar
#  s, squash = use commit, mas se juntar ao commit anterior
#  f, fixup = como o "squash", mas descartar esta mensagem de log no commit
#  x, exec = usar comando (o resto da linha) usando shell
```

#### Branch e Merge

```sh
# Criando um branch local
$ git checkout -b nomedobranch

# Alternar entre dois branchs (na verdade, isso iria funcionar no terminal, bem como para alternar entre dois diretórios - $ cd -)
$ git checkout nomedobranch

# Mandando um branch local para um branch remoto
$ git push -u origin nomedobranch

# Deletando um branch local - este não vai deixar você apagar um ramo que ainda não foi mesclado
$ git branch -d nomedobranch

# Deletando um branch local - Isto irá apagar uma branch, mesmo que não tenha sido dados um merge
$ git branch -D nomedobranch

# Remova qualquer refs remote que você tem localmente que foram removidos de seu controle remoto (você pode substituir <origem> para qualquer ramo remoto)
$ git remote prune origin

# Ver todos os branch's, incluindo os locias e branch's remotos
$ git branch -a

# Vendo todos os branch's que foram incorporadas em seu branch atual, incluindo local e remoto
$ git branch -a --merged

# Ver todos os branch's que ainda nao foram criados merge, incluindo locais e remotos
$ git branch -a --no-merged

# Ver o branch atual
$ git branch

# Ver branch's remotos
$ git branch -r

# Rebase master branch na branch local
$ git rebase origin/master

# Mandando para remote a versao mais nova da branch depois de ter feito o rebase de master na branch
$ git push origin +branchname
```

#### Buscar e verificar branch's remotos

```sh
# Este irá buscar todas as filiais remotas para você.
$ git fetch origin

# Com os branch's remotos na mão, agora você precisa para verificar o branch que você está interessado, dando-lhe uma cópia de trabalho local:
$ git checkout -b test origin/test

# Deletando um branch remoto
$ git branch -rd origin/nomedobranch
$ git push origin --delete nomedobranch  or  $ git push origin:nomedobranch
```

#### Mesclando branch ao master

```sh
# Primeiro check o branch trunk/master
$ git checkout trunk/master

# Agora merge o novo branch para trunk/master
$ git merge nomedobranch

# Para cancelar o merge
$ git merge --abort
```

#### Atualizando repositório local com mudanças de um repositório do Github

```sh
$ git pull origin master
```

#### Acompanhando branch existente

```sh
$ git branch --set-upstream-to=origin/foo foo
```

#### Redefinindo

```sh
# Mistura a HEAD com um sha
# Isso permite que você faça coisas como dividir um commit
$ git reset --mixed [sha]

# Upstream master
$ git reset HEAD origin/master -- nomedoarquivo

# A versão mais recente do commit
$ git reset HEAD -- nomedoarquivo

# A versão mais recente antes do commit
$ git reset HEAD^ -- nomedoarquivo

# Mover a HEAD para um commit específico
$ git reset --hard sha

# Redefinir a área de teste e o diretório de trabalho para coincidir com a mais recente confirmação. Além das mudanças unstaging, a flag --hard diz Git para substituir todas as alterações no diretório de trabalho também.
$ git reset --hard
```


#### Git remote

```sh
# Mostrar onde "origin" está apontando para e também branch de rastos
$ git remote show origin

# Mostrar onde está apontando para "origin"
$ git remote -v

# Alterar a URL do branch remoto "origin"
$ git remote set-url origin https://github.com/user/repo.git

# Adicionar uma nova origem
# Geralmente utilizada para 'rebase' de forks
$ git remote add [NOME] https://github.com/user/fork-repo.git
```

#### Git grep

```sh
# 'Buscas' por partes de uma string em um diretorio
$ git grep 'algumacoisa'

# 'Buscas' por partes de uma string em um diretorio e as cópias -n fora os números de linha onde git encontrou
$ git grep -n 'alguma coisa'

# 'Buscas' por partes de uma string em um contexto (algumas linhas antes e após o termo algumas grepped)
$ git grep -C<número de linhas> 'algumacoisa'

# 'Buscas' por partes de uma string e também mostra linhas ANTES do termo grepped
$ git grep -B<número de linhas> 'algumacoisa'

# 'Buscas' por partes de uma string e também mostra linhas DEPOIS do termo grepped
$ git grep -A<núumero de linhas> 'algumacoisa'
```

#### Git blame

```sh
# Mostra o histórico de alterações do arquivo com o nome do autor
$ git blame [nomedoarquivo]

# Mostra o histórico de alterações do arquivo com o nome do autor e SHA
$ git blame [nomedoarquivo] -l
```

#### Git log

```sh
#Mostrar uma lista de todos os commits em um repositório. Este comando mostra tudo sobre um commit, como commit ID, autor, data e mensagem do commit.
$ git log

# Lista os commits que mostram mensagens de commit e mudanças
$ git log -p

# Lista os commit's com uma expressão em comum
$ git log -S 'algumacoisa'

# Lista os commit's de um autor
$ git log --author 'Nome do Autor'

# Mostrar uma lista de commits em um repositório de uma forma mais resumida. Isso mostra uma versão mais curta do commit ID e a mensagem de commit.
$ git log --oneline

# Mostrar uma lista de commits em um repositório desde o dia anteirior
$ git log --since=yesterday

# Mostra o log pelo autor e em busca de termo específico dentro da mensagem de commit
$ git log --grep "term" --author "name"
```

#### Checkando o que estou commitando

```sh
# Veja todos (não-staged) mudanças feitas a um repo local
$ git diff

# Veja todos (staged) mudanças feitas a um repo local
$ git diff --cached

# Confira o que as mudanças entre os arquivos que você cometidos e a repo ao vivo
$ git diff --stat origin/master
```

#### Comandos úteis

```sh
# Verifique se um sha está em produção
$ git tag --contains [sha]

# Número de commit's por autor
$ git shortlog -s --author 'Nome do Autor'

# Lista de autores e commits para um repositorio em ordem alfabética
$ git shortlog -s -n

# Lista de commits comentados por autor
$ git shortlog -n --author 'Nome do Autor'
# também mostra o número total de commits pelo autor

# Numero de commit's por contribuidores
$ git shortlog -s -n

# Desfazer alterações feitas em um arquivo
$ git checkout -- nomedoarquivo

# Mostra informações mais detalhadas sobre um commit
$ git cat-file sha -p

# Mostra o número de linhas adicionadas e removidas em um repositório por um autor desde uma data no passado até o presente
$ git log --author="Nome do autor" --pretty=tformat: --numstat --since=mes | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }'
```

#### Alias úteis
Para adicionar um alias basta abrir o arquivo .gitconfig em seu diretório home e incluir o código de alias

```sh
# Mostra o log de uma forma mais condizente com o gráfico de branch e merge
lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

### Contribuir

1. Dê um Fork no repositório!
2. Crie seu novo branch: `git checkout -b meu-novo-branch`
3. Commite suas alterações: `git commit -m 'Minhas alterações'`
4. Mande para seu novo branch: `git push -u origin meu-novo-branch`
5. Submeta um pull request - Ótimo!
