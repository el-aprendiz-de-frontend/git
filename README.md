<img src="https://raw.githubusercontent.com/aledc7/git/master/git1.png" width="100">

# Apuntes GIT


## ¿Qué es Git?
Git es un **software de control de versiones** diseñado por Linus Torvalds, pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando estas tienen un gran número de archivos de código fuente.



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
$ git pull
```

<img src="/images/08-git-pull.jpg" width="400">
<img src="/images/07-git-fetch-merge.jpg" width="400">


### Comprobar el estado de la BD de GIT

```sh
$ git status
```

Descarga gratuita del libro de GIT: https://git-scm.com/book/es/v2
