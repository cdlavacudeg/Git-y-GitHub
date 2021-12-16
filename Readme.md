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
`git commit -m "mensaje"`->envia cambios al repositorio con un mensaje  
`git log`-> historia de commits (+`--oneline` para ver la historia como una lista)  
`git show [arch]`->mostrar la diferencia con la version anterior

`git commit` -> escribir el mensaje y salirse con `esc+shift+z+z` vim  guardar  
`git diff [indicador del commit 1] [indicador del commit 1]`->diferencia entre dos commits  
