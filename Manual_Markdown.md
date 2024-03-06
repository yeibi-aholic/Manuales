# **MANUAL MARKDOWN**
## ÍNDICE
1. **[ENCABEZADOS](#encabezados)**
2. **[PÁRRAFOS](#párrafos)**
3. **[LÍNEA HORIZONTAL](#línea-horizontal)**
4. **[ÉNFASIS DE TEXTO](#énfasis-de-texto)**  
   - **[Cursiva](#cursiva)**  
   - **[Negrita](#negrita)**  
   - **[Negrita y Cursiva](#negrita-y-cursiva)** 
   - **[Tachado](#tachado)**
   - **[Subíndice](#subíndice)**
   - **[Superíndice](#superíndice)** 
   - **[Color](#color)**  
   - **[Tipografía](#tipografía)**
5. **[LISTAS](#listas)**  
   - **[Ordenadas](#ordenadas)**  
   - **[No ordenadas](#no-ordenadas)**  
   - **[Sublistas](#sublistas)**   
6. **[TABLAS](#tablas)**
7. **[CITAS](#citas)**
8. **[CÓDIGO](#código)**
9. **[LINKS](#links)**  
    - **[Enlaces web](#enlaces-web)**
    - **[Llamada de encabezados](#llamada-de-encabezados)**
    - **[Referencias](#referencias)**   
    - **[Documentos](#documentos)**  
    - **[Imágenes](#imágenes)**        
10. **[INHABILITACIÓN DE COMANDOS MARKDOWN](#inhabilitación-de-comandos-markdown)**  

## ENCABEZADOS
---
Para crear un encabezado tan solo hace falta poner al principio de un párrafo el símbolo *#* y un espacio. Dependiento del número de símbolos que se empleen corresponderá a un *nivel de título*.

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
~~~~

### Alternativas para # Título 1 y ## Título 2  
Para estos dos casos existe la posibilidad de escribirlos con *=* y *-* estando por debajo del texto.

Título 1
========
~~~~
Título 1  
========
~~~~

Título 2
--------
~~~~
Título 2  
--------
~~~~

## PÁRRAFOS
---
Para separar dos párrafos se deben poner dos espacios al final del primero o dejar una línea en blanco entre los dos.

- **Dos espacios:**

Párrafo 1  
Párrafo 2

- **Línea en blanco:** 

Párrafo 1

Párrafo 2

## LÍNEA HORIZONTAL
---
Para crear una *línea horizontal* solo es necesario poner en una línea aparte 3 asteriscos (***), 3 guiones (---) o 3 barras bajas (___). La línea se verá igual en los tres casos.

~~~~
---  
***  
___
~~~~  

## ÉNFASIS DE TEXTO
---
#### Cursiva
Poner entre asteríscos (\*[  ]*) o barras bajas (\_[  ]_) el texto deseado sin espacios ni al principio ni al final: *Cursiva*.  

#### Negrita
Poner entre dos asteríscos (\*\*[  ]**) o dos barras bajas (\_\_[  ]__) el texto deseado sin espacios ni al principio ni al final: **Negrita**

#### Negrita y Cursiva
Poner entre tres asteríscos (\*\*\*[  ]***) o tres barras bajas (\_\_\_[  ]___) el texto deseado sin espacios ni al principio ni al final: ***Negrita y Cursiva***

#### Tachado
Poner entre dos virgulillas (\~~[  ]~~) el texto deseado sin espacios ni al principio ni al final: ~~Tachado~~

#### Subíndice
Poner entre virgulillas (\~[  ]~) el texto deseado sin espacios ni al principio ni al final: ~subíndice~

#### Superíndice
Poner entre acentos circunflejos (\^[  ]^) el texto deseado sin espacios ni al principio ni al final: ^superíndice^

#### Color
Escribir **\<span style = "color: *'color deseado (en inglés)'*">** y **\</span>** entre el texto al que se quiere aplicar el color: 
<span style = "color: red"> rojo </span> / <span style = "color: blue"> azul </span> / <span style = "color: green"> verde </span> / <span style = "color: orange"> naranja </span> / <span style = "color: purple"> morado </span>

#### Tipografía
Escribir **\<span style = "font-family: *'nombre de la tipografía'*">** y **\</span>** entre el texto al que se le quiere cambiar la tipografía: 
<span style = "font-family: Papyrus"> Papyrus </span> / <span style = "font-family: Georgia"> Georgia </span> / <span style = "font-family: Arial Black"> Arial Black </span> / <span style = "font-family: Calibri"> Calibri </span> / <span style = "font-family: Script"> Script </span>

## LISTAS
---
Hay dos formatos de listas: con guiones (no ordenadas) o numéricas (ordenadas).

- #### Ordenadas
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

- #### No ordenadas
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

- #### Sublistas
Se trataría de tabular al mismo nivel los elementos que se deseen que pertenezcan a un elemento de la lista concreto.

- Primero
- Segundo
  - Tercero
    - Cuarto
- Quinto

1. Primero
2. Segundo
   1. Tercero
      1. Cuarto
3. Quinto

## TABLAS
---
Para crear una tabla hay que añadir tantos | | como columnas se quieran, y en la siguiente fila, tantos |-| como haya en la fila de arriba. En las filas posteriores, siempre que las filas estén seguidas (sin filas vacías), todo lo que se encuentre entre dos | será tomado como columna de la tabla.

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

Si se quiere desplazar el texto hacia la derecha, el centro o la izquierda, tan solo hay que sustituir el |-| de la segunda fila por |:-|, |:-:|, |-:| respectivamente.

~~~~
|Izquierda|Centro|Derecha|  
|:-|:-:|-:|  
|<--|<-->|-->|
~~~~ 

|Izquierda|Centro|Derecha|
|:--------|:----:|------:|
|<--      | <--> |    -->|

## CITAS
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

Las citas se pueden mezclar con otros elementos como el [énfasis de texto](#énfasis-de-texto), [listas](#listas) o [tablas](#tablas).

## CÓDIGO
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

## LINKS
---

#### Enlaces web
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

#### Llamada de encabezados
La llamada de un [encabezado](#encabezados) del propio documento se forma a partir de:
1. El texto que aparecerá en pantalla entre corchetes.
2. Entre paréntesis, nombre del encabezados con guiones en vez espacios y una almohadilla (#) al principio.

~~~~
[Guía Markdown](#guía-markdown)
~~~~

[Guía Markdown](#guía-markdown)

> **NOTA:** las tildes en la llamada del nombre del encabezado no funcionan directamente en *Markdown*, pero sí en la preview de **Azure** o **GitHub**.

#### Referencias

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

#### Documentos
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

#### Imágenes
Para agregar imágenes se trataría de un simbolo de exlamación (!), nombre entre corchetes y la dirección en los documentos (sin espacios) o ***URL***
~~~~
![Foto](https://www.costacruzeiros.com/content/dam/costa/costa-magazine/articles-magazine/travel/croatia-travel/croazia_m.jpg.image.694.390.low.jpg "Croacia")
~~~~
![Foto](https://www.costacruzeiros.com/content/dam/costa/costa-magazine/articles-magazine/travel/croatia-travel/croazia_m.jpg.image.694.390.low.jpg "Croacia")

Para insertar un link a una imágen sería combinar [enlaces web](#enlaces-web) e [imágenes](#imágenes).
~~~~
[![Esquema](https://upload.wikimedia.org/wikipedia/commons/a/a1/Alan_Turing_Aged_16.jpg "Alan Turing")](https://es.wikipedia.org/wiki/Alan_Turing)
~~~~
[![Esquema](https://upload.wikimedia.org/wikipedia/commons/a/a1/Alan_Turing_Aged_16.jpg "Alan Turing")](https://es.wikipedia.org/wiki/Alan_Turing)

## INHABILITACIÓN DE COMANDOS MARKDOWN 
---
Si se quiere escribir un carácter concreto sin que *Markdown* lo interprete solo hay que escribir una barra inversa (\\) a la izquierda del carácter.
~~~~
\*\*Texto**
~~~~
\*\*Texto**
