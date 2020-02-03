<img src="https://raw.githubusercontent.com/aledc7/git/master/git1.png" width="100">

# Apuntes GIT


## ¿Qué es Git?
Git es un **software de control de versiones** diseñado por Linus Torvalds, pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando estas tienen un gran número de archivos de código fuente.


### Ciclo de vida o estados de los archivos en GIT
- Archivos **Tracked**: Son los archivos que viven dentro de Git, no tienen cambios pendientes y sus últimas actualizaciones han sido guardadas en el repositorio gracias a los comandos git add y git commit.
- Archivos **Staged**: Son archivos en Staging. Viven dentro de Git y hay registro de ellos porque han sido afectados por el comando git add, aunque no sus últimos cambios. Git ya sabe de la existencia de estos últimos cambios pero todavía no han sido guardados definitivamente en el repositorio porque falta ejecutar el comando git commit.
- Archivos **Unstaged**: Entiendelos como archivos “Tracked pero Unstaged”. Son archivos que viven dentro de Git pero no han sido afectados por el comando git add ni mucho menos por git commit. Git tiene un registro de estos archivos pero está desactualizado, sus últimas versiones solo están guardadas en el disco duro.
- Archivos **Untracked**: Son archivos que NO viven dentro de Git, solo en el disco duro. Nunca han sido afectados por git add, así que Git no tiene registros de su existencia.
<img src="/images/14-git-data.jpg" width="800">

### Versión que tenemos instalada de GIT

```sh
$ git --version
```
<img src="/images/12-git-version.jpg" width="300">

### Inicializar un repositorio

```sh
# Genera una nueva carpeta oculta llamada .git con toda la base de datos 
# con cambios atómicos en nuestro proyecto.
$ git init
```
<img src="/images/01-git-init.jpg" width="400">

### Clonar repositorio remoto a local

```sh
$ git clone "https_o_ssh"
```
<img src="/images/04-git-clone.jpg" width="400">

### Añadir fichero o ficheros al STAGE

```sh
# Añadimos un único fichero
$ git add "nombre_fichero"

# Añadimos todos los ficheros 
$ git add .

# tambien podemos usar:
$ git add --all
```
<img src="/images/02-git-add.jpg" width="400">

### Quitar ficheros del STAGE (rm)

```sh
# Sin eliminarlos del disco. 
# Mueve los archivos que le indiquemos al estado Untracked.
$ git rm --cached  "nombre_fichero" 

# Ojo!! Se elimina el fichero del disco. 
# Git guarda el registro de la existencia de los archivos, podríamos recuperarlos.
$ git rm --force  "nombre_fichero" 
```

```sh
# Quitar archivos del estado Staged para devolverlos a su estado anterior. 
# Si los archivos venían de Unstaged, vuelven allí. Y lo mismo se venían de Untracked.
$ git reset HEAD 
```

```sh
# Volver al estado anterior los ficheros que tengamos como STAGE
$ git checkout .
```

### Añadir los cambios al repositorio LOCAL (Commit)

```sh
$ git commit -m "mensaje"
```
<img src="/images/03-git-commit.jpg" width="400">

```sh
# Podemos hacer el commit sin previamente hacer un ADD (solo si el fichero ya esta en la BDD de Git)
$ git commit -am "mensaje"
```

### Deshacer los cambios del repositorio LOCAL (The Soft Way)

```sh
# Moves the added files in last commit back to staged area
$ git reset --soft HEAD^
```

```sh
# Discards last two commits and HEAD points two commits back
$ git reset --soft HEAD^^
```

```sh
# Discards last n commits and HEAD points n commits back
$ git reset --soft HEAD~n
```

### Deshacer los cambios del repositorio LOCAL (The Hard Way)

```sh
# Remove the added files in last commit
$ git reset --hard HEAD^
```

```sh
# Discards last two commits and HEAD points two commits back
$ git reset --hard HEAD^^
```

```sh
# Discards last n commits and HEAD points n commits back
$ git reset --hard HEAD~n
```

### Subir los cambios del repositorio LOCAL al repositorio REMOTO (Push)

```sh
$ git push
```
<img src="/images/05-git-push.jpg" width="400">

```sh
# Descartar tu último PUSH
$ git reset --hard HEAD^ 
$ git push -f 
```

### Traer los cambios del repositorio REMOTO al repositorio LOCAL (Fetch)

```sh
$ git fetch
```
<img src="/images/06-git-fetch.jpg" width="400">

### Traer los cambios del repositorio LOCAL a nuestro directorio de trabajo (Pull)

```sh
# Es equivalente a hacer un git fetch origin && git merge origin/master
$ git pull
```

<img src="/images/08-git-pull.jpg" width="400">
<img src="/images/07-git-fetch-merge.jpg" width="400">


### Comprobar el estado de la BD de GIT

```sh
$ git status
```

### Ver el log con los commits

```sh
$ git log --pretty=oneline --abbrev-commit
```
<img src="/images/09-git-log-one-line.jpg" width="400">

```sh
# Mostrar en el log los ficheros que se han modificado
$ git log —stat
```
<img src="/images/10-git-log-stat.jpg" width="500">

```sh
# Mostrar el log sin comits con merge
$ git log --oneline --no-merges
```
### Ver el log comprendido entre varias fechas
```sh
# Mostrar cambios entre las fechas feb 10 2016 - feb 19 2016
git log --since='FEB 10 2016' --until='FEB 19 2016'
```

### Mostrar en el log los commits que se hicieron que incluyeran la palabra...
```sh
git log -S "config.menu_items"
```

### Visualizar changelog por usuario de cambios
```sh
# Cambios que han pasado entre mi commit (ID) y HEAD
git shortlog <commit>..HEAD
```

```sh
# Mostrar changelog de los últimos 20 cambios más recientes
git shortlog HEAD~20..
```

### Reescribir el último mensaje de commit
```sh
# Si nos equivocamos al hacer un commit en el mensaje, podemos volver a reescribirlo
$ git commit -v --amend
```

### Comandos que podemos usar con el STAGE

#### Guardar en el STAGE
```sh
$ git stash pop
```
#### Eliminar del STAGE
```sh
$ git stash drop
```
#### Pasar los cambios del STAGE a una rama 
```sh
$ git stash branch "nombre_rama" 
```
#### Listados de STAGES

```sh
$ git stash list
```
<img src="/images/11-git-stage-list.jpg" width="290">

### Limpiar ficheros Untracked
```sh
# Comprobar que ficheros se eliminaran, no borra nada de disco.
$ git clean --dry-run
```
<img src="/images/13-git-clean-dry.jpg" width="180">


```sh
# Ojo!! Elimina los ficheros UNTRACKED
$ git clean -f -d
```

## Configuración de GIT

```sh
# Abrir con VSCODE el fichero de configuración global de GIT
code ~/.gitconfig
```

```sh
# Visualizar la configuración de GIT
$ git config --list
```

```sh
# Visualizar donde esta almacenda la configuration de Git
$ git config --list --show-origin
```

```sh
# Configurar tu email para GIT de forma global
$ git config --global  user.email"tu@email.com"
```

```sh
# Configurar tu nombre de usuario para GIT de forma global
$ git config --global user.name "tu_nombre"
```

```sh
# Establecer editor por defecto para GIT
$ git config --global core.editor "code --wait"
```

```sh
# Abrir configuración de GIT en nuestro editor por defecto
$ git config --global -e
```

```sh
# Activar autocorrección (Ejemplo: git stats ---> git status
$ git config --global help.autocorrect 1
```

```sh
# Crear un .gitignore a nivel global
$ touch ~/.gitignore
$ git config --global core.excludesFile ~/.gitignore
```

```sh
# Eliminar ramas obsoletas que ya no se encuentran en el reposotio REMOTO,
# al hacer un PULL o FETCH
$ git config --global fetch.prune true
```

```sh
# Cambiar la herramienta por defecto para hacer los "diff" y los "merge"
$ git config --global diff.tool "nombre_herramienta"
$ git config --global merge.tool "nombre_herramienta"
```

## Alias utiles

```sh
# Eliminar ramas locales que ya han sido mergeadas en master
# Si por equivoacion eliminamos master ---> git checkout -b master origin/master
$ git branch --merged master | grep -v "master" | xargs -n 1 git branch -d
```

```sh
# Eliminar ramas locales que no existen en el repositorio REMOTO
$ git remote prune origin
# Para ver que ramas se podrian eliminar al ejecutar un "git remote prune origin"
$ git remote prune origin --dry-run
```

```sh
# Mostrar todos los alias de GIT que tenemos configurados
$ git config -l | grep alias | sed 's/^alias\.//g'
```






Descarga gratuita del libro de GIT: https://git-scm.com/book/es/v2
