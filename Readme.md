# Notas de Git

[Link practica git](https://learngitbranching.js.org/)

## Git Bash

`cd`-> cambiar directorio (home `/`,`/c`,`/user`,`..` volver a carpeta anterior,`tab` autocompletar)  
`ls`-> listar archivos(+`-al`)  
`clear`-> limpiar consola (tambien`ctr+l`)  
`mkdir`-> crear carpeta  
`pwd`-> ver en que carpeta me encuentro  
`touch`-> crear archivo  
`cat`-> ver contenido de archivo
`history`->historial de comandos(`!#`repetir el comando numero #)  
`rm`->remover archivo
`--help` -> ayuda de cada una de las funciones

## Comandos git

### Configuración

`git config`-> comando para revisar configuraciones  
`git config --global user.name "nombre"`->configurar nombre  
`git config --global user.email "email"`->configurar email

### Repositorio

`git init`-> Inicializar repositorio  
`git add [archivo]` -> añadir cambios del archivo (+`.` añadir todos los archivos)  
`git status`-> ver estado de los archivos  
`git rm`-> remover del add  
<img src="img\git_rm_rs.webp" alt="git rm rs" width="50%">  

`git commit -m "mensaje"`->envia cambios al repositorio con un mensaje  
`git commit -am "mensaje"`-> hace el add y commit 
`git log`-> historia de commits (+`--oneline` para ver la historia como una lista,`--stat` cambios en los archivos)  
`git log --all --graph --decorate --oneline`-> toda la historia con los branch  
`git show [arch]`->mostrar la diferencia con la version anterior  
`git commit` -> escribir el mensaje y salirse con `esc+shift+z+z` vim  guardar  
`git diff [indicador del commit 1] [indicador del commit 2]`->diferencia entre dos commits  

#### Branch y Merge

Las ramas permiten realizar experimentos, corregir errores y un merge une el cambio y la rama principal.

`git chekout [ind commit, master] [arch]`-> traer los cambios de una rama a local con el commit se envian los cambios a la rama master  
`git reset [ind commit]`-> volver en el tiempo a un commit anterior (+`--hard`,`--soft`) cuidado!  
`git clone [url_del_servidor_remoto]`-> Nos permite descargar los archivos de la última versión de la rama principal y todo el historial de cambios en la carpeta .git.  
`git push`-> Manda los cambios al servidor remoto.  
`git fetch`->Traer actualizaciones del servidor remoto y guardarlas en nuestro repositorio local.
`git merge`-> También usamos el comando git merge con servidores remotos. Lo necesitamos para combinar los últimos cambios del servidor remoto y nuestro directorio de trabajo.  
`git pull`: Básicamente, git fetch y git merge al mismo tiempo.  

`git branch [nombre_de_rama]`-> Crear rama nueva  
`git checkout -b [yourbranchname]`->Crea la rama y directamente se mueve a esta
`git chekout [nombre_de_rama]`-> Mover el head a la otra rama  
`git branch`-> Nombres de las ramas  
`git merge [nombre_de_la_rama]`->fusiona la rama con la rama actual (preferiblemente master)  
`git push origin nombre-de-la-rama`->Publicar una rama local al repositorio remoto

### Repositorio remoto

`git remote add origin [link repositorio]`-> agregar origen remoto de los archivos  
`git branch -M main`-> cambiar el nombre de la rama master a main   
`git push -u origin main` -> enviar archivos a repositoria remoto  
`git pull origin master --allow-unrelated-histories`->traer archivos remotos ignorando commits  
`git pull origin main`->traer archivos remotos  
`git push origin nombre-rama`->enviar rama a repositorio remoto 

### SSH

`ssh-keygen -t rsa -b 4096 -C "tu@email.com"`->crear Llave
`eval $(ssh-agent -s)`-> Encedel el "servidor" de llaves SSH de tu computadora  
`ssh-add ruta-donde-guardaste-tu-llave-privada`-> añadir la llave SSH a el "Servidor"  
`git remote set-url origin url-ssh-del-repositorio-en-github`-> conectar github por ssh

## Tags

se copia el hash del commit
`git tag -a nombre-del-tag id-del-commit`->crea un nuevo tag y la asigna a un commit  
`git tag -d nombre-del-tag`->Borrar un tag en el repositorio local  
`git tag o git show-ref --tags`->Listar los tags de nuestro repositorio local  
`git push origin --tags`->Publicar un tag en el repositorio remoto  
`git tag -d nombre-del-tag y git push origin :refs/tags/nombre-del-tag`-> Borrar un tag del repositorio remoto  



### Comandos utiles

`alias [nombre-escigido]="[comando_git]"`=hacer que un comando asuma un nombre para no escribirlo  
`gitk`->ver gráficamente nuestro entorno y flujo de trabajo local con Git usando el comando
