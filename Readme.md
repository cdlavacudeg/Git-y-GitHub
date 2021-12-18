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

### Forks o Bifurcaciones
Es una característica única de GitHub en la que se crea una copia exacta del estado actual de un repositorio directamente en GitHub, éste repositorio podrá servir como otro origen y se podrá clonar (como cualquier otro repositorio), en pocas palabras, lo podremos utilizar como un git cualquiera
.
Un fork es como una bifurcación del repositorio completo, tiene una historia en común, pero de repente se bifurca y pueden variar los cambios, ya que ambos proyectos podrán ser modificados en paralelo y para estar al día un colaborador tendrá que estar actualizando su fork con la información del original.
.
Al hacer un fork de un poryecto en GitHub, te conviertes en dueñ@ del repositorio fork, puedes trabajar en éste con todos los permisos, pero es un repositorio completamente diferente que el original, teniendo alguna historia en común.
.
Los forks son importantes porque es la manera en la que funciona el open source, ya que, una persona puede no ser colaborador de un proyecto, pero puede contribuír al mismo, haciendo mejor software que pueda ser utilizado por cualquiera.
.
Al hacer un fork, GitHub sabe que se hizo el fork del proyecto, por lo que se le permite al colaborador hacer pull request desde su repositorio propio.

### Trabajando con más de 1 repositorio remoto
Cuando trabajas en un proyecto que existe en diferentes repositorios remotos (normalmente a causa de un fork) es muy probable que desees poder trabajar con ambos repositorios, para ésto puedes crear un remoto adicional desde consola.

`git remote add nombre_del_remoto url_del_remoto`  
`git remote upstream [link]`  

Al crear un remoto adicional podremos, hacer pull desde el nuevo origen (en caso de tener permisos podremos hacer fetch y push)

`git pull [remoto] [rama]`  
`git pull upstream master`  

Éste pull nos traerá los cambios del remoto, por lo que se estará al día en el proyecto, el flujo de trabajo cambia, en adelante se estará trabajando haciendo pull desde el upstream y push al origin para pasar a hacer pull request.

`git pull upstream master`  
`git push origin master`  

### Git ignore

Ignorar archivos para no subirlos al repositorio (.gitignore)
Por diversas razones, no todos los archivos que agregas a un proyecto deberían guardarse en un repositorio, ésto porque hay archivos que no todo el mundo debería de ver, y hay archivos que al estar en el repositorio alentan el proceso de desarrollo (por ejemplo los binary large objects, blob, que se tardan en descargarse).
.
Para que no se suban estos archivos no deseados se puede crear un archivo con el nombre .gitignore en la raíz del repositorio con las reglas para los archivos que no se deberían subir (ver [sintaxis de los .gitignore](https://git-scm.com/docs/gitignore)).


Las razones principales para tomar la decisión de no agregar un archivo a un repositorio son:

Es un archivo con contraseñas (normalmente con la extensión .env)
Es un blob (binary large object, objeto binario grande), mismos que son difíciles de gestionar en git.
Son archivos que se generan corriendo comandos, por ejemplo la carpeta node_modules que genera npm al correr el comando npm install

## Readme 

[Link editor online readme](https://pandao.github.io/editor.md/en.html)