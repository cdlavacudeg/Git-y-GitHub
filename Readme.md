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
`git log --all --decorate --oneline --graph`->Cambios más graficos.

`[alias] lg1 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all`  

`lg2 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all`  


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

### Rebase

El comando rebase es una mala práctica, nunca se debe usar en remote(borra la historia, son cambios silenciosos). Con rebase puedes recoger todos los cambios confirmados en una rama y ponerlos sobre otra.

`git checkout experimento`-> Cambiamos a la rama que queremos traer los cambios  
`git rebase master`->Aplicamos rebase para traer los cambios de la rama que queremos  

Primero rebase a los cambios y luego a main.

### Git Stash

Cuando necesitamos regresar en el tiempo porque borramos alguna línea de código pero no queremos pasarnos a otra rama porque nos daría un error ya que debemos pasar ese “mal cambio” que hicimos a stage, podemos usar `git stash` para regresar el cambio anterior que hicimos.

`git stash` es típico cuando estamos cambios que no merecen una rama o no merecen un rebase si no simplemente estamos probando algo y luego quieres volver rápidamente a tu versión anterior la cual es la correcta.

#### Stashed:
El stashed nos sirve para guardar cambios para después, Es una lista de estados que nos guarda algunos cambios que hicimos en Staging para poder cambiar de rama sin perder el trabajo que todavía no guardamos en un commit

Ésto es especialmente útil porque hay veces que no se permite cambiar de rama, ésto porque porque tenemos cambios sin guardar, no siempre es un cambio lo suficientemente bueno como para hacer un commit, pero no queremos perder ese código en el que estuvimos trabajando.

El stashed nos permite cambiar de ramas, hacer cambios, trabajar en otras cosas y, más adelante, retomar el trabajo con los archivos que teníamos en Staging pero que podemos recuperar ya que los guardamos en el Stash.

El comando `git stash` guarda el trabajo actual del Staging en una lista diseñada para ser temporal llamada Stash, para que pueda ser recuperado en el futuro.

Para agregar los cambios al stash se utiliza el comando:

`git stash`  
Podemos poner un mensaje en el stash, para asi diferenciarlos en git stash list por si tenemos varios elementos en el stash. Ésto con:

`git stash save "mensaje identificador del elemento del stashed"`  

##### Obtener elelmentos del stash

El stashed se comporta como una Stack de datos comportándose de manera tipo LIFO (del inglés Last In, First Out, «último en entrar, primero en salir»), así podemos acceder al método pop.

El método pop recuperará y sacará de la lista el último estado del stashed y lo insertará en el staging area, por lo que es importante saber en qué branch te encuentras para poder recuperarlo, ya que el stash será agnóstico a la rama o estado en el que te encuentres, siempre recuperará los cambios que hiciste en el lugar que lo llamas.

Para recuperar los últimos cambios desde el stash a tu staging area utiliza el comando:

`git stash pop`  
Para aplicar los cambios de un stash específico y eliminarlo del stash:

`git stash pop stash@{<num_stash>}`  
Para retomar los cambios de una posición específica del Stash puedes utilizar el comando:

`git stash apply stash@{<num_stash>}`  
Donde el <num_stash> lo obtienes desden el git stash list

##### Listado de elementos en el stash
Para ver la lista de cambios guardados en Stash y así poder recuperarlos o hacer algo con ellos podemos utilizar el comando:

`git stash list`  
Retomar los cambios de una posición específica del Stash || Aplica los cambios de un stash específico

##### Crear una rama con el stash
Para crear una rama y aplicar el stash mas reciente podemos utilizar el comando

`git stash branch <nombre_de_la_rama>`  
Si deseas crear una rama y aplicar un stash específico (obtenido desde git stash list) puedes utilizar el comando:

`git stash branch nombre_de_rama stash@{<num_stash>}`  
Al utilizar estos comandos crearás una rama con el nombre <nombre_de_la_rama>, te pasarás a ella y tendrás el stash especificado en tu staging area.

##### Eliminar elementos del stash
Para eliminar los cambios más recientes dentro del stash (el elemento 0), podemos utilizar el comando:

`git stash drop`  
Pero si en cambio conoces el índice del stash que quieres borrar (mediante git stash list) puedes utilizar el comando:

`git stash drop stash@{<num_stash>}`
Donde el <num_stash> es el índice del cambio guardado.

Si en cambio deseas eliminar todos los elementos del stash, puedes utilizar:

`git stash clear`
##### Consideraciones:

El cambio más reciente (al crear un stash) SIEMPRE recibe el valor 0 y los que estaban antes aumentan su valor.
Al crear un stash tomará los archivos que han sido modificados y eliminados. Para que tome un archivo creado es necesario agregarlo al Staging Area con `git add [nombre_archivo]` con la intención de que git tenga un seguimiento de ese archivo, o también utilizando el comando `git stash -u` (que guardará en el stash los archivos que no estén en el staging).
Al aplicar un stash este no se elimina, es buena práctica eliminarlo.

### Limpiar el Repositorio

Mientras estamos trabajando en un repositorio podemos añadir archivos a él, que realmente no forma parte de nuestro directorio de trabajo, archivos que no se deberían de agregar al repositorio remoto.

El comando clean actúa en archivos sin seguimiento, este tipo de archivos son aquellos que se encuentran en el directorio de trabajo, pero que aún no se han añadido al índice de seguimiento de repositorio con el comando add.

`git clean`
La ejecución del comando predeterminado puede producir un error. La configuración global de Git obliga a usar la opción force con el comando para que sea efectivo. Se trata de un importante mecanismo de seguridad ya que este comando no se puede deshacer.

→ Revisar que archivos no tienen seguimiento.

`git clean --dry-run`  

→ Eliminar los archivos listados de no seguimiento.

`git clean -f`

### Git cherry-pick: traer commits viejos al head de un branch

Existe un mundo alternativo en el cual vamos avanzando en una rama pero necesitamos en master uno de esos avances de la rama, para eso utilizamos el comando `git cherry-pick IDCommit`.

cherry-pick es una mala práctica porque significa que estamos reconstruyendo la historia, usa cherry-pick con sabiduría. Si no sabes lo que estás haciendo ten mucho cuidado.

### Remendar un commit
Puede modificar el commit más reciente (enmendar) en la misma rama ejecutando:

`git add -A` # Para hacer uso de ammend los archivos deben de estar en staging  
`git commit --amend` # Remendar último commit  

Este comando sirve para agregar archivos nuevos o actualizar el commit anterior y no generar commits innecesarios.
.
También es una forma sencilla de editar o agregar comentarios al commit anterior porque abrirá la consola para editar el commit anterior.
.
Nota: Es una mala práctica hacer ammend de un commit que ya ha sido pusheado o pulleado del repositorio remoto, al momento de hacer ammend con algún commit que esté en remoto va a generar un conflicto que se va a arreglar haciendo un commit adicional y se perderá el beneficio del ammend.

## Readme 

[Link editor online readme](https://pandao.github.io/editor.md/en.html)
