# Comandos y Apuntes

En la consola de comandos de git se usa un guion(-) en los comandos para especificar que sigue una letra
cuando se usan dos guiones(--) se especifica que sigue una palabra.

**Stage**: es un espacio en donde se almacenan mis archivos para ser enviados en el commit.

**Comandos**:
* **git init:** me inicializa el proyecto es decir para que git le empiece a hacer el seguimiento.

* **git status:** me muestra cuales archivos han sido cambiados.

* **git add nombrearchivo.extension:** Me agrega el archivo al stage.
	- . agregando punto al comando me agrega todos los archivos que hayan cambiado.

* **git commit -m "mensaje commit":** Me crea un commit con los cambios realizados en mis archivos, es buena practiva agregarle un mensaje descriptivo acerca de los cambios realizados para en un futuro recordar que cambios se realizaron.
	* **-am "mensaje":** me permite saltarme el git add para hacer el commit (solo funciona para archivos que ya se les haya realizado seguimiento, si es nuevo no funciona.)

* **git config --list:** para ver la lista de configuraciones que se han realizado en git.
	* **git config --global user.name "Cristian Duarte":** Configuramos el usuario de git.
	* **git config --global user.email "cristianduarte@cristianduarte.cd":** Configuramos el correo para git.

* **git log:** para ver el historial de commits realizados.
	* **--stat:** se agrega  para ver la cantidad de insersiones o el numero de lineas quitadas en los archivos que cambiaron en el commit.
	* **--all --graph:** me muestra un grafico de las ramas y de los commits.
	* **--all --graph --decorate --oneline:** me muestra todo los commits con grafico e id del commita pero mas comprimido.
	* **-S "palabra":** para buscar una palabra en los commits.

* ** git shortlog:** me muestra los commits por persona del equipo.
	* **-sn:** me cuenta los commits por persona.
	* **--all:** para que sean todos los commits mostrados. 
	* **--no-merges:** para que no me tenga en cuenta los merges. 

* **git show nombrearchivo:** me muestra los cambios que ha tenido el archivo a partir del ultimo commit. 

* **git diff idcommit idcommitviejo:** se usa para ver las diferencias entre un commit especifico y otro mas viejo.

* **git reset idcommit:** Me permite volver en el tiempo a una version del proyecto  existen 2 tipos de reset: 
	* **--hard** (me borra todos los cambios realizados que llevo).
	* **--soft** (me mantiene los cambios que esten en el stagging).
	* **--mixed** ().
***Volvemos al pasado sin la posibilidad de volver al futuro.***

* **git checkout idcommit nombrearchivo:** Me permite ir a la version de un commit en especifico del pasado, por si se desea ver o por si se quieren realizar cambios. Para volver al commit actual solo es cambiar el idcommit por master. ***Volvemos al pasado con la posibilidad de volver al futuro.***

* **git branch nombreRama:** para crear una rama nueva.
	* **-l:** para listar las ramas que tengo creadas. 
	* **-D ramaEliminar:** para eliminar una rama.
	* **-r:** puedo ver las ramas remotas. 
	* **-a:** me muestras todas las locales y las remotas.
	* **-m nuevonombrerama:** para cambiar el nombre de una rama.

* **git checkout nombreRama:** para cambiarme de rama.

* **git merge nombreRama:** para fusionar los cambios en las ramas, debo de estar en la rama que quiero que continue su ciclo de vida y llamar a la rama que quiero fusionar.
Desde que no haya conflictos el merge sera automatico.
Por ejemplo: Si quiero fusionar fix-bug con la rama de develop, debo estar en develop y aplicar el comando en esta rama llamando a fix-bug

* **git remote add origin https://direccion.con:** me permite agregar un origen del repositorio es decir para actualizar o mandar mis cambios o el de otras personas al repositorio remoto, "origin" puede ser opcional pero es el nombre que comumente se le da.
	* **-v:** me permite consultar la url del origen.
	* **rm origin:** me permite eliminar el origin configurado.

* **git pull origin main:** me trae los cambios del repositorio remoto a la rama especificada. git pull tambien sirve para traer ramas del repositorio remoto
	* **--allow-unrelated-histories:** para que me traiga cambios, de historias no relacionadas

* **git push:** me envia mis cambios a la al repositorio remoto.

* **alias nombreComando = "comando completo ej: git push":** para crear alias a comandos muy largos

* **git tag -a titulotag(ej: v0.1) -m "mensaje del tag" idcommit:** Para crear tags de mi proyecto, un tag es para especificar una version del proyecto.
Los tags para que se vean reflejados en el repositorio remoto se debe hacer un push con: 
**git push origin --tags**

* **git tag:** Para ver la lista de tags.
	* **-d nombretagaborrar:** Comando para borrar un tag en local.
	* **git push origin :refs/tags/dormigo:** para hacer que se refleje en el repositorio remoto el borrar un tag.

* **git show-ref --tags:** me muestra el commit relacionado al tag 

* **git show-branch --all:** para ver informacion de las ramas

* **gitk:** me abre una interfaz grafica relacionada con las ramas.

* **git clone urlRepositorioRemoto:** Para Clonar un repositorio remoto.

* **git rebase ramaparameterlelahistoria:** Es solo para repositorios locales nunca se debe hacer para remotos porque reescribe la historia.
Me lleva la historia de la rama en la que estoy a la rama que pongo en el comando.
		Primero se hace en la rama que voy a eliminar. 
		Despues se hace en la rama que va a quedar en el proyecto.
	* Es para hacer cambios silenciosos en una rama.
	
	* Es mala practica porque me afecta la historia del proyecto no se cuando arranca la rama nueva y cuando termina.

* **git stash:** comando para guardar los cambios que aun no estan en un commit.
	* **list:** para listar lo que tengo guardado en el stash
	* **pop:** para que me saque los cambios guardados. 
	**branch nombrerRamaNueva:** para poner mis cambios directamente en una rama nueva.
	* **drop:** me borra los cambios que esten en el stash sin aplicarlos en ninguna rama.

* **git clean --dry-run:** Para limpiar el proyecto de archivos que no queremos, o que agregamos por error, me muestra cuales archivos borraria.
	* **-f:** para llevar acabo del borrado. 
	* Git no borra las carpetas borra los archivos. 
	* no borra los arhivos que esten descritos en el gitignore.

* git cherry-pick idCommit: es para traerme solamente un commit, el commit que 
	se especifique.
	
	Es una mala practica porque se reconstruye la historia, es mejor hacer el 
	trabajo duro y usar merge.
	
* git reflog: me muestra el historial de todo el proyecto
	las cosas que se han eliminado etc. todo tod. 

* git reset --soft idcommit: Te recuperará todos los cambios que tengas diferentes al idcommit, los agregará al staging area y moverá el head al idcommit
	--hard idcommit: me lleva al commit que especifique y elimina cualquier cambio que tenga.
	
	Es mala practica hacer git reset.
	
* git commit --amend: me permite agregar cambios pendientes al ultimo commit
	de archivos o mensajes en el commit para agregar los archivos hay que hacer
	previamente un git add.
	
* git grep "paralabra": Comando que me ayuda a buscar una palabra en el proyecto.
	-n "palabra": con el parametro -n me dice en que linea de que archivo esta la palabra buscada.
	-c "palabra": me cuenta las veces que uso la palabra en los archivos que se encuentra.
	
* git blame nombrearchivo: para ver quien ha hecho que en el archivo.
	-C nombrearchivo: indente mejor lo que muestra.
	nombrearchivo -L35,53: me muestra solo las lineas que especifique.
	
* git comando --help: me muestra las diferentes opciones que tiene un comando en github.

----- GENERAR UNA LLAVE PUBLICA/PRIVADA -----
1. En la consola ssh-keygen -t rsa -b 4096 -C "crduarte99@gmail.com"
2. para poder usar la llave hay que verificar que el servidor de llaves del sistema esta operando
usamos el comando: eval $(ssh-agent -s) el cual nos retornara el PID del proceso
3. Una vez sabemos que el servidor de llaves funciona procedemos agregarla al sistema operativo
por medio del comando: ssh-add /c/users/cadm/.ssh/id_rsa la ubicacion de la llave puede cambiar en las 
maquinas.


Anotaciones 
	- Siempre que se vaya a realizar un PUSH a un repositorio hay que hacer un pull
		para traer las actualizaciones realizadas. 
		
	- En un entorno profesional es mejor hacer siempre el pull request en el repositorio remoto. 
	
	- Cuando trabajamos con ramas realizamos nuestros cambios, actualizamos el repositorio local
		antes de hacer los commits, realizamos los commits de nuestros cambios y hacemos el push,
		si debemos unir nuestros cambios con alguna rama nos pasamos a la rama que queremos llevar
		los cambios, la actualizamos y hacemos merge con la rama que contiene nuestros cambios. 

Pagina para editar archivos markDown dm:
https://pandao.github.io/editor.md/en.html
https://getemoji.com/