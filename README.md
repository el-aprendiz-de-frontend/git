<img src="https://raw.githubusercontent.com/aledc7/git/master/git1.png" width="100">

# Apuntes GIT


## ¿Qué es Git?
Git es un **software de control de versiones** diseñado por Linus Torvalds, pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando estas tienen un gran número de archivos de código fuente.


### Ciclo de vida o estados de los archivos en GIT
- Archivos **Tracked**: Son los archivos que viven dentro de Git, no tienen cambios pendientes y sus últimas actualizaciones han sido guardadas en el repositorio gracias a los comandos git add y git commit.
- Archivos **Staged**: Son archivos en Staging. Viven dentro de Git y hay registro de ellos porque han sido afectados por el comando git add, aunque no sus últimos cambios. Git ya sabe de la existencia de estos últimos cambios pero todavía no han sido guardados definitivamente en el repositorio porque falta ejecutar el comando git commit.
- Archivos **Unstaged**: Entiendelos como archivos “Tracked pero Unstaged”. Son archivos que viven dentro de Git pero no han sido afectados por el comando git add ni mucho menos por git commit. Git tiene un registro de estos archivos pero está desactualizado, sus últimas versiones solo están guardadas en el disco duro.
- Archivos **Untracked**: Son archivos que NO viven dentro de Git, solo en el disco duro. Nunca han sido afectados por git add, así que Git no tiene registros de su existencia.

### Versión que tenemos instalada de GIT

```sh
$ git --version
```
<img src="/images/12-git-version.jpg" width="300">

### Inicializar un repositorio

```sh
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
```
<img src="/images/02-git-add.jpg" width="400">

### Quitar ficheros del STAGE 

```sh
# Sin eliminarlos del disco. 
# Mueve los archivos que le indiquemos al estado Untracked.
$ git rm --cached  "nombre_fichero" 

# Ojo!! Se elimina el fichero del disco. 
# Git guarda el registro de la existencia de los archivos, por lo que podremos recuperarlos si es necesario.
$ git rm --force  "nombre_fichero" 
```

```sh
# Quitar archivos del estado Staged para devolverlos a su estado anterior. 
# Si los archivos venían de Unstaged, vuelven allí. Y lo mismo se venían de Untracked.
$ git reset HEAD 
```

### Añadir los cambios al repositorio LOCAL

```sh
$ git commit -m "mensaje"
```
<img src="/images/03-git-commit.jpg" width="400">


### Subir los cambios del repositorio LOCAL al repositorio REMOTO

```sh
$ git push
```
<img src="/images/05-git-push.jpg" width="400">


### Traer los cambios del repositorio REMOTO al repositorio LOCAL

```sh
$ git fetch
```
<img src="/images/06-git-fetch.jpg" width="400">

### Traer los cambios del repositorio LOCAL a nuestro directorio de trabajo

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
$ git clean --dry-run
```
<img src="/images/13-git-clean-dry.jpg" width="180">


Descarga gratuita del libro de GIT: https://git-scm.com/book/es/v2
