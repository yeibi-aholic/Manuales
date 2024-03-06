# MANUAL LaTeX

1. **[INTRODUCCIÓN](#1-introducción)**
    1. [¿Qué es *TeX*?](#11-qué-es-tex)
    2. [¿Qué es *LaTeX*?](#12-qué-es-latex)
    3. [Instalación](#13-instalación)
    4. [Hola LaTeX](#14-hola-latex)
        1. [Compilación](#141-compilación)
2. **[ESTRUCTURA DE UN DOCUMENTO](#2-estructura-de-un-documento)**
    1. [Esqueleto básico para *pdflatex*](#21-esqueleto-básico-para-pdflatex)
        1. [Clase de un documento](#211-clase-de-un-documento)
        2. [Preámbulo](#212-preámbulo)
        3. [Cuerpo](#213-cuerpo)
    2. [Esqueleto básico para *xelatex*](#22-esqueleto-básico-para-xelatex)
3. **[SECCIONES Y PÁRRAFOS](#3-secciones-y-párrafos)**
    1. [Secciones y subsecciones](#31-secciones-y-subsecciones)
    2. [Párrafos y cambios de línea](#32-párrafos-y-cambios-de-línea)
    3. [Justificación](#33-justificación)
4. **[FORMATEO BÁSICO](#4-formateo-básico)**
    1. [Negrita, cursiva y subrayado](#41-negrita-cursiva-y-subrayado)
    2. [Familias de tipos de letra](#42-familias-de-tipos-de-letra)
    3. [Perfiles de letra](43-perfiles-de-letra)
    4. [Tamaños de letra](44-tamaños-de-letra)
5. **[LISTAS](#5-listas)**
6. **[TABLAS](#6-tablas)**
7. **[IMÁGENES](#7-imágenes)**
8. **[FÓRMULAS MATEMÁTICAS](#8-fórmulas-matemáticas)**
    1. Símbolos matemáticos
        1. Letras griegas
        2. Operadores aritméticos
        3. Relaciones
        4. Operadores binarios
        5. Lógica
        6. Conjuntos
        7. Flechas
        8. Puntos suspensivos
        9. Otros símbolos
        10. Funciones
    2. Subíndices y superíndices
    3. Fracciones
    4. Sumatorios, productorios e integrales
    5. Sombreros
    6. Matrices
    7. Teoremas
9. **[ENTORNOS FLOTANTES](#9-entornos-flotantes)**
    1. Entorno flotante para figuras
    2. Entorno flotante para tablas
10. **[REFERENCIAS CRUZADAS Y NOTAS A PIE](#referencias-cruzadas-y-notas-a-pie)**
    1. Referencias cruzadas
    2. Notas a pie de página
11. **[CITAS Y REFERENCIAS BIBLIOGRÁFICAS](#11-citas-y-referencias-bibliográficas)**
12. **[DISEÑO DE PÁGINA](#12-diseño-de-página)**
    1. Dimensiones y márgenes
    2. Encabezados y pies de página

## 1. INTRODUCCIÓN
---
### 1.1. ¿Qué es *TeX*?
*TeX* es un sistema de composición de documentos de alta calidad, orientado especialmente a la creación de documentos científicos y técnicos que incluyen fórmulas matemáticas. Fue creado por ***Donald Knuth*** en **1978**.

A diferencia de un procesador de textos como por ejemplo *Microsoft Word*, *TeX* no es una aplicación sino un lenguaje de programación que require compilar el código fuente para obtener el documento final. Esto, que a priori podría parecer una desventaja, en realidad es la gran ventaja de *TeX* frente a los procesadores de texto que siguen el paradigma WYSIWYG (What You See Is What You Get), ya que permite separar fácilmente el contenido y la estructura de un documento, de su formato, de manera que el usuario puede centrarse en el contenido y la estructura del documento, y dejar que *TeX* se encargue del formato. De hecho, *TeX* incorpora un potente lenguaje de marcado para estructurar y formatear el texto de un documento. Por ejemplo, mientras que para poner una palabra en negrita con un procesador de textos como *Microsoft Word*, bastaría con seleccionar la palabra y hacer clic en el botón de negrita para ver automáticamente la palabra en negrita en la pantalla del ordenador, en *TeX* habría que escribir en el fichero con el código fuente ***{\bf palabra}*** y después compilar el código fuente para obtener un documento final con la palabra en negrita (el comando ***\bf***, que permite aplicar la negrita, se conoce como marca o tag en inglés.) La página principal con información sobre *TeX* es la del [TeX Users Group](https://www.tug.org/).

### 1.2. ¿Qué es *LaTeX*?
![LaTeX](Fotos/Manual_LaTeX/Introducción/LaTeXLogo.PNG)

*LaTeX* es un conjunto de macros para *TeX* debido originalmente a ***Leslie Lamport*** para facilitar el uso de *TeX*.

Tanto *TeX* como *LaTeX* son programas de código abierto, liberados bajo la licencia *LPPL*. Otra de las grandes ventajas de *LaTeX* es que existen multitud de paquetes de código libre
para generar distintos tipos de documentos que pueden descargarse desde el repositorio *[CTAN](https://ctan.org/)*.

La página principal sobre *LaTeX* es [The LaTeX project](https://www.latex-project.org/)

### 1.3. Instalación
Existen distintas distribuciones de *LaTeX* y algunas de ellas son multiplataforma, es decir, están disponibles para diferentes sistemas operativos. Las distribuciones más comunes son:
- *[TeXLive](https://www.tug.org/texlive/)* para *Windows*, *Mac OSX* y *Linux*.
- *[MiKTeX](https://miktex.org/)* para *Windows*, *Mac OSX* y *Linux*.
- *[MacTeX](https://www.tug.org/mactex/)* para *Mac OSX*.
> En sus respectivas páginas está explicado el procedimiento de instalación de cada una.

Junto a la distribución de *LaTeX* es también habitual instalar algún editor de texto para escribir el código fuente. En realidad puede usarse cualquier editor de texto que ya esté instalado en nuestro sistema operativo, pero los existen entornos de edición especializados que facilitan muchas de las tareas del proceso de composición de documentos con *LaTeX*. Los más comunes son:
- *[TeXmaker](https://www.xm1math.net/texmaker/)* - Es un editor de texto libre, multiplataforma, con muchos asistentes disponibles que permite previsualizar en tiempo real el documento final en *pdf*.
- *[TeXstudio](https://www.texstudio.org/)* - Es otro editor libre y multiplataforma que incorpora aún más asistentes que el anterior.
- *[Vim](https://www.vim.org/)* - Es un editor de texto simple de propósito general que también es libre y multiplataforma. Incorpora paquetes o plugins específicos para facilitar la creación de documentos con *LaTeX*. Especialmente indicado para trabajar desde la terminal.
- *[Emacs](https://www.gnu.org/software/emacs/)* - Es otro editor similar a *Vim*, muy extendido entre los usuarios que prefieren usar la terminal.
- *[Visual Studio Code](https://code.visualstudio.com/)* - Es un potente entorno de desarrollo multipropósito. Dispone de paquetes para los lenguajes de programación más comunes, entre ellos *LaTeX*.

Pero también se puede empezar a componer documentos sin necesidad de instalar nada en el ordenador, usando un editor on-line como por ejemplo *[Overleaf](https://www.overleaf.com/)*.

### 1.4. Hola LaTeX
A modo de ejemplo, empezaremos por crear un sencillo documento con el texto *“Hola LaTeX”*.

Para ello utilizaremos nuestro editor de texto preferido para crear un fichero de texto con el nombre *main.tex* y el siguiente contenido:
~~~~ latex
\documentclass{article}
\usepackage[spanish]{babel}
\begin{document}
Hola \LaTeX
\end{document}
~~~~
> ❗ **IMPORTANTE:** El nombre del fichero de texto con el código fuente de *LaTeX* puede ser el que queramos, pero es importante que la extensión sea *.tex*.

Aunque más adelante se verá la estructura general del código fuente de un documento en *LaTeX*, a continuación se explica brevemente el contenido de este fichero:
1. En la primera línea se especifica el tipo de documento (**article**).
2. En la segunda línea se especifica el idioma del documento (**spanish**).
3. La tercera línea marca el comienzo del documento.
4. La cuarta línea contiene el texto del documento. ***\LaTeX*** es un comando que produce la salida *LaTeX*.
5. La quinta línea marca el final del documento.

#### 1.4.1. Compilación
Para obtener el documento final hay que compilar el fichero fuente. Existen diferentes formas de hacerlo y en los editores anteriores suele ser tan sencillo como hacer clic en un botón o pulsar una combinación de teclas, pero en última instancia todos ellos hacen una llamada al compilador de *LaTeX* que es quien se encarga de convertir el código fuente en el documento final.
Cada distribución de *LaTeX* viene con varios compiladores. Los más habituales son:
- *latex* - Es el compilador más antiguo y genera documentos en formato *dvi*, que es un formato independiente creado mucho antes que el formato *pdf*.
- *[pdflatex](https://www.tug.org/applications/pdftex/)* - Es el compilador más usado y genera documentos en formato *pdf*.
- *[xelatex](https://tug.org/xetex/)* - Es un compilador más moderno que admite caracteres *Unicode* en el código fuente y el uso de tipografías más modernas.

En una terminal, la compilación de este documento sería tecleando el comando ***latex main.tex***, ***pdflatex main.tex*** o ***xelatex main.tex***, dependiendo del compilador que
se quiera usar. A continuación se muestra la salida que general el compilador *pdflatex* al compilar el fichero *main.tex*.
~~~~
> pdflatex main.tex
s is pdfTeX, Version 3.141592653-2.6-1.40.22 (TeX Live 2021) (preloaded
format=pdflatex) restricted \write18 enabled.
entering extended mode
(./main.tex
LaTeX2e <2021-06-01> patch level 1
L3 programming layer <2021-06-18>
(/usr/local/texlive/2021/texmf-dist/tex/latex/base/article.cls
Document Class: article 2021/02/12 v1.4n Standard LaTeX document class
(/usr/local/texlive/2021/texmf-dist/tex/latex/base/size10.clo))
(/usr/local/texlive/2021/texmf-dist/tex/generic/babel/babel.sty
(/usr/local/texlive/2021/texmf-dist/tex/generic/babel/babel.def
(/usr/local/texlive/2021/texmf-dist/tex/generic/babel/txtbabel.def))
(/usr/local/texlive/2021/texmf-dist/tex/generic/babel-spanish/spanish.ldf))
(/usr/local/texlive/2021/texmf-dist/tex/latex/l3backend/l3backend-pdftex.def)
(./main.aux) [1{/usr/local/texlive/2021/texmf-var/fonts/map/pdftex/updmap/
pdftex.map}] (./main.aux) )</usr/local/texlive/2021/texmf-dist/fonts/type1/
public/amsfonts/cm/cmr10.pfb></usr/local/texlive/2021/texmf-dist/fonts/type1/
public/amsfonts/cm/cmr7.pfb>
Output written on main.pdf (1 page, 20106 bytes).
Transcript written on main.log.
~~~~

##### Ejemplo
Si en el documento anterior cambiamos el comando ***\LaTeX*** por otro que no existe, por ejemplo ***\error***, al compilar el documento tendremos el siguiente error.
~~~~
> pdflatex main.tex
This is pdfTeX, Version 3.141592653-2.6-1.40.22 (TeX Live 2021) (preloaded format=pdflatex) restricted \write18 enabled.
entering extended mode
(./main.tex
LaTeX2e <2021-06-01> patch level 1
L3 programming layer <2021-06-18>
(/usr/local/texlive/2021/texmf-dist/tex/latex/base/article.cls
Document Class: article 2021/02/12 v1.4n Standard LaTeX document class
(/usr/local/texlive/2021/texmf-dist/tex/latex/base/size10.clo))
(/usr/local/texlive/2021/texmf-dist/tex/latex/l3backend/l3backend-pdftex.def)
(./main.aux)
! Undefined control sequence.
l.6 Ejemplo de documento con un error. \error
~~~~
> ⚠️ **ADVERTENCIA:** Si el documento contiene referencias cruzadas, citaciones bibliográficas, tabla de contenidos o índices, es necesario compilar el documento dos o tres veces para que se generen automáticamente esas partes.

## 2. ESTRUCTURA DE UN DOCUMENTO
---
### 2.1. Esqueleto básico para *pdflatex*
El esqueleto básico del código fuente de un documento en español para compilar con *latex* o *pdflatex* es el siguiente:
~~~~ latex
% CLASE
\documentclass[a4paper,10pt]{article}

% PREÁMBULO
% Paquetes
\usepackage[utf8]{inputenc}
\usepackage[spanish]{babel}
\usepackage[T1]{fontenc}

% Título, autor y fecha
\title{Título}
\author{Autor}
\date{Fecha}

% CUERPO
\begin{document}

\maketitle

% Resumen
\begin{abstract}
Contenido del resumen
\end{abstract}

% Tabla de contenidos
\tableofcontents

Contenido del documento

\end{document}
~~~~
![](Fotos/Manual_LaTeX/2_Estructura_de_un_documento/pdflatex.PNG)

Antes de explicar las distintas partes de este esqueleto conviene mencionar varias cosas sobre la sintaxis de algunos elementos básicos:
- **Comandos** - Los comandos comienzan siempre por la barra invertida (backslash) ***\\***. En muchas ocasiones van acompañados de argumentos obligatorios que se escriben entre llaves {...} y opcionales que se escriben entre corchetes [...].
- **Entornos** - Los entornos, a diferencia de los comandos, son bloques de código sobre los que se aplica alguna acción, y están delimitados siempre por un comando de apertura ***\begin{entorno}*** y otro de cierre ***\end{entorno}***.
- **Comentarios** - Al igual que en otros lenguajes del programación se pueden hacer comentarios en el código fuente que no serán interpretados por el compilador. Para ello se utiliza el símbolo de porcentaje ***%*** al comienzo del comentario.
- **Símbolos reservados** - Existe una serie de símbolos que están reservados para funciones especiales:  
    + ***\\*** : Indica el inicio de un comando.
    + ***$*** : Declara el entorno matemático.
    + ***{ }*** : Inicia y finaliza un grupo.
    + ***#*** : Indica el número de un argumento en la definición de comandos.
    + ***%*** : Indica el inicio de un comentarios.
    + ***&*** : Separa elementos en una tabla o fórmula.
    + ***ˆ*** : Escribe un superíndice.
    + ***_*** : Escribe un subíndice.
    + ***~*** : Indica por dónde se puede partir una palabra al final de una línea.
  
Para que aparezcan estos caracteres en el documento final es necesario escribirlos en el código fuente precedidos por la barra invertida (***\$, \{, \}, \#, \%, \&, \ˆ, \_, \~***) excepto la barra invertida que se
escribe con el comando ***\backslash***.

#### 2.1.1. Clase de un documento
La primera línea de un fichero con código *LaTeX* indica la clase de documento que se va a generar mediante el comando ***\documentclass***. En el ejemplo aparece un argumento obligatorio que indica el tipo de documento que se desea crear, artículo (**article**), pero se pueden crear otros tipos de documentos como informes (**report**), libros (**book**) o cartas (**letter**). Y también aparecen dos argumentos opcionales, **a4paper** que indica el tamaño de la hoja en el documento final (**a4**), y **10pt** que indica el tamaño base de la fuente utilizada en el documento (existe también **11pt** y **12pt**).

#### 2.1.2. Preámbulo
El preámbulo es la parte que va después de la clase y antes del comienzo del cuerpo del documento. En parte suele utilizarse para la carga de los paquetes de macros que se van a utilizar en el documento y la configuración del documento. En el ejemplo el preámbulo comienza con la carga de tres paquetes mediante el comando ***\usepackage***: el paquete inputenc que permite definir la codificación de los caracteres del código fuente (conviene utilizar la codificación **utf8** sobre todo si se van a utilizar caracteres no **ASCII**); el paquete babel que permite definir el idioma del documento (**spanish**); y el paquete **fontenc** que especifique las codificaciones [^1] de las fuentes (**T1**).

A continuación, se suelen configurar algunos aspectos del documento como podrían ser los márgenes, encabezados y pies, el título, autor y fecha, y otras muchas posibilidades.

En el preámbulo también se pueden definir nuevos comandos *LaTeX* o redefinir los ya existentes.

#### 2.1.3. Cuerpo
Contiene el texto del cuerpo del documento y tiene que ir dentro del entorno document. Suele empezar con el comando ***\maketitle*** si se desea empezar el documento con el título, autor y fecha que se hayan definido previamente en el preámbulo, y le sigue el comando ***\tableofcontents*** que introduce la tabla de contenidos en el documento. Finalmente iría el texto en sí con el contenido del documento.

### 2.2. Esqueleto básico para *xelatex*
Si se va a utilizar el compilador *xelatex* los paquetes del preámbulo cambian y deberían utilizarse los siguientes:
~~~~ latex
% Paquetes
\usepackage{fontspec}
\setmainfont{Times New Roman}
\usepackage{polyglossia}
\setdefaultlanguage{spanish}
~~~~

El paquete **fontspec** permite definir las fuentes tipográfica que se desean utilizar en el documento final (por ejemplo *Times New Roman*), que debe estar instalada en el sistema donde se compile el documento, y el paquete **polyglossia** permite definir el idioma del documento.

[^1]: Una codificación de fuente es un mapeo de los códigos de caracteres a los glifos de la fuente que se utilizan para componer su salida.

## 3. SECCIONES Y PÁRRAFOS
---
### 3.1. Secciones y subsecciones
Normalmente un documento extenso se dividirá en secciones y subsecciones (o incluso capítulos si se trata de un libro). Para definir las secciones de un documento se utilizan los siguientes comandos:
- ***\chapter{Título del capítulo}*** - Crea un nuevo capítulo con el título indicado y lo numera. Solo puede usarse cuando la clase del documento es book.
- ***\section{Título de la sección}*** - Crea una nueva sección con el título indicado y la numera.
- ***\subsection{Título de la subsección}*** - Crea una nueva subsección con el título indicado y la numera.
- ***\subsubsection{Título de la subsubsección}*** - Crea una nueva subsubsección con el título indicado y la numera.

Las secciones definidas con estos documentos aparecerán en la tabla de contenidos automáticamente.

Existen versiones alternativas de estos comandos añadiendo un asterisco (***\chapter\*, \section\*, \subsection\*, \subsubsection\****) que crean encabezados de sección sin numerar y que tampoco aparecerán en la tabla de contenidos.

##### Ejemplo
~~~~ latex
\documentclass[a4paper, 10pt]{article}
...
% CUERPO
\begin{document}
\tableofcontents
\section{Sección primera}
Texto de la sección.
\subsection{Subsección primera}
Texto de la subsección.

% Encabezado de subsección sin numerar
\subsection*{Subsección segunda}
Texto de la subsección.
\subsection{Subsección tercera}
Texto de la subsección.
\section{Sección segunda}
Texto de la sección.
\end{document}
~~~~
![](Fotos/Manual_LaTeX/3_Secciones_y_subsecciones/pdflatex.PNG)

### 3.2. Párrafos y cambios de línea
Para crear un párrafo nuevo basta dejar una o más líneas en blanco.

Si se quiere hacer un cambio de línea dentro de un mismo párrafo, se utiliza el comando ***\newline*** o ***\\\\***.

##### Ejemplo
~~~~ latex
% CUERPO
\begin{document}
Este es el primer párrafo del documento, con un \\
cambio de linea.
Este es el segundo párrafo del documento. Obsérvese que cada vez que se
comienza un párrafo la primera línea de desplaza un poco hacia la derecha.
Esto se conoce como \emph{sangría}.
\end{document}
~~~~
![](Fotos/Manual_LaTeX/3_Secciones_y_subsecciones/pdflatex2.PNG)

### 3.3. Justificación
Los párrafos se justifican por defecto a la izquierda y a la derecha. *LaTeX* utiliza un algoritmo que permite partir las palabras al final de una línea para obtener párrafos con una buena estética (sin grandes espacios en blanco entre palabras). Pero también se pueden justificar solo a la izquierda, solo a la derecha o centrados entre los márgenes. Para ello se utilizan los siguientes entornos:
- **flushleft** - Justifica el texto a la izquierda.
- **flushright** - Justifica el texto a la derecha.
- **center** - Justifica el texto centrado entre los márgenes.

~~~~ latex
% CUERPO
\begin{document}
Este es el primer párrafo del documento, y aparece justificado a ambos lados
(márgenes izquierdo y derecho) por defecto. Para que las líneas tengan la
misma longitud, se utiliza un algoritmo que permite partir las palabras al
final de una línea.
\begin{flushleft}
Este es el segundo párrafo del documento y aparece justificado a la
izquierda, es decir alineado con el margen izquierdo del documento.
Obsérvese que no todas las líneas acaban a la misma altura.
\end{flushleft}
\begin{flushright}
Este es el tercer párrafo del documento y aparece justificado a la derecha,
es decir alineado con el margen derecho del documento. Obsérvese que no
todas las líneas empiezan a la misma altura.
\end{flushright}
\begin{center}
Este es el último párrafo del documento y aparece justificado en el centro
entre los márgenes del documento. Obsérvese que ahora las líneas no
empiezan ni terminan a la misma altura.
\end{center}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/3_Secciones_y_subsecciones/pdflatex3.PNG)

> ⚠️ **ADVERTENCIA:** El algoritmo para partir palabras al final de una línea funciona muy bien, pero si alguna vez divide mal una palabra, se puede indicar por dónde partir la palabra con el comando ***\\-*** (por ejemplo ***si\\-la\\-ba***)

## 4. FORMATEO BÁSICO
---
Existen multitud de comandos para dar formato al texto de un documento, pero en esta sección nos limitaremos a los más importantes.

### 4.1. Negrita, cursiva y subrayado
Para resaltar un texto habitualmente se utiliza negrita, cursiva o subrayado. Estos formatos se aplican con los siguientes comandos:
- ***\textbf{...}*** - Pone el texto en negrita.
- ***\textit{...}*** - Pone el texto en cursiva o itálica.
- ***\emph{...}*** - Enfatiza el texto cambiando de estilo (si estamos en un entorno de cursiva pasa a normal y si estamos en un entorno de texto normal pasa a cursiva).
- ***\underline{...}*** - Subraya el texto.

##### Ejemplo
~~~~ latex
% CUERPO
\begin{document}
Este texto está en \textbf{negrita}, este en \textit{cursiva} y este
\underline{subrayado}.
\textit{Este texto está \emph{enfatizado}}.
\end{document}
~~~~
![](Fotos/Manual_LaTeX/4_Formateo_básico/pdflatex.PNG)

### 4.2. Familias de tipos de letra
Existen tres tipos de letra que se activan con los siguientes comandos:
- ***\texrm{...}*** - Texto normal (con *serif*). Es el tipo por defecto.
- ***\texsf{...}*** - Texto sin adornos (sin *serif*)
- ***\texttt{...}*** - Texto de máquina de escribir o monoespaciado (caracteres con la misma anchura).

##### Ejemplo
~~~~ latex
% CUERPO
\begin{document}
Este texto es normal, \textsf{este es sin adornos}, \texttt{y este de máquina de escribir}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/4_Formateo_básico/pdflatex2.PNG)

En el preámbulo del documento se puede seleccionar la fuente a utilizar para cada uno de ellos, especialmente con el paquete fontspec para compilar con *xelatex*. Para ello se utilizan los siguientes comandos:
- ***\setromanfont{Fuente normal}*** - Establece la fuente para el tipo de letra normal.
- ***\setsansfont{Fuente sin adorno}*** - Establece la fuente para el tipo de letra sin adorno.
- ***\setmonofont{Fuente monoespaciada}*** - Establece la fuente para el tipo de letra monoespaciado.
> 🚨 **PRECAUCIÓN:** Las fuentes utilizadas en un documento deben estar previamente instaladas en el sistema operativo donde se compile el documento.

##### Ejemplo
~~~~ latex
% PREÁMBULO
\usepackage{fontspec}
\setromanfont{Times New Roman}
\setsansfont{Arial}
\setmonofont{Courier New}

% CUERPO
\begin{document}
Este texto es normal, \textsf{este es sin adornos}, \texttt{y este de máquina de escribir}.
\end{document}
~~~~
![](Fotos/Manual_LaTeX/4_Formateo_básico/xelatex.PNG)

### 4.3. Perfiles de letra
Para cada tipo de letra existen también varios perfiles que se activan con los siguientes comandos:
- ***\textup{...}*** - Activa el perfil recto. Es el perfil por defecto.
- ***\textit{...}*** - Activa el perfil de letra itálica.
- ***\textsl{...}*** - Activa el perfil inclinado.
- ***\textsc{...}*** - Activa el perfil de letra versalita (mayúsculas pequeñas).

##### Ejemplo
~~~~ latex
% CUERPO
\begin{document}
Texto normal con perfil recto, \textit{itálica}, \textsl{inclinado} y
\textsc{versalita}.

\textsf{Texto sin adorno con perfil recto, \textit{itálica},
\textsl{inclinado} y \textsc{versalita}.}

\texttt{Texto monoespaciado con perfil recto, \textit{itálica},
\textsl{inclinado} y \textsc{versalita}.}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/4_Formateo_básico/pdflatex3.PNG)

### 4.4. Tamaños de letra
A diferencia de otros procesadores donde el tamaño de la fuente se indica en puntos o pixels, en *LaTeX* existen 10 tamaños predefinidos que se activan con los siguientes comandos, de menor a mayor tamaño:
- ***\tiny***
- ***\scriptsize***
- ***\footnotesize***
- ***\small***
- ***\normalsize***
- ***\large***
- ***\Large***
- ***\LARGE***
- ***\huge***
- ***\Huge***

Existen paquetes que permiten definir tamaños más pequeños o mayores pero no suelen ser necesarios en un documento normal.

##### Ejemplo
~~~~ latex
% CUERPO
\begin{document}
\tiny{tiny}\\
\scriptsize{scripsize}\\
\footnotesize{footnotesize}\\
\small{small}\\
\normalsize{normalsize}\\
\large{large}\\
\Large{Large}\\
\LARGE{LARGE}\\
\huge{huge}\\
\Huge{Huge}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/4_Formateo_básico/pdflatex4.PNG)

## 5. LISTAS
---
Existen tres tipos de listas, no ordenadas, ordenadas y descriptivas (en lugar de marcas o números los items de la lista están encabezados por texto), que se crean con los siguientes entornos:
- **itemize** - Crea un lista sin numerar.
- **enumerate** - Crea una lista enumerada.
- **description** - Crea una lista de tipo descripción.
Dentro de estos entornos, cada elemento de la lista debe empezar en una línea nueva con el comando ***\item***. En el caso de las listas descriptivas, hay que proporcionar el texto del item de la lista como un argumento obligatorio.

##### Ejemplos
Lista no ordenada:
~~~~ latex
% CUERPO
\begin{document}
Ejemplo de lista no ordenada:
\begin{itemize}
\item Este es un item.
\item Este es otro item.
\item Y otro item más.
\end{itemize}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/5_Listas/pdflatex.PNG)

Lista ordenada:
~~~~ latex
% CUERPO
\begin{document}
Ejemplo de lista ordenada:
\begin{enumerate}
\item Primer item.
\item Segundo item.
\item Tercer item.
\end{enumerate}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/5_Listas/pdflatex2.PNG)

Lista descriptiva:
~~~~ latex
% CUERPO
\begin{document}
Ejemplo de lista descriptiva:
\begin{description}
\item{\textbf{latex}} Genera documentos en formato dvi.
\item{\textbf{pdflatex}} Genera documentos en formato pdf.
\item{\textbf{xelatex}} Genera documentos en formato pdf que admiten
codificación Unicode.
\end{description}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/5_Listas/pdflatex3.PNG)

Sublistas:
~~~~ latex
% CUERPO
\begin{document}
Ejemplo de listas anidadas:
\begin{enumerate}
\item Primer item.
    \begin{enumerate}
    \item Primer subitem.
    \item Segundo subitem.
    \end{enumerate}
\item Segundo item.
    \begin{itemize}
    \item Un item.
    \item Otro item.
    \end{itemize}
\end{enumerate}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/5_Listas/pdflatex4.PNG)
> La indentación en el código fuente no es obligatoria pero ayuda a ver mejor la estructura de anidamiento de entornos.

## 6. TABLAS
---
Las tablas son uno de los elementos más complejos de *LaTeX*, ya que, aunque es fácil crear una tabla sencilla, aplicarles un formato más avanzado con justificación de columnas, fusión de columnas o filas, márgenes de columnas, líneas de división, etc. suele ser bastante más difícil, aunque algunos entornos de edición facilitan la tarea. Existen multitud de paquetes para personalizar las tablas pero en esta sección solo veremos lo más básico. 

Para crear una tabla se utiliza el entorno tabular. Este entorno tiene como argumento obligatorio el número de columnas de la tabla y su justificación, que se indica con una letra: 
- ***l*** - izquierda
- ***r*** - derecha
- ***c*** - centrada
> ***lcr*** indica tres columnas, la primera justificada a la izquierda, la segunda centrada y la tercera justificada a la derecha.

A continuación se introduce el contenido de la tabla, separando las filas con el comando de cambio de línea ***\\\\*** y dentro de cada línea separando las celdas con el comando ***&***.

##### Ejemplo
~~~~ latex
% CUERPO
\begin{document}
% Tabla con tres columnas, justificadas a la izquierda, centrada y derecha.
\begin{tabular}{lcr}
Nombre & Ciudad & Edad \\
María & Valencia & 22 \\
Juan & Madrid & 50 \\
Carmen & Barcelona & 35 \\
\end{tabular}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/6_Tablas/pdflatex.PNG)

Para añadir líneas de división entre columnas, se introduce el carácter de barra vertical ***|*** entre las letras que definen la justificación de las columnas en el argumento obligatorio del entorno tabular. Mientras que para añadir líneas de división entre filas, se utiliza el comando ***\hline*** al principio de cada línea. Se insertarán tantas líneas divisorias como veces se introduzca el comando ***\hline***.

##### Ejemplo
~~~~ latex
% CUERPO
\begin{document}
% Tabla con líneas divisorias de filas y columnas.
\begin{tabular}{|l|c|r|}
\hline
Nombre & Ciudad & Edad \\
\hline
\hline
María & Valencia & 22 \\
\hline
Juan & Madrid & 50 \\
\hline
Carmen & Barcelona & 35 \\
\hline
\end{tabular}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/6_Tablas/pdflatex2.PNG)

El comando ***\multicolumn{num}{col}{texto}*** permite crear celdas que se extienden a lo largo de varias columnas, donde **num** es el número de columnas a ocupar, **col** es el carácter que define la justificación de la celda (***l***, ***r*** o ***c***), y **texto** es el contenido de la celda.

También es posible utilizar el comando ***\cline{n-m}*** para dibujar líneas horizontales divisorias que no abarquen toda la fila, sino desde la columna **n** hasta la **m**.

##### Ejemplo
~~~~ latex
% CUERPO
\begin{document}
\begin{tabular}{lrrcrr}
\hline
& \multicolumn{2}{c}{Enero} & & \multicolumn{2}{c}{Febrero}\\
\cline{2-3}\cline{5-6}
Ciudad & Ingresos & Gastos & & Ingresos & Gastos\\
\hline
Madrid & 2500 & 1750 & & 2600 & 1800\\
Barcelona & 2250 & 1500 & & 2400 & 1650\\
\hline
\end{tabular}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/6_Tablas/pdflatex3.PNG)

## 7. IMÁGENES
---
Para incluir una imagen o figura en un documento, además de disponer de la imagen del fichero en un formato gráfico adecuado, es necesario cargar en el preámbulo el paquete graphicx. Este paquete permite gestionar imágenes en los formatos gráficos *jpg*, *png*, *tiff*, *eps* y *pdf* (los tres primeros son formatos de mapas de bits y los dos últimos vectoriales).

Una vez cargado el paquete, para insertar una imagen en el documento basta con utilizar el comando ***\includegraphics[opiones]{fichero}***. Este comando tiene como argumento obligatorio es el nombre del fichero con la imagen (incluyendo la ruta en el sistema de ficheros local) y los siguientes argumentos opcionales para modificar el aspecto de la
imagen:
- **height** - Indica la altura de la imagen. Escala la imagen hasta esa altura.
- **width** - Indica la anchura de la imagen. Escala la imagen hasta esa anchura.
- **scale** - Factor de escalado de la imagen de 0 a 1.
- **angle** - Ángulo de rotación de la imagen. Rota la imagen en el sentido de las agujas del reloj los grados indicados.

##### Ejemplo
~~~~ latex
% PREÁMBULO
\usepackage{graphicx}

% CUERPO
\begin{document}
Ejemplo de imagen en línea
\includegraphics{img/logo-aprendeconalf.png},
escalada
\includegraphics[height=1cm]{img/logo-aprendeconalf.png},
y rotada
\includegraphics[angle=90]{img/logo-aprendeconalf.png}

Ejemplo de imagen centrada:
\begin{center}
\includegraphics{img/logo-aprendeconalf.png}
\end{center}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/7_Imágenes/pdflatex.PNG)

## 8. FÓRMULAS MATEMÁTICAS
---
La escritura de fórmulas matemáticas es uno de los puntos fuertes de *LaTeX*, y es por ello que se utiliza tanto para la creación de documentos científicos o técnicos con contenido matemático.

Para escribir una fórmula es necesario cambiar al modo matemático. Existen distintas formas de activar el modo matemático:
- **$** - Activa el modo matemático en linea, es decir, las fórmulas aparecerán en la misma linea que el texto que las rodea. Para desactivar este modo hay que volver a escribir **$**.
- **$$** - Activa el modo matemático *display* (desplegado), de manera que las fórmulas aparecen en una línea aparte.
- El entorno equation también activa el modo matemático *display* pero además asigna un número a la ecuación, para poder referenciarla en otras partes del documento.

##### Ejemplo
~~~~ latex
% CUERPO
\begin{document}
Ejemplo de fórmula en linea $ x+y=0 $.
Ejemplo de fórmula desplegada

$$
x+y=0
$$
Ejemplo de fórmula con el entorno \texttt{equation}

\begin{equation}
x+y=0
\end{equation}
\end{document}
~~~~
![](Fotos/Manual_LaTeX/8_Fórmulas_matemáticas/pdflatex.PNG)

## 9. ENTORNOS FLOTANTES
---


## 10. REFERENCIAS CRUZADAS Y NOTAS A PIE
---


## 11. CITAS Y REFERENCIAS BIBLIOGRÁFICAS
---


## 12. DISEÑO DE PÁGINA
---

