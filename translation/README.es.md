<img
  src="/img/git.png"
  width="70"
  align="right"
/>



# Comandos útiles de Git

También puedes leer la versión en [Portugués](/README.pt-br.md).

Volver a la versión en [Inglés](/README.md).

## Sobre
> ¿Has comenzado a utilizar Git recientemente? Esta documentación debería darte los comandos básicos necesarios para realizar las acciones más comunes en Git. Si encuentras un comando que no esté listado acá, o que podría ser explicado de una mejor manera, por favor no dudes en [contribuir](#contribuyendo). ¡Saludos!

## Tabla de contenidos

* [Instalar Git](#instalar-git)
* [Configurando Git](#configurando-git)
* [Aplicando color a Git](#aplicando-color-a-git)
* [Inicializando un repositorio en un directorio existente](#inicializando-un-repositorio-en-un-directorio-existente)
* [Verificando el estado de tus archivos](#chequeando-el-estado-de-tus-archivos)
* [Preparar archivos](#preparar-archivos)
* [Guardar archivos provisionalmente](#guardar-archivos-provisionalmente)
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

Hay diferentes maneras de instalar git (desde la fuente o para Linux) pero el propósito de esta página es centrarse en comandos de git, así que vamos a asumir que estás instalando git en Mac.

Para mirar otras maneras de instalarlo visita el [sitio oficial de Git](http://git-scm.com/book/en/Getting-Started-Installing-Git)

Click [aquí](http://git-scm.com/download/mac) para descargar e instalar Git

##### Configurando git

```sh
$ git config --global user.name "Nombre de usuario"

$ git config --global user.email "email"
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
$ git add <archivo>
$ git add README
$ git commit -m 'Versión inicial del proyecto.'
```

##### Verificando el estado de tus archivos

La herramienta principal que se utiliza para determinar qué archivos están en qué estado es con el comando `$ git status`. Si corres este comando directamente después de una clonación, deberías ver algo como esto:

```sh
$ git status
# On branch master
nothing to commit (working directory clean)
```

Si agregas un nuevo archivo al proyecto, y si el archivo no existía anteriormente, cuando corras un `$ git status` deberías ver tu archivo sin seguimiento así:

```sh
$ git status
# On branch master
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#   README
nothing added to commit but untracked files present (use "git add" to track)
```

#### Preparar archivos

Después de inicializar un repositorio de git en el directorio escogido, todos tus archivos estarán en seguimiento. Cualquier cambio hecho a cualquier archivo se mostrarán después de un `$ git status` si los cambios no fueron preparados para un commit.

Para preparar archivos para un commit, necesitarás agregar el o los archivos - o en palabras más técnicas, prepararlos.

```
# Agregando un archivo
$ git add nombreDelArchivo

# Agregando todos los archivos
$ git add -A

# Agregando todos los cambios de archivos en un directorio
$ git add .

# Escogiendo que cambios agregar (esto irá a través de todos tus cambios y puedes elegir 'Y' o 'N' a los cambios)
$ git add -p
```

#### Guardar archivos provisionalmente

`$ git stash` es un comando muy útil, donde git añadirá los cambios en un directorio sucio - pero no te preocupes, puedes reaplicarlos luego. Este comando guardará tus cambios locales por fuera y revertirá el directorio de trabajo para que asemeje el commit de cabecera (HEAD).

```sh
# Guardar provisionalmente cambios locales
$ git stash

# Guardar provisionalmente cambios locales con un mensaje personalizado
$ git stash save "este es tu mensaje personalizado"

# Reaplicar los cambios locales que guardaste en el último stash
$ git stash apply

# Reaplicar los cambios locales que guardaste en un número de stash dado
$ git stash apply stash@{stash_number}

# Arroja cualquier stash por su número
$ git stash drop stash@{0}

# Aplicar el stash e inmediatamente retirarlo de la pila
$ git stash pop

# 'Libera' un stash en particular de tu lista de stashes
$ git stash pop stash@{stash_number}

# Lista todos los stashes
$ git stash list

# Difiere los detalles de un número de stash dado
$ git diff stash@{0}
```

#### Consolidando archivos

Después de agregar o guardar provisionalmente un archivo, el siguiente paso es consolidar (commit) el o los archivos preparados.

```sh
# Consolidar archivo/s preparado/s
$ git commit -m 'mensaje de consolidación'

# Agregar un archivo y commit
$ git commit nombreDeArchivo -m "mensaje de consolidación'

# Enmendar un commit
$ git commit --amend 'nuevo mensaje de consolidación' o sin mensaje para mantener el mensaje anterior.

# Apiñar commits juntos
$ git rebase -i
Esto te proporcionará una interface en tu editor base:
# Comandos:
# p, pick = usar commit
# r, reword = usar commit, pero editar el mensaje del commit
# e, edit = usar commit, pero parar de enmendar
# s, squash = usar commit, pero combinar con el commit previo
# f, fixup = como "squash", pero descarta el log de mensajes de commit
# x, exec = corre comando (el resto de la línea) utilizando el shell

# Apiñar commits juntos usando reset --soft
$ git reset --sfot HEAD~number_of_commits
$ git commit
** ADVERTENCIA: esto requerirá de commits mandados a la fuerza, lo cual está BIEN si esto está en una rama antes de hacer push a master o crear un Pull Request.
```

##### Ramificaciones y fusiones

```sh
# Creando una rama local
$ git checkout -b nombreDeLaRama

# Cambiando entre 2 ramas (de hecho, esto funciona en una terminal como al cambiar entre 2 directorios - $ cd -)
$ git checkout -

# Mandando rama local a remoto
$ git push -u origin nombreDeLaRama

# Eliminando una rama local - esto no eliminará una rama que no ha sido fusionada todavía
$ git branch -d nombreDeLaRama

# Eliminando una rama local - ¡esto ELIMINARÁ una rama incluso si no ha sido fusionada todavía!
$ git branch -D nombreDeLaRama

# Remueve cualquier referencia remota que haya eliminado localmente de su remoto (puedes sustituir <origin> con cualquier rama remota)
$ git remote prune origin

# Ver todas las ramas, incluyendo ramas locales y remotas
$ git branch -a

# Ver todas las ramas que han sido fusionadas en tu rama actual, incluyendo las locales y remotas
$ git branch -a --merged

# Ver todas las ramas que no han sido fusionadas en tu rama actual, incluyendo las locales y remotas
$ git branch -a --merged

# Ver ramas locales
$ git branch -r

# Traspasa la rama master a tu rama local
$ git rebase origin/master

# Manda la rama local después de un traspaso (rebase) de master a tu rama local
$ git push origin +branchname
```

#### Trayendo y verificando nuestras ramas remotas

```sh
# Esto traerá todas las ramas remotas hacia ti.
$ git fetch origin

# Con las ramas remotas en mano, ahora necesitas verificar la rama en la que estás interesado, dándote una copia de trabajo local:
$ git checkout -b test origin/test

# Eliminando una rama remota
$ git branch -rd origin/branchname
$ git push origin --delete nombreDeLaRama o $ git push origin:nombreDeLaRama
```

#### Fusionando ramas a trunk/master

```sh
# Primer checkout trunk/master
$ git checkout trunk/master

# Ahora fusiona la rama a trunk/master
$ git merge nombreDeLaRama

# Para cancelar una fusión
$ git merge --abort
```

#### Actualizando un repositorio local con cambios de un repositorio de Github

```sh
$ git pull origin master
```

#### Seguimiento de una rama existente

```sh
$ git branch --set-upstream-to=origin/foo foo
```