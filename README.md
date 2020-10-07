# Git: gitting started

## Crendo un proyecto en GitHub y sincronizandolo en nuestro equipo.

1. Creamos el repositorio en GitHub y copiamos la URL del mismo
1. Clonamos el proyecto en nuestro ordenador:
```bash
$ git clone https://github.com/TuCuentaDeUsuario/TuRepositorio.git
```
3. En la carpeta que se ha creado en la clonación configuramos los datos para sicronizar nuestros cambios:
```bash
$ git config user.name "Tu Nombre"
$ git config user.email "tu@corr.eo"
```
## Evitando que determinados contenidos pasen de nuestro ordenador al repositorio
Hemos de crear un nuevo fichero `.gitignore` en la carpeta del proyecto.
```bash
$ touch .gitignore
```
Edita el fichero con la misma aplicación que emplees para escribir código y añade las rutas de los ficheros y carpetas que no desees sincronizar.
```bash
/node_modules/
secrets.txt
```
## Subiendo cambios al repositorio en GitHub
```bash
$ git add *
$ git commit -m "Tus comentarios a los cambios"
$ git push
```
## Eliminando contenidos del repositorio
Si deseamos eliminar ficheros que ya no forman parte del proyecto o hemos sincronizado al repositorio por error podemos usar `git rm --cached`
```bash
$ git rm --cached "DirectorioABorrar"
```
El parámetro `--cached` hace que elimine los contenidos del repositorio sin eliminarlos de nuestro ordenador.
