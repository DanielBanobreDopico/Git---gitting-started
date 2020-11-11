# Git: gitting started

## Contenidos

### Uso básico

1. [Crendo un proyecto en GitHub y sincronizandolo en nuestro equipo.](#crendo-un-proyecto-en-github-y-sincronizandolo-en-nuestro-equipo)

1. [Evitando que determinados contenidos pasen de nuestro ordenador al repositorio](#evitando-que-determinados-contenidos-pasen-de-nuestro-ordenador-al-repositorio)
1. [Subiendo cambios al repositorio en GitHub](#subiendo-cambios-al-repositorio-en-github)
1. [Eliminando contenidos del repositorio](#eliminando-contenidos-del-repositorio)
1. [Creando un repositorio vacío en GitHub y poblándolo con los contenidos de una carpeta preexistente.](#creando-un-repositorio-vaco-en-github-y-poblndolo-con-los-contenidos-de-una-carpeta-preexistente)

### Trabajo en equipo

6. 

## Uso básico

### Crendo un proyecto en GitHub y sincronizandolo en nuestro equipo.

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
### Evitando que determinados contenidos pasen de nuestro ordenador al repositorio
Hemos de crear un nuevo fichero `.gitignore` en la carpeta del proyecto.
```bash
$ touch .gitignore
```
Edita el fichero con la misma aplicación que emplees para escribir código y añade las rutas de los ficheros y carpetas que no desees sincronizar.
```bash
/node_modules/
secrets.txt
```
### Subiendo cambios al repositorio en GitHub
```bash
$ git add .
$ git commit -m "Tus comentarios a los cambios"
$ git push
```
### Eliminando contenidos del repositorio
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
### Creando un repositorio vacío en GitHub y poblándolo con los contenidos de una carpeta preexistente.
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

## Trabajo en equipo

Cuando trabajamos en equipo compartiendo un repositorio es necesario adoptar mecánicas de trabajo (flujos de trabajo) específicos.

### Creación del respositorio

El repositorio es creado por uno de los participantes siguiendo las mecánicas expuestas anteriormente.

Una vez creado el respositorio y poblado con los ficheros iniciales (puede ser simplemente el README.md) el creador del invitará al resto de participantes en la gestión de acceso de la configuración del respositorio.

### Clonación local del respositorio

Tras los pasos anteriores, los participantes tendrán que crear la copia del respositorio en sus equipos locales y la configuración de sus identidades en el mismo:
```bash
$ git clone https://github.com/TuCuentaDeUsuario/RepoCompartido.git
$ cd RepoCompartido
$ git config user.name "Tu Nombre"
$ git config user.email "tu@correo.es"
```
### Creación de ramas

Lo siguiente será crear una "rama" para nuestro trabajo. Las ramas permiten que la evolución del código transite por diferentes caminos sin interferirse. Esto es útil cuando se trabaja de forma individual para poder probar diferentes soluciones sin afectar a la rama principal, pero es imprescindible para que varias personas puedan trabajar en un único proyecto sin pisarse entre si.

Las ramas pueden emplearse de formas muy variadas. Cada empresa o cada equipo puede tener sus propias mecánicas definidas. Lo importante es que cada persona realice tareas definidas y que estas tareas realicen en sus ramas correspondientes para evitar interferencias y facilitar explorar diferentes soluciones.

Al crear tu propia rama, los cambios que realices no se mezclarán con el trabajo de los demás. Una vez tu tarea esté finalizada tu rama podrá fusionarse con la rama principal y de esa manera los cambios se incorporarán al proyecto de forma definitiva. Para la siguiente tarea podrás abrir una nueva rama.

Antes de abrir una rama:
* Asegurate de haber guardado todos los cambios en todos los ficheros.
* Asegurate de que los ficheros son coherentes dentro de tu tarea.

Ya con todo en orden crea una rama, y publicala en el respositorio compartido y empezar a trabajar sobre ella:
```bash
$ git checkout -b nombreDeMiRama
$ git push -u origin nombreDeMiRama
```
Tus cambios se realizarán en la rama que has creado, y esta rama estará accesible para tus compañeros en el repositorio. Esto último es opcional, pero te permitirá cooperar en las tareas de tus compañeros y que tus compañeros puedan participar de las tuyas.

### Accediendo al las ramas de tus compañeros

Es importante que todos los participantes en el proyecto se coodinen en la forma en que asignan nombres a sus ramas. Que no existan diferentes ramas con el mismo nombra facilita mucho las cosas.

Actualizar tu respositorio local desde el respositorio remoto para ver si existen nuevas ramas en el proyecto:

```bash
$ git fetch
$ git branch -a
```

Vamos a suponer que el resultado es algo como esto:

```bash
master
* workgroup1
remotes/origin/HEAD -> origin/master
remotes/origin/master
remotes/origin/workgroup
remotes/origin/workgroup1
```

Para acceder a la rama origin/workgroup, guarda los cambios necesarios, pon orden y a continuación:

```bash
$ git checkout workgroup
$ git config user.name "Tu Nombre"
$ git config user.email "tu@correo.es"
```

Si compruebas nuevamente las ramas disponibles, verás que se ha creado una rama local correspondiente con la remota:

```bash
master
workgroup1
* workgroup
remotes/origin/HEAD -> origin/master
remotes/origin/master
remotes/origin/workgroup
remotes/origin/workgroup1
```

Todos los cambios que realices ahora serán almacenados en tu rama local y se sincronizarán en su correspondiente remota cuando hagas un `git push` desde la rama.
### Manteniendose al día

Para trabajar en tu rama emplea los mecanismos normales: commit, push, pull, fecth, merge...

La única diferencia será que el comando que emplees afectarán a las ramas local y remota en la que estés trabajando en ese momento.

Tendrás que hacer un pull para ver el contenido actualizado de una rama de un compañero y tendrás que hacer un push en tu rama si quieres que tus compañeros puedan acceder a tu trabajo.

### Fusionando las ramas a la principal

Una vez qur hayas encontrado una solución satisfactoria o completado una taréa, que esta ha sido supervisada y se ha comprobado que todo está en orden, puedes fusionar la rama en la que has estado trabajando con la rama principal para hacer esta aportación definitiva:

```bash
$ git checkout master
$ git merge workgroup1 -m 'Incorporación de la rutina de detección de malware'
```
### Pull request

Cuando trabajas con GitHub puede solicitar la revisión y aprobación de tus aportaciones realizando un *Pull Request*.

Cuando haces un pull request indicas que quieres fusionar dos ramas y se crea un dialogo en el que tus compañeros pueden comprobar las aportaciones de dicha rama y hacer correcciones al respecto. Suele haber una persona encargada de aceptar o no los pull request y cerrarlos si es el caso.
