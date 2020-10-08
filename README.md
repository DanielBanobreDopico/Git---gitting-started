# Git: gitting started

## Contenidos
1. [Crendo un proyecto en GitHub y sincronizandolo en nuestro equipo.](#crendo-un-proyecto-en-github-y-sincronizandolo-en-nuestro-equipo)

1. [Evitando que determinados contenidos pasen de nuestro ordenador al repositorio](#evitando-que-determinados-contenidos-pasen-de-nuestro-ordenador-al-repositorio)
1. [Subiendo cambios al repositorio en GitHub](#subiendo-cambios-al-repositorio-en-github)
1. [Eliminando contenidos del repositorio](#eliminando-contenidos-del-repositorio)
1. [Creando un repositorio vacío en GitHub y poblándolo con los contenidos de una carpeta preexistente.](#creando-un-repositorio-vaco-en-github-y-poblndolo-con-los-contenidos-de-una-carpeta-preexistente)

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
$ git add .
$ git commit -m "Tus comentarios a los cambios"
$ git push
```
## Eliminando contenidos del repositorio
Si deseamos eliminar ficheros que ya no forman parte del proyecto o hemos sincronizado al repositorio por error podemos usar `git rm --cached`.
```bash
$ git rm --cached "CosaParaBorrarDelRepo"
```
El parámetro `--cached` hace que elimine los contenidos del repositorio sin eliminarlos de nuestro ordenador.
Si omitimos este parámetro, eliminaremos lo que sea no del repositorio sino del universo.
```bash
$ git rm --cached "CosaParaBorrarDelUniverso".
```
En cualquier caso, los cambios serán aplicados al repositorio dentro del próximo `commit`.
## Creando un repositorio vacío en GitHub y poblándolo con los contenidos de una carpeta preexistente.
Cuando ya tenemos un proyecto en nuestro ordenador y queremos publicarlo en GitHub, podemos hacerlo creando un repositorio vacío.
1. Crearemos el repositorio sin marcar opciones de `.gitignore` ni `README.md`. Copiamos la URL del repositorio.
1. Abrimos un terminal en la carpeta de nuestro proyecto y la inicializamos como repositorio de git:
```bash
$ git init
```
3. Configuramos nuestra identidad para el proyecto:
```bash
$ git config user.name "Tu Nombre"
$ git config user.email "tu@corr.eo"
```
4. Configuramos la dirección del repositorio de GitHub para el proyecto con la URL obtenida en el paso 1.
```bash
$ git remote add origin https://github.com/TuUsuario/TuRepositorio.git
```
5. De ser necesario, establecemos los contenidos a ignorar. Creamos el fichero `.gitignore`:
```bash
$ touch .gitignore
```
6. Editamos su contenido con nuestro editor de código preferido:
```bash
**/node_modules/
secrets.txt
```
7. Preparamos el envío inicial del proyecto. Seleccionamos los ficheros a incluir en el repositorio, establecemos el `commit` y realizamos el primer `push` estableciendo `master` como la rama de destino.
```bash
$ git add .
$ git commit -m "Aportación inicial"
$ git push --set-upstream origin master
```
Una vez realizado este proceso inicial, podremos manejar nuestro proyecto de la forma habitual.