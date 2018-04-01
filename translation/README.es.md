<img
  src="/img/git.png"
  width="70"
  align="right"
/>



# Comandos útiles de Git

También puedes leer la versión en [Portugués](translation/README.pt-br.md).

Volver a la versión en [Inglés](/README.md).

## Sobre
> ¿Has comenzado a utilizar Git recientemente? Esta documentación debería darte los comandos básicos necesarios para realizar las acciones más comunes en Git. Si encuentras un comando que no esté listado acá, o que podría ser explicado de una mejor manera, por favor no dudes en [Contribuir](#contributing). ¡Saludos!

## Tabla de contenidos

* [Instalar Git](#instalar-git)
* [Configurando Git](#configurando-git)
* [Aplicando color a Git](#aplicando-color-a-git)
* [Inicializando un repositorio en un directorio existente](#inicializando-un-repositorio-en-un-directorio-existente)
* [Verificando el estado de tus archivos](#chequeando-el-estado-de-tus-archivos)
* [Preparar archivos](#preparar-archivos)
* [Ocultar archivos](#ocultar-archivos)
* [Consolidar archivos](#consolidar-archivos)
* [Ramificaciones y fusiones](#ramificaciones-y-fusiones)
* [Restableciendo](#restableciendo)
* [Git remoto](#git-remoto)
* [Git grep](#git-grep)
* [Git blame](#git-blame)
* [Git log](#git-log)
* [Verificando que estás consolidando](#verificando-que-estás-consolidando)
* [Comandos útiles](#comandos-útiles)
* [Alias útiles](#alias-útiles)
* [Contribuyendo](#contribuyendo)

#### Git

Git es un sistema de control de versiones distribuidos, ¡muy fácil de aprender y súper rápido!

#### Instalar Git

Hay algunas maneras diferentes de instalar git (desde la fuente o para Linux) pero el propósito de esta página es centrarse en comandos de git, así que vamos a asumir que estás instalando git en Mac.

Para mirar otras maneras de instalarlo vista el [sitio oficial de Git](http://git-scm.com/book/en/Getting-Started-Installing-Git)

Click [aquí](http://git-scm.com/download/mac) para descargar e instalar Git

##### Configurando git

```sh
$git config --global user.name "Nombre de usuario"

$git config --global user.email "email"
```

##### Aplicando color a Git

```sh
$ git config --global color.ui true
```

##### Inicializando un repositorio en un directorio existente

Si estás comenzando a realizar un seguimiento de un proyecto en Git, debes ir al directorio del proyecto y escribir:

```sh
$ git init
```

Esto creará un nuevo subdirectorio llamado .git que contiene todos tus archivos de repositorio necesarios - un esqueleto de repositorio Git. Llegados a este punto, nada en tu proyecto tiene seguimiento todavía.

Para comenzar a versionar-controlar archivos existentes deberías empezar por hacerle seguimiento a esos archivos y hacer una consolidación (commit) inicial. Para llevarlo a cabo debes empezar con algunos `$git add` que especifiquen los archivos a los que quieres hacerles seguimiento seguido de un commit.

```sh
$git add <archivo>
$git add README
$git commit -m 'Versión inicial del proyecto.'
```

  