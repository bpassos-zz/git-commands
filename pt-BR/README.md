<img
  src="/img/git.png"
  width="70"
  align="right"
/>
# Useful Git Commands

## Sobre 
Começou a usar Git recentemente? Esse documento deve lhe dar os principais comandos para comecar a usar o Git de uma forma básica  e simples. Caso não encontre algum comando que o julgue importante para o documento, não hesite, basta apenas [contribuir](#contribuir).  

## Sumário

* [Instalando o Git](#install-git)
* [Configurando o Git](#setting-up-git)
* [Aplicando cores ao Git](#applying-colour-to-git)
* [Inicializando um repositorio em diretorio existente](#initializing-a-repository-in-an-existing-directory)
* [Checkando o status dos arquivos](#checking-the-status-of-your-files)
* [Staging Arquivos](#staging-files)
* [Stashing Arquivos](#stashing-files)
* [Commitando Arquivos](#committing-files)
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





