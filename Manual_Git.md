# MANUAL GIT
![Git](Fotos/Manual_Git/Git_logo.png)

1. [Introducción a Git](#introducción-a-git)
2. [Creación y actualización de repositorios](#creación-y-actualización-de-repositorios)
3. [Historial de cambios](#historial-de-cambios)
4. [Deshacer cambios](#deshacer-cambios)
5. [Gestión de ramas](#gestión-de-ramas)
6. [Repositorios remotos](#repositorios-remotos)

## Introducción a Git
---
### ¿Qué es Git?
[Git](https://git-scm.com/) es un SCV [^SCV] (Sistema de Control de Versiones) de código abierto ideado por Linus Torvalds (padre del sistema operativo **Linux**) y actualmente es el sistema de control de versiones más extendido.

A diferencia de otros SCV, Git tiene una arquitectura *distribuida*, lo que significa que en lugar de guardar todos los cambios de un proyecto en un único sitio, cada usuario contiene una copia del repositorio con el historial de cambios completo del proyecto. Esto aumenta significativamente su rendimiento.

### Configuración de Git
Antes de empezar a usar Git es necesario configurarlo con el nombre de usuario y su correo electrónico.
~~~~ bash
git config --global user.name "Your-Full-Name"       # Establecer el nombre de usuario
git config --global user.email "your-email-address"  # Establecer el correo del usuario
git config --global color.ui auto                    # Activar el coloreado de la salida
git config --global merge.conflictstyle diff3        # Mostrar el estado original en los conflictos
git config --list                                    # Mostrar la configuración
~~~~

## Creación y actualización de repositorios
---
### Creación de un repositorio
~~~~ bash
git init <nombre-repositorio>                        # Crea un repositorio nuevo con el nombre <nombre-repositorio>
~~~~
Este comando crea una nueva carpeta con el nombre del repositorio, que a su vez contiene otra carpeta oculta llamada *.git* que contiene la base de datos donde se registran los cambios en el repositorio.

### Clonación de un repositorio
~~~~ bash
git clone <url-repositorio>  # Crea una copia local del repositorio ubicado en la dirección <url-repositorio>
~~~~
A partir de que se hace la copia, los dos repositorios, el original y la copia, son independientes, es decir, cualquier cambio en uno de ellos no se verá reflejado en el otro.

### Añadir cambios a un repositorio
Cualquier cambio que hagamos en un proyecto tiene que pasar por tres estados hasta que guarde definitivamente en el repositorio.
1. **Directorio de trabajo** : directorio que contiene una copia de una versión concreta del proyecto en la que se está trabajando. Puede contener ficheros que no pertenecen al repositorio.

~~~~ bash
git add <fichero>  # Añade los cambios en el fichero <fichero> del directorio de trabajo a la zona de intercambio temporal.
git add <carpeta>  # Añade los cambios en todos los ficheros de la carpeta <carpeta> del directorio de trabajo a la zona de intercambio temporal.
git add .          # Añade todos los cambios de todos los ficheros no guardados aún en la zona de intercambio temporal.
~~~~

2. **Zona temporal de intercambio (*staging area*)** : zona donde se guardan los cambios temporalmente desde el directorio de trabajo antes de hacerlos definitivos y registrarlos en el repositorio.

~~~~ bash
git commit -m "mensaje"          # Confirma todos los cambios de la zona de intercambio temporal añadiéndolos al repositorio y creando una nueva versión del proyecto. "mensaje" es un breve mensaje describiendo los cambios realizados que se asociará a la nueva versión del proyecto.
git commit --amend -m "mensaje"  # Cambia el mensaje del último commit por el nuevo mensaje "mensaje".
~~~~

3. **Repositorio** : donde finalmente se guardan los cambios confirmados desde la zona temporal de intercambio.

![](Fotos/Manual_Git/git-add-commit.png)

### Registro de cambios
Para guardar los cambios en un repositorio Git utiliza una estructura de tres niveles:

- **Commit** : Contiene información sobre el autor, el momento y el mensaje de los cambios.
- **Árbol (*tree*)** : Cada *commit* contiene además un árbol donde se registran los nombres y rutas de los ficheros en el repositorio cuando se hizo el *commit*.
- **Blob (*binary file object*)** : Para cada uno de los ficheros listados en el árbol hay un *blob*, que contiene una instantánea comprimida del contenido del fichero cuando se hizo el *commit*.

> ℹ️ Si un fichero del repositorio no ha cambiado en el commit, el árbol apunta al blob del fichero del último commit donde el fichero cambió.

![](Fotos/Manual_Git/git-commit-tree-blob.png)

### Referenciar a un commit
Cada *commit* tiene asociado un código *hash* de 40 caracteres hexadecimales que lo identifica de manera única. Hay dos formas de referirse a un *commit*:
- **Nombre absoluto** : Se utiliza su código *hash* (basta indicar los 4 o 5 primeros dígitos).
- **Nombre relativo** : Se utiliza la palabra *HEAD* para referirse siempre al último *commit*. Para referirse al penúltimo *commit* se utiliza *HEAD~1*, al antepenúltimo *HEAD~2*, etc.

## Historial de cambios
---
### Mostrar el estado de un repositorio
~~~~ bash
git status  # Muestra el estado de los cambios en el repositorio desde la última versión guardada.
~~~~
> ❗ En particular, muestra los ficheros con cambios en el directorio de trabajo que no se han añadido a la zona de intercambio temporal y los ficheros en la zona de intercambio temporal que no se han añadido al repositorio.

### Mostrar el historial de versiones de un repositorio
~~~~ bash
git log            # Muestra el historial de commits (hash, autor, fecha, hora y mensaje asociado) de un repositorio ordenado cronológicamente.
git log --oneline  # Muestra cada commit en una línea produciendo una salida más compacta.
git log --graph    # Muestra la historia en forma de grafo.
~~~~

### Mostrar los datos de un commit
~~~~ bash
git show           # Muestra el usuario, día, hora y mensaje del último commit, así como las diferencias con el anterior.
git show <commit>  # Muestra el usuario, día, hora y mensaje del commit indicado, así como las diferencias con el anterior.
~~~~

### Mostrar el historial de cambios de un fichero
~~~~ bash
git annotate  # Muestra el contenido de un fichero anotando cada línea con información del commit en el que se introdujo.
~~~~
> ℹ️ Cada línea de la salida contiene los 8 primeros dígitos del código *hash* del *commit* correspondiente al cambio, el autor de los cambios, la fecha, el número de línea del fichero y el contenido de la línea.

### Mostrar las diferencias entre versiones
~~~~ bash
git diff           # Muestra las diferencias entre el directorio de trabajo y la zona de intercambio temporal.
git diff --cached  # Muestra las diferencias entre la zona de intercambio temporal y el último commit.
git diff HEAD      # Muestra la diferencia entre el directorio de trabajo y el último commit.
~~~~

## Deshacer cambios
---
### Eliminar cambios del directorio de trabajo o volver a una versión anterior
~~~~ bash
git checkout <commit> -- <file>  # Actualiza el fichero <file> a la versión correspondiente al commit <commit>.
~~~~
> ℹ️ Suele utilizarse para eliminar los cambios en un fichero que no han sido guardados aún en la zona de intercambio temporal, mediante el comando *git checkout HEAD -- \<file>*

### Eliminar cambios de la zona de intercambio temporal
~~~~ bash
git reset <fichero>  # Elimina los cambios del fichero <fichero> de la zona de intercambio temporal, pero preserva los cambios en el directorio de trabajo.
~~~~
> ℹ️ Para eliminar por completo los cambios de un fichero que han sido guardados en la zona de intercambio temporal hay que aplicar este comando y después *git checkout HEAD -- \<fichero>*.

### Eliminar cambios de un commit
~~~~ bash
git reset --hard <commit>  # Elimina todos los cambios desde el commit <commit> y actualiza el HEAD este commit.
~~~~
> ℹ️ Suele usarse para eliminar todos los cambios en el directorio de trabajo desde el último *commit* mediante el comando *git reset --hard HEAD*.  
> ⚠️ Usar con cuidado este comando pues los cambios posteriores al *commit* indicado se pierden por completo.
~~~~ bash
git reset <commit>  # Actualiza el HEAD al commit <commit>.
~~~~
> ℹ️ Elimina todos los *commits* posteriores a este *commit*, pero no elimina los cambios del directorio de trabajo.


## Gestión de ramas
---
Inicialmente cualquier repositorio tiene una única rama llamada *master* donde se van sucediendo todos los *commits* de manera lineal.

Una de las característica más útiles de Git es que permite la creación de ramas para trabajar en distintas versiones de un proyecto a la vez. Esto es muy útil si, por ejemplo, se quieren añadir nuevas funcionalidades al proyecto sin que interfieran con lo desarrollado hasta ahora. Cuando se termina el desarrollo de las nuevas funcionalidades, las ramas se pueden fusionar para incorporar lo cambios al proyecto principal.

### Creación de ramas
~~~~ bash
git branch <rama>  # Crea una nueva rama con el nombre <rama> en el repositorio a partir del último commit, es decir, donde apunte HEAD.
~~~~
Al crear una rama a partir de un commit, el flujo de commits se bifurca en dos de manera que se pueden desarrollar dos versiones del proyecto en paralelo.

![](Fotos/Manual_Git/git-branch.png)

![](Fotos/Manual_Git/git-branches.png "Desarrollo en ramas diferentes")

### Listado de ramas
~~~~ bash
git branch             # Muestra las ramas activas de un repositorio indicando con * la rama activa en ese momento.
git log --graph --all  # Muestra el historial del repositorio en forma de grafo incluyendo todas las ramas.
~~~~

### Cambio de ramas
~~~~ bash
git checkout <rama>     # Actualiza los ficheros del directorio de trabajo a la última versión del repositorio correspondiente a la rama <rama> y la activa (HEAD pasa a apuntar al último commit de esta rama).
git checkout -b <rama>  # Crea una nueva rama con el nombre <rama> y la activa.
~~~~
> ℹ️ Este comando es equivalente aplicar los comandos *git branch \<rama>* y *git checkout \<rama>*.

### Fusión de ramas
~~~~ bash
git merge <rama>  # Integra los cambios de la rama <rama> en la rama actual a la que apunta HEAD.
~~~~

![](Fotos/Manual_Git/git-merge.png)

> ❗ **Resolución de conflictos**  
> Para fusionar dos ramas es necesario que no haya conflictos entre los cambios realizados a las dos versiones del proyecto. Si en ambas versiones se han hecho cambios sobre la misma parte de un fichero, entonces se produce un conflicto y es necesario resolverlo antes de poder fusionar las ramas.
> 
> La resolución debe hacerse manualmente observando los cambios que interfieren y decidiendo cuales deben prevalecer, aunque existen herramientas como *KDif3* o *meld* que facilitan el proceso.

### Reorganización de ramas
~~~~ bash
git rebase <rama-1> <rama-2>  # Replica los cambios de la rama <rama-2> en la rama <rama-1> partiendo del ancestro común de ambas ramas.
~~~~
> ℹ️ El resultado es el mismo que la fusión de las dos ramas pero la bifurcación de la *\<rama-2>* desaparece ya que sus *commits* pasan a estar en la *\<rama-1>*.

### Eliminación de ramas
~~~~ bash
git branch -d <rama>  # Elimina la rama de nombre <rama> siempre y cuando haya sido fusionada previamente.
git branch -D <rama>  # Elimina la rama de nombre <rama> incluso si no ha sido fusionada.
~~~~
> ⚠️ Si la rama no ha sido fusionada previamente se perderán todos los cambios de esa rama.

## Repositorios remotos
---
La otra característica de Git, que unida a las ramas, facilita la colaboración entre distintos usuarios en un proyecto son los repositorios remotos.

Git permite la creación de una copia del repositorio en un servidor git en internet. La principal ventaja de tener una copia remota del repositorio, a parte de servir como copia de seguridad, es que otros usuarios pueden acceder a ella y hacer también cambios.

Existen muchos proveedores de alojamiento para repositorios Git pero el más usado es [GitHub](https://github.com/).

![GitHub](Fotos/Manual_Git/GitHub_logo.png)

### Añadir un repositorio remoto
~~~~ bash
git remote add <repositorio-remoto> <url>  # Crea un enlace con el nombre <repositorio-remoto> a un repositorio remoto ubicado en la dirección <url>.
~~~~
> ❗ Cuando se añade un repositorio remoto a un repositorio, Git seguirá también los cambios del repositorio remoto de manera que se pueden descargar los cambios del repositorio remoto al local y se pueden subir los cambios del repositorio local al remoto.

### Lista de repositorios remotos
~~~~ bash
git remote     # Muestra un listado con todos los enlaces a repositorios remotos definidos en un repositorio local.
git remote -v  # Muestra además las direcciones url para cada repositorio remoto.
~~~~

### Descargar cambios desde un repositorio remoto
~~~~ bash
git pull <remoto> <rama>  # Descarga los cambios de la rama <rama> del repositorio remoto <remoto> y los integra en la última versión del repositorio local, en el HEAD.
git fetch <remoto>        # Descarga los cambios del repositorio remoto <remoto> pero no los integra en la última versión del repositorio local.
~~~~

### Subir cambios a un repositorio remoto
~~~~ bash
git push <remoto> <rama>  # Sube al repositorio remoto <remoto> los cambios de la rama <rama> en el repositorio local.
~~~~

[^SCV]: Es una aplicación que permite gestionar los cambios que se realizan sobre los elementos de un proyecto o repositorio, guardando así versiones del mismo en todas sus fases de desarrollo.<ul> <li>Registra cada cambio en el proyecto o repositorio, quién y cuándo lo hace, en una base de datos.</li><li>Permite volver a estados previos del desarrollo.</li><li>Permite gestionar diferentes versiones del proyecto (ramas) para trabajar en paralelo y luego fundirlas.</li><li>Permite colaborar entre diferentes usuarios en un mismo repositorio, facilitando la resolución de conflictos.</li><li>Se utiliza principalmente en proyectos de desarrollo de software, pero sirve para cualquier otro tipo de proyecto.</li></ul>

