# **MANUAL COBOL**

1. **[Introducción](#introducción)**
2. **[IDENTIFICATION DIVISION](#identification-division)**
3. **[ENVIRONMENT DIVISION](#environment-division)**
4. **[DATA DIVISION](#data-division)**
5. **[PROCEDURE DIVISION](#procedure-division)**
6. **[Instrucciones de Cálculo](#instrucciones-de-cálculo)**
7. **[Instrucciones de Archivos](#instrucciones-de-archivos)**
8. **[Instrucciones de Pantalla](#instrucciones-de-pantalla)**
9. **[Instrucciones de Variables](#instrucciones-de-variables)**
10. **[Instrucción PERFORM](#instrucción-perform)**

## **[<](#manual-cobol)**
## Introducción
---
COBOL es un acrónimo que significa ***CO****mmon* ***B****usiness* ***O****riented* ***L****anguage* (Lenguaje orientado a los negocios comunes). Está diseñado para el desarrollo de negocios, por lo general orientada a archivos y aplicaciones. No está diseñado para escribir programas de sistemas, como por ejemplo un sistema operativo o un compilador.  
Durante décadas, COBOL ha sido el lenguaje de programación dominante en la informática empresarial, gracias a la capacidad de manejar ficheros grandes.

COBOL además es un lenguaje estructurado y sus partes se diferencian claramente en "divisiones".
Éstas son 4, son obligatorias y cada una de ellas tiene una misión diferente dentro de cada programa como veremos a continuación.

El programa cobol se escribe secuencialmente en líneas de 80 caracteres o menos con la siguiente división:
~~~~
         1         2         3         4         5         6         7         8
12345678901234567890123456789012345678901234567890123456789012345678901234567890
------_----______________________________________________________________-------
 (1) (2)(3)                            (4)                                 (5)
~~~~
|División|Rango de columnas|Descripción|
|:-:|:-:|:-|
|(1)|1-6|Se utiliza para numerar las líneas.|
|(2)|7|Se pueden incluir caractesres especiales para diversas funciones: <*> (línea de comentario), <-> (continuación de un texto de la línea previa), etc.|
|(3)|8-11|Se le llama ***Área A***. Es donde se escriben los nombre de las divisiones, de las secciones, de los párrafos, los indicadores de FD (File Description) y los niveles de variables *01* y *77*.|
|(4)|12-73|Se le llama ***Área B***. Es donde se incluirán todas las instrucciones del programa, las lineas de las secciones y los niveles de variables mayores a *01*.|
|(5)|74-80|A nivel de código no se emplean. Sirve únicamente para extender las líneas de comentario.|

El punto <.> es un signo de vital importancia en COBOL ya que nos indica el final de una línea, con él han de terminar todas las secciones, divisiones y párrafos. Si al final de una linea el compilador no encuentra el punto, interpretará que la instrucción continúa hasta que aparezca el punto de fin de linea.

Al igual que en otros lenguajes, el cobol dispone de *palabras reservadas* que no debemos de utilizar como nombres de variables o de párrafos, además éstos no deben de exceder de 30 caracteres (depende del compilador).

Las variables y constantes que se pueden utilizar son numéricas, alfabéticas o alfanuméricas. Las numéricas al contrario de la mayoría de los lenguajes actuales o las bases de datos no miden su tamaño por bytes sino por dígitos, es decir, que una variable de 6 dígitos podrá contener números desde 0 hasta 999999 si es de valor absoluto o incluyendo los negativos si lleva signo. Para las alfanuméricas en cambio no hay cambio alguna y su tamaño viene indicado por el número de caracteres que ocupa.
Existen además en cobol unas variables que vienen con un valor propio y que se pueden utilizar libremente, también llamadas **Constantes Figurativas**, como *ZERO*, *SPACE*, *LOW-VALUES*, *HIGH-VALUES*, etc...

## **[<](#manual-cobol)**
## IDENTIFICATION DIVISION
---
~~~~ cobol
        IDENTIFICATION DIVISION.
        PROGRAM-ID. <Nombre del programa>.
        AUTHOR. <Nombre del autor>.
        INSTALLATION. <Lugar donde está instalado>.
        DATE-WRITTEN. <Fecha de creación>.
        DATE-COMPILED. <Fecha de compilación>.
        REMARKS. <Comentarios>.
~~~~
> El único campo obligatorio es **PROGRAM-ID**

## **[<](#manual-cobol)**
## ENVIRONMENT DIVISION
---
~~~~ cobol
        ENVIRONMENT DIVISION.
        CONFIGURATION SECTION.
        SOURCE-COMPUTER. <Ordenador donde se escribió el fuente>.
        OBJECT-COMPUTER. <Ordenador donde se ejecuta el objeto>.
        SPECIAL-NAMES. <Cambiar valores para constantes del lenguaje (pueden variar en cada compilador)>.
~~~~

#### CONFIGURATION SECTION
Donde describimos los tipos de ordenadores en que se escribió y se ejecutará el programa, o bien el nombre del compilador y asignación de valores a ciertas constantes utilizadas por el compilador.

Para la linea de SPECIAL-NAMES el uso más habitual es el de cambiar el punto decimal usado por los ingleses por la coma y así poder especificar los puntos para los miles, o cambiar el valor del símbolo de la moneda, o hacer que todas las letras introducidas sean mayúsculas o minúsculas o que no haya diferencias entre ambas:
~~~~ cobol
        SPECIAL-NAMES.
            DECIMAL-POINT IS COMMA.
            CURRENCY SIGN IS <literal (no puede coincidir con ninguno de los que usamos para definir las variables)>.
            ALPHABET.
~~~~

#### INPUT-OUTPUT SECTION
se especificarán todos los ficheros que vamos a utilizar, su tipo, su modo de acceso asi como el medio en que estarán, esta sección solo será obligatoria cuando vayamos a utilizar ficheros.
~~~~ cobol
        INPUT-OUTPUT SECTION.
        FILE-CONTROL.
        SELECT [OPTIONAL] Nombre-de-archivo
        ASSIGN                          TO <Tipo de dispositivo>
        ORGANIZATION                    IS <Tipo de organización>
        ACCESS MODE                     IS <Modo de acceso al fichero>
        RECORD KEY                      IS <Clave del registro>
        ALTERNATE RECORD KEY            IS <Claves alternativas registro> [WITH DUPLICATES]
        FILE STATUS                     IS <Variable de estado del fichero>.
~~~~

##### SELECT
Especificamos el nombre lógico que va a tener el fichero dentro del programa, suele ser una palabra que identifique lo mas claro posible el contenido del fichero, por ejemplo ARTICULOS, PROVEEDORES, CLIENTES.
##### OPTIONAL
Si indicamos esta opción al hacer un OPEN I-O, si el archivo no existe, se crea. Con lo cual nos evitamos tener que abrirlo como OUTPUT y cerrarlo, antes de poder utilizarlo por primera vez.
##### ASSIGN
Especificamos el tipo de dispositivo, si es una impresora PRINTER, si es un fichero sobre el que vamos a grabar RANDOM o DISC, se pueden utilizar otros como INPUT, INPUT-OUTPUT, CASSETTE, MAGNETIC-TAPE, pero sin duda los mas utilizados son los dos primeros para identificar si el fichero utilizará una salida impresa o se utilizará sobre disco. Para identificar ficheros utilizados para clasificar utilizaremos SORT.
##### ORGANIZATION
Indicamos la organización de los registros de nuestro fichero, podrá ser SEQUENTIAL, RELATIVE o INDEXED, si nuestro archivo fuera secuencial se podrían omitir ésta clausula asi como las restantes.
De ésta organización se deriva el formato del fichero, SEQUENTIAL si los registros se graban secuencialmente conforme se dan entrada sin importar si están o no repetidos, un ejemplo claro son los archivos de impresora, todos los listados son secuenciales.
RELATIVE, si cada registro es identificado por un valor entero con su posición relativa (practicamente no se utiliza).
INDEXED es la mas utilizada e identifica a ficheros que sus registros son accesibles mediante una clave unica e irrepetible o por varias que pueden estar duplicadas, cualquier fichero de mantenimiento, por ejemplo de ARTICULOS, podría ser INDEXED, y cada código será único para cada artículo y con el nos iremos a su posición y podremos ver todos los demas datos que hagan referencia al registro.
Existe también para los archivos de texto, tipo AUTOEXEC.BAT la posibilidad de asignarlos directamente especificando LINE SEQUENTIAL en ésta clausula.
##### ACCESS MODE
Indica el modo de acceso al fichero, puede ser SEQUENTIAL, RANDOM o DYNAMIC, si no se especifica ninguno o si el fichero es SEQUENTIAL entiende que el modo será SEQUENTIAL.
RANDOM indica que accederemos a el aleatoriamente por su clave y DYNAMIC (la mas utilizada) con la que podremos acceder al fichero en el modo que queramos dentro del programa, unas veces secuencialmente, si nos interesa, otras veces por su clave.
##### RECORD KEY
Se utiliza solo si el fichero es indexado y en el decimos cual es el nombre de la clave por la cual accederemos a los registros. Esta deberá ser alfanúmerica y tendrá que estar especificada en la FD del fichero. Si el archivo fuera RELATIVE, esta clausula se sustituiría por RELATIVE KEY e indicará el número de registro del fichero, deberá estar declarado en la WORKING-STORAGE SECTION como una variable numérica sin signo.
##### ALTERNATE RECORD KEY
Solo para ficheros indexados e identifican una o mas claves alternadas para nuestros registros, por ejemplo en un fichero de clientes cuya clave principal sería el código, podríamos asignar como clave alternativa el NIF, y podríamos acceder a el por las dos claves, bien por código o bien por NIF, será también alfanumérico y deberá también estar declarado en la FD. Si aparece WITH DUPLICATES, indica que ésta clave alternativa pudiera estar duplicada, por ejemplo si hubieramos escogido como clave alternada además del NIF, el Nombre del cliente, podría darse el caso de que dos clientes tuvieran el mismo nombre.
##### FILE STATUS
Damos un nombre de una variable que especificaremos en la WORKING como un campo alfanumérico de dos caracteres donde el programa depositará el código de error que ocurra en el fichero, dependiendo del valor nosotros podremos operar o hacer alguna acción en concreto.

El párrafo I-O CONTROL se utiliza par indicarle al programa cuantos archivos van a utilizar el mismo area de memoria para trabajar, os puedo decir poco mas de éste párrafo porque yo no lo he utilizado nunca (lo que no quiere decir que no sea útil).

## **[<](#manual-cobol)**
## DATA DIVISION
---

## **[<](#manual-cobol)**
## Instrucciones de Cálculo
---

## **[<](#manual-cobol)**
## Instrucciones de Archivos
---

## **[<](#manual-cobol)**
## Instrucciones de Pantalla
---

## **[<](#manual-cobol)**
## Instrucciones de Variables
---

## **[<](#manual-cobol)**
## Instrucción PERFORM
---
