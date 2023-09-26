<p align="center">
  <a target="blank"><img src="https://cdn-icons-png.flaticon.com/512/25/25231.png" width="150" alt="GitHub Logo" /></a>
</p>
<p align="center">
  <strong><span style="font-size: 30px;">Comandos Git-GitHub</span></strong>
</p>
Para validar la version de Git:
~~~
git --version
~~~
Para validar la ayuda de Git:
~~~
git help
~~~
>Cuando se ingresa a un comando y se ve **:** se puede salir de este ingresando la letra **q**

Para hacer una configuracion global de Git:
~~~
git config --global user.name "Jeferson Romero"

git config --global user.email "j.daniel0320@gmail.com"
~~~

Para listar todos los cambios, adicionalmente adentro se puede oprimir la letra **a** para modificar y para salir se oprime **:wq!** esto es para salir(**:**), grabar(**w**), inmediatamente(**!**), si se quiere solo salir sin guardar se oprime **:q**:
~~~
git config --global -e
:wq! => Salir con grabar
:q! => Salir
~~~
Para inicializar o crear el repositorio local:
~~~
git init
~~~
Para validar el status:
~~~
git status
~~~
Para alistar a un solo archivo:
~~~
git add index.html
~~~
Para alistar todos los archivos:
~~~
git add .
~~~
Para remover uno de los archivos:
~~~
git reset .DS_Store
~~~
Para hacer el primer commit:
~~~
git commit -m "Primer commit"
~~~
>Si se presenta un error de CRLF se debe ejecutar el siguiente comando:
git config core.autocrlf true 

Para recuperar el ultimo commit:
~~~
git checkout -- .
~~~
Para recuperar un commit en especial:
~~~
git checkout -- README.md
~~~
Para ver la rama en la cual se esta:
~~~
git branch
~~~
> Se recomienda colocar en la rama **master** lo que va a producción

Para cambiar el nombre de la rama master a main:
~~~
git branch -m master main
~~~
Para que por defecto que en cualquier proyecto que cree se cree el nombre main y no master, se debe correr la siguiente linea, primero va el modelo y luego el ejemplo:
~~~
git config --global init.defaultBranch <name>
git config --global init.defaultBranch main
~~~
Luego de esto podremos validar las configuraciones que dejamos establecidas con:
~~~
git config --global -e
~~~
>Para simplificar un add y un message:
~~~
git commit -am "Readme Actualizado"
~~~

Para ver los log:
~~~
git log
~~~

> Para hacer un commit desde VSCode lo primero es ir a "**Source Control**", luego en el "**+**" alli se agregara y posterior en el Message se agrega el texto deseado y se oprime **ctrl** + **Enter** y se agregara el commit.

Para añadir por extensiones de archivos, en este caso todos los html:
~~~
git add *.html
~~~
Para añadir por carpetas con la misma extension:
~~~
git add js/*.js
~~~
Para agregar todo lo que esta en Directorios o Subdirectorios:
~~~
git add css/
~~~
> Git no mantiene carpetas sin archivos y a veces se requiere una carpeta vacia en donde se guarda cierta informacion, para esto se crea el archivo **.gitkeep**, esto le dice a git que mantenga esta carpeta

PAra poder agregar este archivo, lo hacemos así:
~~~
git add uploads/.gitkeep
~~~

Para agregar un modificador, es decir, lo mismo pero abreviado, por ejemplo se puede agregar **--short**
~~~
git status --short
~~~
Para crear un **Alias**, esto es para crear nuestros propios atajos:
~~~
git config --global alias.s "status --short"
~~~
Alias para **Git Log** seria **git lg**, en donde se formatea por completo, o el de **git status** se creo como **git s**
~~~
git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
~~~
Para saber los cambios que se han aplicado se usa:
~~~
git diff
~~~
Cuando los cambios estan aun en el add, la forma de ver los cambios es con este comando:
~~~
git diff --staged
~~~
> Para hacer la comparacion de los cambios, se recomienda hacerlo desde VSCode.
Para modificar el comentario de un commit, se lleva a cabo con este:
~~~
git commit --amend -m "Notas actualizadas"
~~~
Si queremos entrar a todo el historial accedemos:
~~~
git commit --amend
~~~
Para borrar el ultimo commit, lo hacemos así:
~~~
git reset --soft HEAD^
~~~
Si queremos irnos a un commit en especial, cambiamos el HEAD por el id
~~~
git reset --soft 0d21528
~~~
Si queremos irnos a un commit en especial, pero borrando todo y haciendolo de nuevo pero conservando los cambios en los archicvos:
~~~
git reset --mixed 77448ef
~~~
Si queremos irnos a un commirt destructivo:
~~~
git reset --hard 77448ef
~~~
Para conocer el orden cronologico de los cambios:
~~~
git reflog
~~~
Luego de conocer el log que necesitamos regresar, vamos a la siguiete intancia:
~~~
git reset --hard fb12f57
~~~
Para renombrar un archivo:
~~~
git mv destruir-mundo.md salvar-mundo.md
~~~
Para eliminar un archivo:
~~~
git rm salvar-mundo.md
~~~
Para no darle seguimiento a archivos en especifico:
> Se crea el archivo **.gitignore** y allí se incluyen los nombres de los archivos que no queremos darle seguimiento.

## Ramas

- Union **Fast-forward**: Esto es que no se detectan cambios en la rama principal y se puede unir cada uno de los commit. 

- Union **Uniones Automáticas**: Git detecta que en la rama principal hubo un cambio y que la rama secundaria no reconoce, pero como se modificaron lineas diferentes no hay conflicto y lo puede unir.

- Union **Manual**: Esto es cuando en la rama 1 tenemos cambios y en la rama 2 tambien que afectan a las mismas lineas.

Para crear una nueva rama:
~~~
git branch rama-villanos
~~~
Para movernos a la nueva rama:
~~~
git checkout rama-villanos
~~~
> Para poder hacere un **merge**, lo prinmero es pararnos en la rama que queremos que se le apliquen los cambios, es decir, tengo la rama master, de donde cree la rama-villanos, me tengo que parar en la master para que los cambios de rama-villanos se aplique en la master, esto se hace mediante el siguiete script:
~~~
git merge rama-villanos
~~~
Lo siguiente al unir a las ramas, es borrar la rama que no se utilizara, si esta tiene cambios y queremos forzar la eliminacion, oprimimos **-f**:
~~~
git branch -d rama-villanos
git branch -d rama-villanos -f
~~~
Para crear una rama y ubicarme en ella en un solo paso:
~~~
git checkout -b rama-villanos
~~~
>Para resolver los problemas con **Union Manual**, se deba validar el Script de conflicto, validar que se deja o se quita y posteriormente se hace un nuevo commit.

## Tags

Esto es para nombrar las versiones de nuestros desarrollos.
~~~
git tag super-release
~~~
Para crear de otra forma el tag:
~~~
git tag -a v1.0.0 -m "Version 1.0.0 lista"
~~~
Para eliminar tag:
~~~
git tag -d super-release
~~~
Para ver la infomracion completa de un tag:
~~~
git show v0.1.0
~~~
## Stash
Este es un metodo con el cual se guardo algo en una rama que no va a ir a produccion, no se recomienda hacer muchos de estos porque se puede tender a confundir, pero basicamente encapsulo algo mientras soluciono algo y luego regreso a esto.
[Comandos](https://git-scm.com/docs/git-stash)
~~~
git stash
~~~
**Se recomienda usar mejor este guardado de stash**
~~~
git stash save "Agregamos a Loki a Villanos"
~~~
Para validar el stash
~~~
git stash list
~~~
Para validar el stash completo
~~~
git stash list --stat
~~~
Para regresar el stash y elimina este
~~~
git stash pop
~~~
Para borrar los registros del stash
~~~
git stash clear
~~~
Para borrar el ultimo stash, despues de **drop** se deja vacio, si se requiere uno especifico, se coloca el log 
~~~
git stash drop stash@{2}
~~~
Para recuperar un stash especifico
~~~
git stash apply stash@{2}
~~~
Para revisar un stash especifico
~~~
git stash show stash@{2}
~~~

## Rebase
Este es un metodo para cambiar el orden de los commit y poder hacer un merge mas limpio.

Lo primero que se debe hacer es estar parado en la rama la cual quiero que se muevan los cambios, es decir que queden de ultimas.
~~~
git rebase master
~~~
Para unir commit, lo que esta despues del **~**(alt + 126) es la cantidad de commit a unir:
~~~
git rebase -i HEAD~4
~~~
Luego de esto, nos llevara a una pantalla en donde debemos seleccionar **s** para combinar, siempre la **s** la colocamos en el segundo commit, luego salimos y este nos lleva a una pantalla donde cambiaremos el nombre, si lo deseamos, si queremos cambiar el nombre de los commit lo hacemos con **r**


Para editar los commit y separlos, accedemos como en el punto anterior y seleccionamos la letra **e**, luego esto nos saca y hacemos un **git reset HEAD^** y volveremos al modo de edicion y podremos hacer el **add** y luego el **commit**, por ultimo para salir escribimos **git rebase --continue**

# GitHub
Se crea un repositorio y tenemos dos opcinoes para subir archivos.
Una vez se loguea la cuenta, podemos seguir subiendo.

## Pasos para subir un proyecto a GitHub

1. Primero se crea el repositorio.
2. Crear el archivo **.gitignore**
3. Se copia el cod de **"…or push an existing repository from the command line"**
4. se hace un **git init** luego se hace un **git add .** seguido de un **git commit**
5. Seguimos con lo que copiamos de gitHub.
6. crear el tag **git tag -a v0.0.1 -m "Version Alpha"**, para validar si quedo bien creada se escribe **git show v0.0.1**
7. Para subier el tag **git push --tags**
8. Para que se convierta en un release, editamos el tag y lo guardamos.
9. Para agregar colaboradores se hace desde el proyecto en la seccion **Settings**

Los tag no se suben automaticamente, debemos subirlos manualmente:

Cuando descargamos una versión esta viene sin el historial de git.
~~~
git push --tags
~~~
Para traer los datos desde github
~~~
git pull
~~~
Para ver el repositorio de github:
~~~
git remote -v
~~~
Para clonar un repositorio, vamos al repositorio y seleccionamos **HTTPS** y copiamos la url
~~~
git clone https://github.com/Jefferdaniel0320/liga-justicia.git
~~~
Cuando un pull no funciona por conflicto con el commit se configura lo siguiente:
~~~
git config pull.rebase true
~~~
Para mantener en toda la maquina esta configuracion anterior lo hacemos de la siguiete forma:
~~~
git config --global pull.rebase true
~~~
## Pull Requests
Es una rama que se desprendio en cierto punto del tiempo y luego se puede volver a unir.

Para crear un pull Requests:
1. nos paramos en la una carpeta y crea mos un nuevo archivo.
2. Hacemos un commit yseleccionamos **create a new branch**
3. colocamos el nombre.
4. Luego marcamos ****Popose new file ****
5. luego se crea el pull reques.
6. Luego se puede confirmar este pull reques.
7. Si ya no se necesita la rama,se puede eliminar.

## Git Fetch
este se puede hacer primero para comprobar y luego si hacer el git pull 


## Para Clonar el repositorio

Lo primero que se debe hacer es clonar el repositorio, esto se hace seleccionando en el relpositorio que queremos **Fork**

lo segundo es una vez tengamos el repositorio, lo vamos a clonar.

## Crear Ramas, unirlas al main y eliminarla.
1. creamos el archivo
2. escribimos **git checkout -b rama-villanos**
3. hacemos un **git add .**, un **git commit -m ""**
4. hacemos un **git push** esto falla, pero nos trae el comando correcto **git push --set-upstream origin rama-villanos** 
5. En github podemos seleccionar el boton de "compare & pull request" y colocar un mensaje, aun no se hace el merge, se coloca comentarios para que validen.
6. validamos en que rama estamos **git branch** y cambiamos con **git checkout rama-villanos**.
7. Puedo aplicar cambios y hacer un commit.
8. hacemos un **git push** y validamos en "Pull requests" de GitHub y podemos hacer el Merge.
9. Si deseamos borrar la rama, vamos a la ramas en GitHub y la borramos, pero debemos tambien borrarla en el Git.
10. para borrarla, primero debemos hacer es pasarnos a la rama main **git checkout main** y corremos un **git pull**
11. procedemos a borrar la rama **git branch -d rama-villanos** 

### Se quedo hasta el videeo 83.
**.**
**.**
**.**
**.**
**.**

## WIKI
## GitHub Pages
Para crear un portafolio:
1. Se crea un nuevo repositorio, este puede ser de la siguiente forma **jefferdaniel0320**
2. Nos dirigimos a settings y se selecciona la opcion de **pages**

## GitHub Pages2 
Para crear un portafolio:
* Primero en Git crearemos una rama **git checkout -b rama-web**
* Se crea una carpeta llamada docs
* Creamos un archivo html y escribimos **!** y tab, luego creamos el archivo js.
* Luego hacemos un **git add .**, un **git commit -m ""**
* Luego pasamos a la rama main con un **git checkout main** y hacemos un merge **git merge rama-web**
* Luego vamos a settings en GitHub y se selecciona la rama main y la carpeta docs.
* Recargamos y aparecera la opcion para acceder a la url.

## Gist
Para acceder a este se hace con el comando **gist Open gist** o **gist insert text**