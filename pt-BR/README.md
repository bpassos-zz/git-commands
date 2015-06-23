<img
  src="/img/git.png"
  width="70"
  align="right"
/>
# Git Comandos Uteis

## Sobre 
Começou a usar Git recentemente? Esse documento deve lhe dar os principais comandos para comecar a usar o Git de uma forma básica  e simples. Caso não encontre algum comando que o julgue importante para o documento, não hesite, basta apenas [contribuir](#contribuir).  

## Sumário

* [Instalando o Git](#instalando-o-git)
* [Configurando o Git](#configurando-o-git)
* [Aplicando cores ao Git](#aplicando-cores-ao-git)
* [Inicializando um repositorio em diretorio existente](#inicializando-um-repositorio-em-diretorio-existente)
* [Checkando o status dos arquivos](#Checkando-o-status-dos-arquivos)
* [Staging Arquivos](#staging-arquivos)
* [Stashing Arquivos](#stashing-arquivos)
* [Commitando Arquivos](#commitando-arquivos)
* [Branch e Merge](#branching-and-merging)
* [Reset](#resetting)
* [Git remote](#git-remote)
* [Git grep](#git-grep)
* [Git blame](#git-blame)
* [Git log](#git-log)
* [Checkando meus commits](#checking-what-you-are-committing)
* [Comandos úteis](#useful-commands)
* [Alias úteis](#useful-alias)
* [Contribuição](#contributing)

#### Git

Git e um sistema de controle de versao distribuido, muito facil de aprender e super rapido!

#### Instalando o Git

Existem algumas maneiras diferentes de instalar git (da fonte ou pelo Linux) mas o objectivo desta página é se concentrar em comandos do git, por isso estou indo supor que você está instalando o git em um Mac.

Para ver outras maneiras de instalar o Git, visite a [Git official site](http://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

Clique [aqui](http://git-scm.com/download/mac) para baixar e instalar o Git

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

Se voce adicionar um novo arquivo ao seu projeto, e o mesmo nao existia antes, quando vice executar o comando `$ git status` você deve ver seu arquivos que nao estao adicionados como este:

```sh
$ git status
# On branch master
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#   README
nothing added to commit but untracked files present (use "git add" to track)
```

#### Staging Arquivos 

Depois de inicializar um repositório git no diretório escolhido, todos os arquivos serão agora rastreados.Quaisquer alterações feitas a qualquer arquivo será exibido após o comando `$ git status`, sendo esses or arquivos que ainda nao estao commitados.

To stage changes for commit you need to add the file(s) - or in other words, stage file(s).
 
Para adicionar os arquivos na Stage Area, basta adicionar eles? 

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

Depois de adicionar/staging os arquivos, o próximo passo é commitar os arquivos que estão na Stagin:

```sh
# Commitar arquivos da stage
$ git commit -m 'commit message'

# Adicionar arquivo e commitar
$ git commit filename -m 'commit message'

# Adicionar arquivos na stage e comitar
$ git commit -am 'insert commit message'

# Alterar um Commit
$ git commit --amend 'mensagem do novo commit' ou nenhuma mensagem para manter a mensagem anterior

# Squashing commits juntos
$ git rebase -i
Isto lhe dará uma interface em seu editor de núcleo:
# Comandos:
#  p, pick = use commit
#  r, reword = use commit, mas editar a mensagem do commit 
#  e, edit = use commit, mas parar para alterar
#  s, squash = use commit, mas se juntar ao commit anterior
#  f, fixup = like "squash", mas descartar esta mensagem de log no commit
#  x, exec = usar comando (o resto da linha) usando shell
```



