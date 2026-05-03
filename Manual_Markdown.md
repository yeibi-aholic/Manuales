# **MANUAL MARKDOWN**

![MarkDown](Fotos/Manual_Markdown/Markdown_logo.png)

## ÍNDICE
1. **[ENCABEZADOS](#1-encabezados)**
2. **[PÁRRAFOS](#2-párrafos)**
3. **[LÍNEA HORIZONTAL](#3-línea-horizontal)**
4. **[ÉNFASIS DE TEXTO](#4-énfasis-de-texto)**  
5. **[LISTAS](#5-listas)**  
6. **[TABLAS](#6-tablas)**
7. **[CITAS](#7-citas)**
8. **[CÓDIGO](#8-código)**
9. **[LINKS](#9-links)**
10. **[MATEMÁTICAS](#10-matemáticas)**
11. **[EMOJIS](#11-emojis)**       
12. **[INHABILITACIÓN DE COMANDOS MARKDOWN](#12-inhabilitación-de-comandos-markdown)**

## 1. ENCABEZADOS
---
Para crear un encabezado tan solo hace falta poner al principio de un párrafo el símbolo *#* y un espacio. Dependiento del número de símbolos que se empleen corresponderá a un *nivel de título*.

~~~~
# Título 1
~~~~
# Título 1

~~~~
## Título 2
~~~~
## Título 2

~~~~
### Título 3
~~~~
### Título 3

~~~~
#### Título 4
~~~~
#### Título 4

~~~~
##### Título 5
~~~~
##### Título 5

~~~~
###### Título 6
~~~~
###### Título 6

> :memo: **Alternativas para # Título 1 # y ## Título 2 ##**  
> ~~~~
> Alternativa 1
> =============
> ~~~~
> Alternativa 1
> =============
>
> ~~~~
> Alternativa 2
> -------------
> ~~~~
> Alternativa 2
> -------------

> :bulb: **Versión HTML**  
> Para crear un encabezado con HTML hay que escribir el texto entre las etiquetas **\<hN>** y **\</hN>**, siendo *N* un número comprendido entre 1 y 6.
> ~~~~
> <h1> HTML </h1>
> ~~~~
> <h1> HTML </h1>


## 2. PÁRRAFOS
---
Para separar dos párrafos se deben poner dos espacios al final del primero o dejar una línea en blanco entre los dos.

- **Sin espacios ni líneas en blanco / Soft break**
~~~~
Párrafo 1
Párrafo 2
~~~~
Párrafo 1
Párrafo 2

- **Dos espacios / Hard break ↵**
~~~~
Párrafo 1  Párrafo 2
~~~~
Párrafo 1  
Párrafo 2

> :memo: **Versión HTML**  
> Para crear un salto de línea con HTML hay que escribir **\<br>** al final del párrafo.
> ~~~~
> Párrafo 1 <br>
> Párrafo 2
> ~~~~
> Párrafo 1 <br>
> Párrafo 2

- **Salto de línea →** 
~~~~
Párrafo 1

Párrafo 2
~~~~
Párrafo 1

Párrafo 2

> :memo: **Versión HTML**  
> Para crear un párrafo con HTML hay que escribir el texto entre las etiquetas **\<p>** y **\</p>**.
> ~~~~
> <p> Párrafo 1 </p>
> <p> Párrafo 2 </p>
> ~~~~
> <p> Párrafo 1 </p>
> <p> Párrafo 2 </p>


## 3. LÍNEA HORIZONTAL
---
Para crear una *línea horizontal* solo es necesario poner en una línea aparte 3 asteriscos (***), 3 guiones (---), 3 barras bajas (___) o los mismos casos seprados por espacios. La línea se verá igual en todos los casos.

~~~~
---  
- - -  
***  
* * *  
___
_ _ _
~~~~ 


## 4. ÉNFASIS DE TEXTO
---

|Texto|Descripción|
|:-:|:-|
|*Cursiva*|Poner entre asteríscos (\*[ ]\*) el texto deseado sin espacios ni al principio ni al final.<br>Poner entre barras bajas (\_[ ]\_) el texto deseado sin espacios ni al principio ni al final.<br>Escribir **\<em>** y **\</em>** entre el texto deseado.<br>Escribir **\<i>** y **\</i>** entre el texto deseado.|
|**Negrita**|Poner entre dos asteríscos (\*\*[ ]\*\*) el texto deseado sin espacios ni al principio ni al final.<br>Poner entre dos barras bajas (\_\_[ ]\_\_) el texto deseado sin espacios ni al principio ni al final.<br>Escribir **\<strong>** y **\</strong>** entre el texto deseado.<br>Escribir **\<b>** y **\</b>** entre el texto deseado.|
|***Negrita y Cursiva***|Poner entre tres asteríscos (\*\*\*[ ]\*\*\*) el texto deseado sin espacios ni al principio ni al final.<br>Poner entre tres barras bajas (\_\_\_[ ]\_\_\_) el texto deseado sin espacios ni al principio ni al final.|
|~~Tachado~~|Poner entre dos virgulillas (\~\~[ ]~~) el texto deseado sin espacios ni al principio ni al final.<br>Escribir **\<del>** y **\</del>** entre el texto deseado.<br>Escribir **\<s>** y **\</s>** entre el texto deseado.|
|~Subíndice~|Poner entre virgulillas (\~[ ]~) el texto deseado sin espacios ni al principio ni al final.<br>Escribir **\<sub>** y **\</sub>** entre el texto deseado.|
|^Superíndice^|Poner entre acentos circunflejos (\^[ ]^) el texto deseado sin espacios ni al principio ni al final.<br>Escribir **\<sup>** y **\</sup>** entre el texto deseado.|
|<ins>Subrayado</ins>|Escribir **\<ins>** y **\</ins>** entre el texto deseado.<br>Escribir **\<u>** y **\</u>** entre el texto deseado.|
|==Resaltado==|Poner entre dos signos de igual (\==[ ]==) el texto deseado sin espacios ni al principio ni al final.|
|Color|Escribir **\<span style="color:*'color (en inglés)'*">** y **\</span>** entre el texto al que se quiere aplicar el color. <span style="color:red">rojo</span>, <span style="color:blue">azul</span>, <span style="color:green">verde</span>, <span style="color:orange">naranja</span>, <span style="color:purple">morado</span>|
|Tipografía|Escribir **\<span style="font-family:*'tipografía'*">** y **\</span>** entre el texto al que se le quiere cambiar la tipografía: <span style = "font-family:Papyrus">Papyrus</span>, <span style="font-family:Georgia">Georgia</span>, <span style="font-family:Arial Black">Arial Black</span>, <span style="font-family:Calibri">Calibri</span>, <span style="font-family:Script">Script</span>|


## 5. LISTAS
---
Hay dos formatos de listas: con guiones (no ordenadas) o numéricas (ordenadas).

### Ordenadas
Se trata de párrafos seguidos donde al comienzo se encuentra un número y seguido un punto.

~~~~
1. Primero
2. Segundo
3. Tercero
~~~~ 

1. Primero
2. Segundo
3. Tercero

> :warning: No hace falta que los números sigan un orden. La lista seguirá el orden del primer número escrito (no hace falta que sea "1.") y en la siguienta línea, independientemente que número esté escrito en la misma, continuará al número anterior.
> ~~~~
> 1. Primero
> 1. Segundo
> 4. Tercero
> ~~~~
> 1. Primero
> 1. Segundo
> 4. Tercero

### No ordenadas
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

> :warning: Cuando se ponen dos simbolos de listado diferentes en dos líneas seguidas, *Markdown* los separará un poco más que si fuesen ambos del mismo símbolo.

### Sublistas
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

### Tareas
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

> :memo: **Alternativa HTML**  
> Para crear una tabla con HTML hay que escribir la tabla entre las etiquetas **\<table>** y **\</table>**. Cada fila de la tabla se escribe entre las etiquetas **\<tr>** y **\</tr>**, cada título de columna entre las etiquetas **\<th>** y **\</th>** y cada elemento de la tabla entre las etiquetas **\<td>** y **\</td>**.
> ~~~~
> <table border="1">
>   <tr>
>     <th>Título 1</th>
>     <th>Título 2</th>
>     <th>Título 3</th>
>   </tr>
>   <tr>
>     <td>Elemento 1</td>
>     <td></td>
>     <td></td>
>   <tr>
>     <td></td>
>     <td>Elemento 2</td>
>     <td></td>
>   </tr>
>   <tr>
>     <td></td>
>     <td></td>
>     <td>Elemento 3</td>
>   </tr>
> </table>
> ~~~~
> <table border="1">
>   <tr>
>     <th>Título 1</th>
>     <th>Título 2</th>
>     <th>Título 3</th>
>   </tr>
>   <tr>
>     <td>Elemento 1</td>
>     <td></td>
>     <td></td>
>   <tr>
>     <td></td>
>     <td>Elemento 2</td>
>     <td></td>
>   </tr>
>   <tr>
>     <td></td>
>     <td></td>
>     <td>Elemento 3</td>
>   </tr>
> </table>

Si se quiere desplazar el texto hacia la derecha, el centro o la izquierda, tan solo hay que sustituir el **|-|** de la segunda fila por **|:-|**, **|:-:|** o **|-:|** respectivamente.
~~~~
|Izquierda|Centro|Derecha|  
|:-|:-:|-:|  
|<--|<-->|-->|
~~~~ 
|Izquierda|Centro|Derecha|
|:--------|:----:|------:|
|<--      | <--> |    -->|

> :memo: **Alternativa HTML**  
> Para alinear el texto con HTML hay que escribir el texto entre las etiquetas **\<td align="tipo de alineación">** y **\</td>**, siendo el tipo de alineación *left*, *center* o *right*.
> ~~~~
> <table border="1">
>   <tr>
>     <th align="left">Izquierda</th>
>     <th align="center">Centro</th>
>     <th align="right">Derecha</th>
>   </tr>
>   <tr>
>     <td align="left"><--</td>
>     <td align="center"><--></td>
>     <td align="right">--></td>
>   </tr>
> </table>
> ~~~~
> <table border="1">
>   <tr>
>     <th align="left">Izquierda</th>
>     <th align="center">Centro</th>
>     <th align="right">Derecha</th>
>   </tr>
>   <tr>
>     <td align="left"><--</td>
>     <td align="center"><--></td>
>     <td align="right">--></td>
>   </tr>
> </table>

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

> :memo: **Alternativa HTML**
> Para crear una cita con HTML hay que escribir el texto entre las etiquetas **\<blockquote>** y **\</blockquote>**.
> ~~~~
> <blockquote>
>   Cita
>   <blockquote>
>     Subcita
>     <blockquote>
>       Subsubcita
>       <blockquote>
>         Subsubsubcita
>       </blockquote>
>     </blockquote>
>   </blockquote>
> </blockquote>
> ~~~~
> <blockquote>
>   Cita
>   <blockquote>
>     Subcita
>     <blockquote>
>       Subsubcita
>       <blockquote>
>         Subsubsubcita
>       </blockquote>
>     </blockquote>
>   </blockquote>
> </blockquote>

### Notas internas
Si se quisiera añadir una nota que solo se verá dentro del código fuente de *Markdown* y no en la preview, se puede escribir incluir la nota dentro de un comentario HTML \<!--[ ]-->.
~~~~
> Cita con nota interna <!--Nota interna-->
~~~~
> Cita con nota interna <!--Nota interna-->


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


## 9.MATEMÁTICAS
Para escribir fórmulas matemáticas se pueden usar los símbolos de dólar (\$) al principio y al final de la fórmula. Para escribir fórmulas matemáticas en varias líneas, se pueden usar dos símbolos de dólar (\$\$) al principio y al final de la fórmula.
~~~~
$E=mc^2$

$$\int_a^b f(x)dx$$

$$\sum_{n=1}^{100} \frac{n(n+1)}{2}$$
~~~~
$E=mc^2$

$$\int_a^b f(x)dx$$

$$\sum_{n=1}^{100} \frac{n(n+1)}{2}$$
> :memo: **Alternativa HTML**  
> Para escribir fórmulas matemáticas con HTML hay que escribir la fórmula entre las etiquetas **\<math>** y **\</math>**. Para escribir fórmulas matemáticas en varias líneas, se pueden usar las etiquetas **\<div style="display: block; text-align: center;">** y **\</div>** al principio y al final de la fórmula respectivamente.
> ~~~~
> <math>
>   <mi>E=m</mi>
>   <msup>
>     <mi>c</mi>
>     <mn>2</mn>
>   </msup>
> </math>
> <br>
> <math>
>   <msubsup>
>     <mo>∫</mo>
>     <mi>a</mi>
>     <mi>b</mi>
>   </msubsup>
>   <mi>f(x) dx</mi>
> </math>
> <br>
> <math>
>   <msubsup>
>     <mo>∑</mo>
>     <mi>n=1</mi>
>     <mi>100</mi>
>   </msubsup>
>   <mfrac>
>     <mrow>
>       <mi>n(n+1)</mi>
>     </mrow>
>     <mn>2</mn>
>   </mfrac>
> </math>
> ~~~~
> <math>
>   <mi>E=m</mi>
>   <msup>
>     <mi>c</mi>
>     <mn>2</mn>
>   </msup>
> </math>
> <br>
> <math>
>   <msubsup>
>     <mo>∫</mo>
>     <mi>a</mi>
>     <mi>b</mi>
>   </msubsup>
>   <mi>f(x) dx</mi>
> </math>
> <br>
> <math>
>   <msubsup>
>     <mo>∑</mo>
>     <mi>n=1</mi>
>     <mi>100</mi>
>   </msubsup>
>   <mfrac>
>     <mrow>
>       <mi>n(n+1)</mi>
>     </mrow>
>     <mn>2</mn>
>   </mfrac>
> </math>


## 10. LINKS
---
### Enlaces web
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

### Llamada de encabezados
La llamada de un [encabezado](#encabezados) del propio documento se forma a partir de:
1. El texto que aparecerá en pantalla entre corchetes.
2. Entre paréntesis, nombre del encabezados con guiones en vez espacios y una almohadilla (#) al principio.
~~~~
[Manual Markdown](#manual-markdown)
~~~~
[Manual Markdown](#manual-markdown)
> :warning: **ADVERTENCIA:** las tildes en la llamada del nombre del encabezado no funcionan directamente en *Markdown*, pero sí en la preview de **Azure** o **GitHub**.

### Llamada de otros archivos
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

### Referencias
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

### Notas a pie de página
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

### Documentos
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

### Imágenes
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


## 11. EMOJIS
Se pueden añadir *emojis* mediante el símbolo dos puntos (**:**) y el nombre del *emoji* a insertar ()
~~~~
:warning: **WARNING:** esto es un aviso.  
:bulb: **CONSEJO:** esto es un consejo.  
:memo: **NOTA:** esto es una nota.  
~~~~
:warning: **WARNING:** esto es un aviso.  
:bulb: **CONSEJO:** esto es un consejo.  
:memo: **NOTA:** esto es una nota.  


## 12. INHABILITACIÓN DE COMANDOS MARKDOWN 
---
Si se quiere escribir un carácter concreto sin que *Markdown* lo interprete solo hay que escribir una barra inversa (\\) a la izquierda del carácter.
~~~~
\*\*Texto**
~~~~
\*\*Texto**
