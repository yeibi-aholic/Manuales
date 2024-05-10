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
[Git](https://git-scm.com/) es un SCV (Sistema de Control de Versiones) de código abierto ideado por Linus Torvalds (padre del sistema operativo **Linux**) y actualmente es el sistema de control de versiones más extendido.

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
### Creación de un repositorio nuevo
~~~~ bash
git init <nombre-repositorio>                        # Crea un repositorio nuevo con el nombre <nombre-repositorio>
~~~~
Este comando crea una nueva carpeta con el nombre del repositorio, que a su vez contiene otra carpeta oculta llamada *.git* que contiene la base de datos donde se registran los cambios en el repositorio.

### 


## Historial de cambios
---

## Deshacer cambios
---

## Gestión de ramas
---

## Repositorios remotos
---
