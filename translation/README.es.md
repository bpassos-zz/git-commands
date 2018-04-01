<img
  src="/img/git.png"
  width="70"
  align="right"
/>



# Comandos útiles de Git

También puedes leer la versión en [Portugués](/translation/README.pt-br.md).

Volver a la versión en [Inglés](/README.md).

## Sobre
> ¿Has comenzado a utilizar Git recientemente? Esta documentación debería darte los comandos básicos necesarios para realizar las acciones más comunes en Git. Si encuentras un comando que no esté listado acá, o que podría ser explicado de una mejor manera, por favor no dudes en [contribuir](#contribuyendo). ¡Saludos!

## Tabla de contenidos

* [Instalar Git](#instalar-git)
* [Configurando Git](#configurando-git)
* [Aplicando color a Git](#aplicando-color-a-git)
* [Inicializando un repositorio en un directorio existente](#inicializando-un-repositorio-en-un-directorio-existente)
* [Verificando el estado de tus archivos](#verificando-el-estado-de-tus-archivos)
* [Preparar archivos](#preparar-archivos)
* [Guardar archivos provisionalmente](#guardar-archivos-provisionalmente)
* [Consolidar archivos](#consolidar-archivos)
* [Ramificaciones y fusiones](#ramificaciones-y-fusiones)
* [Restableciendo](#restableciendo)
* [Git remoto](#git-remoto)
* [Git grep](#git-grep)
* [Git blame](#git-blame)
* [Git log](#git-log)
* [Verificando lo consolidando](#verificando-lo-consolidando)
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

Para comenzar a versionar-controlar archivos existentes deberías empezar por hacerle seguimiento a esos archivos y hacer una consolidación (commit) inicial. Para llevarlo a cabo debes empezar con algunos `$ git add` que especifiquen los archivos a los que quieres hacerles seguimiento seguido de un commit.

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

```sh
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

# Reaplicar los cambios locales que guardaste en un número de stash otorgado
$ git stash apply stash@{stash_number}

# Arroja cualquier stash por su número
$ git stash drop stash@{0}

# Aplicar el stash e inmediatamente retirarlo de la pila
$ git stash pop

# 'Libera' un stash en particular de tu lista de stashes
$ git stash pop stash@{stash_number}

# Lista todos los stashes
$ git stash list

# Difiere los detalles de un número de stash otorgado
$ git diff stash@{0}
```

#### Consolidar archivos

Después de agregar o guardar provisionalmente un archivo, el siguiente paso es consolidar (commit) el o los archivos preparados.

```sh
# Consolidar archivo/s preparado/s
$ git commit -m "mensaje de consolidación"

# Agregar un archivo y commit
$ git commit nombreDeArchivo -m "mensaje de consolidación"

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
$ git reset --soft HEAD~number_of_commits
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
$ git branch -a --no-merged

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

# Con las ramas remotas en mano, ahora necesitas verificar la rama en la que estás interesado, otorgándote una copia local del trabajo:
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

#### Restableciendo

```sh
# Mezcla tu cabecera con un sha otorgado
# Esto te permite hacer cosas como dividir un commit
$ git reset --mixed [sha]

# Upstream master
$ git reset HEAD origin/master -- nombreDelArchivo

# La versión del commit más reciente
$ git reset HEAD -- nombreDelArchivo

# La versión antes del commit más reciente
$ git reset HEAD^ -- nombreDelArchivo

# Mover cabecera a un commit en específico
$ git reset --hard sha

# Reiniciar el área de preparación y el directorio de trabajo para asemejar el commit más reciente. En adición a los cambios sin preparar, la bandera --hard le dice a Git que sobreescriba todos los cambios en el directorio de trabajo también.
$ git reset --hard
```

#### Git remoto

```sh
# Muestra hacia donde está apuntando 'origin' y también las ramas a las que se están haciendo seguimiento
$ git remote show origin

# Muestra hacia donde está apuntando 'origin'
$ git remote -v

# Cambia la url remota de 'origin'
$ git remote set-url origin https://github.com/user/repo.git

# Agrega un nuevo 'origin'
# Usualmente utilizado para traspasar (rebase) desde bifurcaciones (forks)
$ git remote add [NOMBRE] https://hithub.com/user/fork-repo.git
```

#### Git grep

```sh
# 'Busca' por partes de cadenas de caracteres en un directorio
$ git grep 'algo'

# 'Busca' por partes de cadenas de caracteres en un directorio y el -n imprime el número de líneas donde git ha encontrado equivalencias.
$ git grep -n 'algo'

# 'Busca' por partes de cadenas de caracteres en un contexto (algunas líneas antes y algunas después del término grepped) 
$ git grep -C<número de líneas> 'algo'

# 'Busca' por partes de cadenas de caracteres y también muestra las líneas ANTES del término grepped
$ git grep -B<número de líneas> 'algo' 

# 'Busca' por partes de cadenas de caracteres y también muestra las líneas DESPUÉS del término grepped
$ git grep -A<número de líneas> 'algo'
```

#### Git blame

```sh
# Muestra el historial de alteración de un archivo con el nombre del autor
$ git blame [nombreDelArchivo]

# Muestra el historial de alteración de un archivo con el nombre del autor && SHA
$ git blame [nombreDelArchivo] -l
```

#### Git log

```sh
# Muestra la lista de todos los commits en un repositorio. Este comando muestra absolutamente todo acerca de un commit, tal como ID del commit, autor, fecha y el mensaje del commit.
$ git log

# Listado de commits mostrando los mensajes de commits y los cambios
$ git log -p

# Listado de commits con la expresión en particular que estás buscando
$ git log -S 'algo'

# Listado de commits por autor
$ git log --author 'Nombre del autor'

# Muestra un listado de commits en un repositorio de una manera más resumida. Este muestra una versión corta del ID del commit y el mensaje del commit.
$ git log --oneline

# Muestra un listado de commits en un repositorio desde ayer
$ git log --since=yesterday

# Muestra el log por autor y buscando por un término en específico dentro del mensaje del commit
$ git log --grep "término" --author "nombre"
```

#### Verificando lo consolidado

```sh
# Muestra todos los cambios (no-preparados) hechos en un repositorio local
$ git diff

# Muestra todos los cambios (preparados) hechos en un repositorio local
$ git diff --cached

# Verifica los cambios que has consolidado entre los archivos y el repositorio en vivo.
$ git diff --stat origin/master
```

#### Comandos útiles

```sh
# Verifica si un sha está en producción
$ git tag --contains [sha]

# Número de commits por autor
$ git shortlog -s --author 'Nombre del autor'

# Listado de autores y commits de un repositorio ordenados alfabéticamente
$git shortlog -s -n

# Listado de comentarios de commits por autor
$ git shortlog -n --author 'Nombre del autor'
# Esto también muestra el número total de commits por autor

# Número de commits por contribuidores
$git shortlog -s -n

# Deshacer cambios locales a un archivo
$ git checkout -- nombreDelArchivo

# Muestra información más detallada acerca de un commit
$ git cat-file sha -p

# Muestra el número de líneas agregadas y eliminadas de un repositorio por un autor desde hace algún tiempo.
$ git log --author="Author name" --pretty=tformat: --numstat --since=month | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }'
```

#### Alias útiles
Para agregar un alias, simplemente abre tu archivo .gitconfig en tu directorio raíz e incluye el código de alias

```sh
# Muestra el log en un modo más consistente con una gráfica para ramificaciones y fusiones.
lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

### Contribuyendo

1. ¡Bifucarlo! (Fork it)
2. Crea tu rama de características: `git checkout -b mi-nueva-caracteristica`
3. Consolida tus cambios: `git commit -m 'Agrega nueva característica'`
4. Push a la rama: `git push -u origin mi-nueva-caracteristica`
5. Envía un pull request - ¡gracias!
