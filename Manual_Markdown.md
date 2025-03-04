# **MANUAL MARKDOWN**

![MarkDown](Fotos/Manual_Markdown/Markdown_logo.png)

## ÍNDICE
1. **[ENCABEZADOS](#1-encabezados)**
2. **[PÁRRAFOS](#2-párrafos)**
3. **[LÍNEA HORIZONTAL](#3-línea-horizontal)**
4. **[ÉNFASIS DE TEXTO](#4-énfasis-de-texto)**  
   - **[Cursiva](#cursiva)**  
   - **[Negrita](#negrita)**  
   - **[Negrita y Cursiva](#negrita-y-cursiva)** 
   - **[Tachado](#tachado)**
   - **[Subíndice](#subíndice)**
   - **[Superíndice](#superíndice)**
   - **[Subrayado](#subrayado)**
   - **[Color](#color)**  
   - **[Tipografía](#tipografía)**
5. **[LISTAS](#5-listas)**  
   - **[Ordenadas](#ordenadas)**  
   - **[No ordenadas](#no-ordenadas)**  
   - **[Sublistas](#sublistas)**
   - **[Tareas](#tareas)**
6. **[TABLAS](#6-tablas)**
7. **[CITAS](#7-citas)**
8. **[CÓDIGO](#8-código)**
9. **[LINKS](#9-links)**  
    - **[Enlaces web](#enlaces-web)**
    - **[Llamada de encabezados](#llamada-de-encabezados)**
    - **[Llamada de otros archivos](#llamada-de-otros-archivos)**
    - **[Notas a pie de página](#notas-a-pie-de-página)**
    - **[Referencias](#referencias)**   
    - **[Documentos](#documentos)**  
    - **[Imágenes](#imágenes)**
10. **[EMOJIS](#10-emojis)**       
11. **[INHABILITACIÓN DE COMANDOS MARKDOWN](#11-inhabilitación-de-comandos-markdown)**

## 1. ENCABEZADOS
---
Para crear un encabezado tan solo hace falta poner al principio de un párrafo el símbolo *#* y un espacio. Dependiento del número de símbolos que se empleen corresponderá a un *nivel de título*.

~~~~
# Título 1
## Título 2
### Título 3
#### Título 4
##### Título 5
###### Título 6
~~~~

# Título 1
## Título 2
### Título 3
#### Título 4
##### Título 5
###### Título 6

> **Alternativas para # Título 1 y ## Título 2**  
> Para estos dos casos existe la posibilidad de escribirlos con *=* y *-* estando por debajo del texto.
> ~~~~
> Título 1  
> ========
> Título 2  
> --------
> ~~~~
> Título 1
> ========
> Título 2
> --------

## 2. PÁRRAFOS
---
Para separar dos párrafos se deben poner dos espacios al final del primero o dejar una línea en blanco entre los dos.

- **Dos espacios:**

Párrafo 1  
Párrafo 2

- **Línea en blanco:** 

Párrafo 1

Párrafo 2

## 3. LÍNEA HORIZONTAL
---
Para crear una *línea horizontal* solo es necesario poner en una línea aparte 3 asteriscos (***), 3 guiones (---) o 3 barras bajas (___). La línea se verá igual en los tres casos.

~~~~
---  
***  
___
~~~~  

## 4. ÉNFASIS DE TEXTO
---
- ### Cursiva
Poner entre asteríscos (\*[  ]*) o barras bajas (\_[  ]_) el texto deseado sin espacios ni al principio ni al final: *Cursiva*.  

- ### Negrita
Poner entre dos asteríscos (\*\*[  ]**) o dos barras bajas (\_\_[  ]__) el texto deseado sin espacios ni al principio ni al final: **Negrita**

- ### Negrita y Cursiva
Poner entre tres asteríscos (\*\*\*[  ]***) o tres barras bajas (\_\_\_[  ]___) el texto deseado sin espacios ni al principio ni al final: ***Negrita y Cursiva***

- ### Tachado
Poner entre dos virgulillas (\~~[  ]~~) el texto deseado sin espacios ni al principio ni al final: ~~Tachado~~

- ### Subíndice
Poner entre virgulillas (\~[  ]~) el texto deseado sin espacios ni al principio ni al final: ~subíndice~

- ### Superíndice
Poner entre acentos circunflejos (\^[  ]^) el texto deseado sin espacios ni al principio ni al final: ^superíndice^

- ### Subrayado
Escribir **\<ins>** y **\</ins>** entre el texto que se quiere subrayar: <ins>subrayado</ins>

- ### Color
Escribir **\<p style="color:*'color (en inglés)'*">** y **\</p>** entre el texto al que se quiere aplicar el color: 
<p style="color:red">rojo</p>/<p style="color:blue">azul</p>/<p style="color:green">verde</p>/<p style="color:orange">naranja</p>/<p style="color:purple">morado</p>

- ### Tipografía
Escribir **\<p style="font-family:*'tipografía'*">** y **\</p>** entre el texto al que se le quiere cambiar la tipografía: 
<p style = "font-family:Papyrus">Papyrus</p> / <p style="font-family:Georgia">Georgia</p> / <p style="font-family:Arial Black">Arial Black</p> / <p style="font-family:Calibri">Calibri</p> / <p style="font-family:Script">Script</p>

## 5. LISTAS
---
Hay dos formatos de listas: con guiones (no ordenadas) o numéricas (ordenadas).

- ### Ordenadas
Se trata de párrafos seguidos donde al comienzo se encuentra un número y seguido un punto.

~~~~
1. Primero  
2. Segundo  
3. Tercero
~~~~ 

1. Primero  
2. Segundo  
3. Tercero  

> No hace falta que los numeros sigan un orden. La lista seguirá el orden del primer número escrito (no hace falta que sea "1.") y en la siguienta línea, independientemente que número esté escrito en la misma, continuará al número anterior.

- ### No ordenadas
Hay varios guiones validos para que *Markdown* los interprete como lista: -, *, +.

~~~~
- A  
- a  
+ B  
+ b  
* C  
* c
~~~~  

- A  
- a  
+ B  
+ b  
* C  
* c

> Cuando se ponen dos simbolos de listado diferentes en dos líneas seguidas, *Markdown* los separará un poco más que si fuesen ambos del mismo símbolo.

- ### Sublistas
Se trataría de tabular al mismo nivel los elementos que se deseen que pertenezcan a un elemento de la lista concreto.

~~~~
- Primero
- Segundo
  - Tercero
    - Cuarto
- Quinto
~~~~

- Primero
- Segundo
  - Tercero
    - Cuarto
- Quinto

~~~~
1. Primero
2. Segundo
   1. Tercero
      1. Cuarto
3. Quinto
~~~~

1. Primero
2. Segundo
   1. Tercero
      1. Cuarto
3. Quinto

- ### Tareas
Después de definir una lista, se añade **[ ]** para definir una casilla o **[x]** para una casilla marcada.
~~~~
- [x] Tarea 1
- [ ] Tarea 2
- [ ] Tarea 3
~~~~
- [x] Tarea 1
- [ ] Tarea 2
- [ ] Tarea 3

## 6. TABLAS
---
Para crear una tabla hay que añadir tantos **| |** como columnas se quieran, y en la siguiente fila, tantos **|-|** como haya en la fila de arriba. En las filas posteriores, siempre que las filas estén seguidas (sin filas vacías), todo lo que se encuentre entre dos | será tomado como columna de la tabla.
~~~~
|Título 1|Título 2|Título 3|  
|-|-|-|  
|Elemento 1|||  
||Elemento 2||  
|||Elemento 3|
~~~~  
| Título 1 | Título 2 | Título 3 |
|----------|----------|----------|
|Elemento 1|          |          |
|          |Elemento 2|          |
|          |          |Elemento 3|

Si se quiere desplazar el texto hacia la derecha, el centro o la izquierda, tan solo hay que sustituir el **|-|** de la segunda fila por **|:-|**, **|:-:|** o **|-:|** respectivamente.
~~~~
|Izquierda|Centro|Derecha|  
|:-|:-:|-:|  
|<--|<-->|-->|
~~~~ 
|Izquierda|Centro|Derecha|
|:--------|:----:|------:|
|<--      | <--> |    -->|

Si se quiere hacer un salto de línea dentro de la tabla, tan solo hay que escribir **\<br>** al final de la misma.
~~~~
| Fila   | Contenido |
| ------ | ----------- |
| Fila 1 | Línea 1.<br> Línea 2.|
~~~~
| Fila   | Contenido |
| ------ | ----------- |
| Fila 1 | Línea 1.<br> Línea 2.|

También se pueden insertar varios párrafos escribiendo **\<p>** y **\</p>** entre cada texto que queremos separar.
~~~~
| Fila   | Contenido |
| ------ | ----------- |
| Fila 1 | <p>Párrafo 1.</p> <p>Párrafo 2.</p> <p>Párrafo 3.</p> |
~~~~
| Fila   | Contenido |
| ------ | ----------- |
| Fila 1 | <p>Párrafo 1.</p> <p>Párrafo 2.</p> <p>Párrafo 3.</p> |

Dentro de las tablas no se pueden insertar [encabezados](#1-encabezados) de la misma forma que un texto normal. Hay que escribir **\<hN>** y **\</hN>** entre el texto que se quiere alterar, siendo *N* un número comprendido entre 1 y 6.
~~~~
| Fila | <h1>Contenido</h1> |
| ---- | ------------------ |
| <h3>Texto 1</h3> | Texto 2 |
~~~~
| Fila | <h1>Contenido</h1> |
| ---- | ------------------ |
| <h3>Texto 1</h3> | Texto 2 |

Para insertar [listas](#5-listas) dentro de una columna hay escribir **\<li>** y **\</li>** entre cada elemento de la lista y **\<ul>** y **\</ul>** entre los elemento de la lista.
~~~~
| Fila   | Contenido |
| ------ | ----------- |
| Fila 1 | Lista <ul><li>Elemento 1</li><li>Elemento 2</li></ul> |
~~~~
| Fila   | Contenido |
| ------ | ----------- |
| Fila 1 | Lista <ul><li>Elemento 1</li><li>Elemento 2</li></ul> |

## 7. CITAS
---
Para añadir un texto en formato *cita*, se añade un *>* al principo del párrafo.
~~~~
> Cita
~~~~
> Cita

Dentro de una misma *cita* se pueden crear múltiples párrafos añandiendo un > entre dos párrafos citados.
~~~~
> Párrafo 1  
>  
> Párrafo 2 
~~~~ 

> Párrafo 1  
>
> Párrafo 2  

Las *citas* se pueden anidar añadiendo varios > seguidos en el siguiente párrafo. Si se pasa de escribir de un párrafo a uno de "mayor nivel", se debe dejar una línea en blanco con tantos > tenga el párrafo de mayor nivel.
~~~~
> Párrafo 1  
>> Subpárrafo 1.1  
>> Subpárrafo 1.2   
>  
> Párrafo 2  
>> Subpárrafo 2.1  
>>> Subsubpárrafo 2.1.1  
>  
> Párrafo 3 
~~~~ 
> Párrafo 1  
>> Subpárrafo 1.1  
>> Subpárrafo 1.2  
>
> Párrafo 2  
>> Subpárrafo 2.1  
>>> Subsubpárrafo 2.1.1 
> 
> Párrafo 3  

Las citas se pueden mezclar con otros elementos como el [énfasis de texto](#4-énfasis-de-texto), [listas](#5-listas) o [tablas](#6-tablas).

## 8. CÓDIGO
---
Escribir el código deseado entre dos líneas que contengan "~~~~". Para remarcar con colores el código, se puede escribir el nombre del programa al que se hace referencia *(pascal, c, python, sql, ...)* seguido de la primera línea de virgulillas.

PASCAL:
~~~~ pascal
PROGRAM HOLAMUNDO;

USES Crt;

begin
    Write('Hola Mundo');
    ReadKey;
end.
~~~~

C:
~~~~ c
/*Programa: Hola Mundo*/

#include <conio.h>
#include <stdio.h>

int.main(){
    printf("Hola Mundo");
    return 0;
}
~~~~

Python:
~~~~ python
print("Hola Mundo")
~~~~

SQL:
~~~~ sql
SELECT Nombre, Apellido, Edad, DNI
  FROM TABLA.DATOS
 WHERE Edad BETWEEN 18 AND 35
   AND DNI LIKE '%X'
 ORDER BY DNI;
~~~~

> Todo lo que se escriba dentro de las virguilillas, *Markdown* lo escribirá directamente sin interpretación de símbolos.

## 9. LINKS
---

- ### Enlaces web
Las ***URLs*** se pueden escribir directamente (o entre los símbolos <>) y *Markdown* los interpreta directamente como énlaces.
~~~~
https://duckduckgo.com/
~~~~
https://duckduckgo.com/

Para convertir un texto en link solo hay que encerrarlo entre corchetes y seguido la ***URL*** entre paréntesis.
~~~~
[Duck Duck Go](https://duckduckgo.com/)
~~~~
[Duck Duck Go](https://duckduckgo.com/)

Si se quiere que aparezca un pequeño título al dejar el ratón sobre el énlace, después del enlace, escribir entre comillas el texto deseeado.
~~~~
[Duck Duck Go](https://duckduckgo.com/ "El mejor buscador para programación")
~~~~
[Duck Duck Go](https://duckduckgo.com/ "El mejor buscador para programación")

> Para editar el *target* (el lugar en donde se abrirán dichos enlaces) de un enlace hay que escribir el enlace conel estilo **\<a href="URL" target="tipo de target">Texto de enlace</a>**
> - **_blank** - Abre el enlace en una nueva pestaña o ventana.
> - **_self** - Abre el enlace en la pestaña, marco o ventana actual.
> - **_parent** - Abre el enlace en el frame de nivel superior al actual.
> - **_top** - Abre el enlace en el frame de mayor nivel con respecto al actual.

- ### Llamada de encabezados
La llamada de un [encabezado](#encabezados) del propio documento se forma a partir de:
1. El texto que aparecerá en pantalla entre corchetes.
2. Entre paréntesis, nombre del encabezados con guiones en vez espacios y una almohadilla (#) al principio.
~~~~
[Manual Markdown](#manual-markdown)
~~~~
[Manual Markdown](#manual-markdown)
> ⚠️ **ADVERTENCIA:** las tildes en la llamada del nombre del encabezado no funcionan directamente en *Markdown*, pero sí en la preview de **Azure** o **GitHub**.

- ### Llamada de otros archivos
La llamada de un archivo/documento de una misma ruta se forma a partir de:
1. El texto que aparecerá en pantalla entre corchetes.
2. Entre paréntesis, nombre del archivo en la ruta y "./" al principio.
~~~~
[Manual Python](./Manual_Python.md)
~~~~
[Manual Python](./Manual_Python.md)
> Si se quiere especificar una encabezado de otro archivo se añade la estructura de encabezados al final de la ruta.
> ~~~~
> [Manual Python -> RegEx](./Manual_Python.md#expresiones-regulares)
> ~~~~
> [Manual Python -> RegEx](./Manual_Python.md#expresiones-regulares)

- ### Referencias
Se trata de links especiales declarados dentro del propio documento de *Markdown*. Están formados a partir de dos partes:  
1. El texto entre corchetes que funcionará a modo de énlace y a su derecha, también entre corchetes, el nombre del énlace referenciado definido aparte.
2. El énlace definido con su nombre entre corchetes, dos puntos, espacio, ***URL*** ó nombre de un encabezado, un título entre (), "" ó '' (opcional)

~~~~
[URL][link 1]
[Encabezado][link 2]

[link 1]: https://www.google.es/ (buscador)
[link 2]: #índice "vuelta al principio"
~~~~
[URL][link 1]  
[Encabezado][link 2]

[link 1]: https://www.google.es/ (buscador)
[link 2]: #índice "vuelta al principio"

- ### Notas a pie de página
Se pueden crear notas puntuales en formato de superíndice que acumularán al final de página. 
~~~~
Primera nota [^1] a pie de página.
[^1]: Definición 1

También se pueden definir palabras [^palabra] y volver a usar una nota [^1].
[^palabra]: Definición de la palabra
~~~~

Primera nota [^1] a pie de página.
[^1]: Definición 1

También se pueden definir palabras [^palabra] y volver a usar una nota [^1].
[^palabra]: Definición de la palabra

- ### Documentos
El formato es parecido al de [enlaces web](#enlaces-web) pero esta vez poniendo la dirección del documento dentro de nuestros archivos o simplemente escribiendo el nombre del documento si se encuentra en la misma ruta que el archivo actual.
~~~~
[Manual de Python](Manual_Python.md)
~~~~
[Manual de Python](Manual_Python.md)

Si queremos ir a un apartado concreto del documento tan solo hay que aplicar la [llamada de encabezados](#llamada-de-encabezados) al final.
~~~~
[Manual de Python - Tipos de datos Primitivos Simples](Manual_Python.md#tipos-de-datos-primitivos-simples)
~~~~
[Manual de Python - Tipos de datos Primitivos Simples](Manual_Python.md#tipos-de-datos-primitivos-simples)
> Si el archivo al que queremos acceder se encuentra una o varias carpetas más atrás, tan solo hay que poner *"../"* al comienzo de la ruta por cada carpeta que queramos retroceder.

- ### Imágenes
Para agregar imágenes se trataría de un simbolo de exlamación (**!**), nombre entre corchetes y la dirección en los documentos (sin espacios) o ***URL*** (de forma opcional está el nombre que se quiere que se muestre al posicionar el ratón encima de la imagen).
~~~~
![Paisaje](https://th.bing.com/th/id/OIP.zX5zs6UG8Jx06QEh_y-3DAHaEK?rs=1&pid=ImgDetMain "Croacia")
![QR](Fotos/Manual_Markdown/qr.png "Scan me")
~~~~
![Paisaje](https://th.bing.com/th/id/OIP.zX5zs6UG8Jx06QEh_y-3DAHaEK?rs=1&pid=ImgDetMain "Croacia")
![QR](Fotos/Manual_Markdown/qr.png "Scan me")

Para insertar un link a una imágen sería combinar [enlaces web](#enlaces-web) e [imágenes](#imágenes).
~~~~
[![Alan Turing](https://cdn.futura-sciences.com/buildsv6/images/profilehero/3/7/4/374cd9a3be_50142133_turing-1000.jpg "Alan Turing")](https://es.wikipedia.org/wiki/Alan_Turing)
~~~~
[![Alan Turing](https://cdn.futura-sciences.com/buildsv6/images/profilehero/3/7/4/374cd9a3be_50142133_turing-1000.jpg "Alan Turing")](https://es.wikipedia.org/wiki/Alan_Turing)

Para redimensionar una imagen habra que insertar la imagen con el estilo **\<img src="*URL*" width="999" height="999">**
~~~~
<img src="https://hocbato.com/wp-content/uploads/hinh-nen-may-tinh-4k-dep-45-780x439.jpg" width="450" height="300">
~~~~
<img src="https://hocbato.com/wp-content/uploads/hinh-nen-may-tinh-4k-dep-45-780x439.jpg" width="450" height="300">

## 10. EMOJIS
Se pueden añadir *emojis* mediante el símbolo dos puntos (**:**) y el nombre del *emoji* a insertar ()
~~~~
:warning **WARNING:** esto es un aviso.  
:bulb **CONSEJO:** esto es un consejo.  
:memo **NOTA:** esto es una nota.  
~~~~
⚠️ **WARNING:** esto es un aviso.  
💡 **CONSEJO:** esto es un consejo.  
📝 **NOTA:** esto es una nota.  

## 11. INHABILITACIÓN DE COMANDOS MARKDOWN 
---
Si se quiere escribir un carácter concreto sin que *Markdown* lo interprete solo hay que escribir una barra inversa (\\) a la izquierda del carácter.
~~~~
\*\*Texto**
~~~~
\*\*Texto**
