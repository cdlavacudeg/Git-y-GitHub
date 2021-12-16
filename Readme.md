# Notas de Git

## Git Bash

`cd`-> cambiar directario (home `/`,`/c`,`/user`,`..` volver a carpeta anterior,`tab` autocompletar)  
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
`git log`-> historia de commits (+`--oneline` para ver la historia como una lista,`--stat` cambios en los archivos)  
`git show [arch]`->mostrar la diferencia con la version anterior  
`git commit` -> escribir el mensaje y salirse con `esc+shift+z+z` vim  guardar  
`git diff [indicador del commit 1] [indicador del commit 2]`->diferencia entre dos commits  

#### Branch y Merge

Las ramas permiten realizar experimentos, corregir errores y un merge une el cambio y la rama principal.

`git chekout [ind commit, master] [arch]`-> traer los cambios de una rama a local con el commit se envian los cambios a la rama master  
`git reset [ind commit]`-> volver en el tiempo a un commit anterior (+`--hard`,`--soft`) cuidado!  
