# **MANUAL PYTHON**

![Python](Fotos/Manual_Python/Python_logo.png)

1. **[Introducción a Python](#introducción-a-python)**
2. **[Tipos de Datos Primitivos Simples](#tipos-de-datos-primitivos-simples)**
3. **[Entrada y Salida por Terminal](#entrada-y-salida-por-terminal)**
4. **[Condicionales](#condicionales)**
5. **[Bucles](#bucles)**
6. **[Listas](#listas)**
7. **[Tuplas](#tuplas)**
8. **[Diccionarios](#diccionarios)**
9. **[Funciones](#funciones)**
10. **[Programación funcional](#programación-funcional)**
11. **[Comprensión de Colecciones](#comprensión-de-colecciones)**
12. **[Ficheros](#ficheros)**
13. **[Excepciones](#excepciones)**
14. **[Programación Orientada a Objetos](#programación-orientada-a-objetos)**
15. **[Módulos](#módulos)**
16. **[Librería Datetime](#librería-datetime)**
17. **[Librería Numpy](#librería-numpy)**
18. **[Librería Pandas](#librería-pandas)**
19. **[Librería Matplotlib](#librería-matplotlib)**
20. **[Librería itertools](#librería-itertools)**
21. **[Librería Turtle](#librería-turtle)**
22. **[Librería Tkinter](#librería-tkinter)**
23. **[Librería Pygame](#librería-pygame)**
24. **[Expresiones regulares](#expresiones-regulares)**
25. **[Depuración de código](#depuración-de-código)**
26. **[Trucos y consejos](#trucos-y-consejos)**

## Introducción a Python
---
### ¿Qué es Python?
[Python](https://www.python.org/) es un lenguaje de programación de alto nivel multiparadigma que permite:

- Programación imperativa
- Programación funcional
- Programación orientada a objetos

Fue creado por Guido van Rossum en 1990 aunque actualmente es desarrollado y mantenido por la *Python Software Foundation*.

### Principales ventajas de Python
- Es de código abierto (certificado por la OSI).
- Es interpretable y compilable.
- Es fácil de aprender gracias a que su sintaxis es bastante legible para los humanos.
- Es un lenguaje maduro (+30 años).
- Es fácilmente extensible e integrable en otros lenguajes (C, java).
- Esta mantenido por una gran comunidad de desarrolladores y hay multitud de recursos para su aprendizaje.

### Tipos de Ejecución
#### Interpretado en la consola de Python
Se ejecuta cada instrucción que introduce el usuario de manera interactiva.
~~~~ python
> python
>>> name = "Yeibi"
>>> print("Hola", name)
Hola Yeibi
~~~~

#### Interpretado en fichero
Se leen y se ejecutan una a una todas las instrucciones del fichero.
~~~~ python
# Fichero hola.py
name = "Yeibi"
print("Hola", name)
~~~~
~~~~ python
> python hola.py
Hola Yeibi
~~~~
También se puede hacer el fichero ejecutable indicando en la primera línea la ruta hasta el intérprete de Python.
~~~~ python
#!/usr/bin/python3
name = "Yeibi"
print("Hola", name)
~~~~
~~~~ python
> chmod +x hola.py
> ./hola.py
Hola Yeibi
~~~~

#### Compilado a bytecode
~~~~ python
# Fichero hola.py
name = "Yeibi"
print("Hola " + name)
~~~~
~~~~ python
> python -O -m py_compile hola.py
> python __pycache__/hola.cpython-37.pyc
Hola Yeibi
~~~~

#### Compilado a ejecutable del sistema
Hay distintos paquetes que permiten compilar a un ejecutable del sistema operativo usado, por ejemplo *pyinstaller*.
~~~~ python
> conda install pyinstaller
> pyinstaller hola.py
> ./dist/hola/hola
Hola Yeibi
~~~~

## Tipos de Datos Primitivos Simples
---
### Tipos de datos primitivos simples
- **Números** (numbers): Secuencia de dígitos (pueden incluir el - para negativos y el . para decimales) que representan números.
> Ejemplo: 0, -1, 3.1415.
- **Cadenas** (strings): Secuencia de caracteres alfanuméricos que representan texto. Se escriben entre comillas simples o dobles.
> Ejemplo: ‘Hola’, “Adiós”.
- **Booleanos** (boolean): Contiene únicamente dos elementos *\<True>* y *\<False>* que representan los valores lógicos verdadero y falso respectivamente.

Estos datos son inmutables, es decir, su valor es constante y no puede cambiar.

### Tipos de datos primitivos compuestos (contenedores)
- **Listas** (lists): Colecciones de objetos que representan secuencias ordenadas de objetos de distintos tipos. Se representan con corchetes y los elementos se separan por comas.
> Ejemplo: [1, “dos”, [3, 4], True].
- **Tuplas** (tuples). Colecciones de objetos que representan secuencias ordenadas de objetos de distintos tipos. A diferencia de las listas son inmutables, es decir, que no cambian durante la ejecución. Se representan mediante paréntesis y los elementos se separan por comas.
> Ejemplo: (1, ‘dos’, 3)
- **Diccionarios** (dictionaries): Colecciones de objetos con una clave asociada. Se representan con llaves, los pares separados por comas y cada par contiene una clave y un objeto asociado separados por dos puntos.
> Ejemplo: {‘pi’:3.1416, ’e’:2.718}.

### Clase de un dato (*type()*)
La clase a la que pertenece un dato se obtiene con el comando *type()*.
~~~~ python
>>> type(1)
<class 'int'>
>>> type("Hola")
<class 'str'>
>>> type([1, "dos", [3, 4], True])
<class 'list'>
>>>type({'pi':3.1416, 'e':2.718})
<class 'dict'>
>>>type((1, 'dos', 3))
<class 'tuple'>
~~~~

### Números (clases *int* y *float*)
Secuencia de dígitos (pueden incluir el - para negativos y el . para decimales) que representan números. Pueden ser enteros (*int*) o reales (*float*).
~~~~ python
>>> type(1)
<class 'int'>
>>> type(-2)
<class 'int'>
>>> type(2.3)
<class 'float'>
~~~~

#### Operadores aritméticos
Realizan operaciones algebraicas para el cálculo entre dos operandos.

|Operadores|Equivalencia|
|:-:|:-|
|+|Suma|
|-|Resta|
|*|Producto|
|/|División|
|//|Cociente de la división|
|%|Resto de la disvisión|
|**|Potencia|

> ⚠️ Orden de prioridad de evaluación:  
>> Funciones predefinidas => Potencias => Productos y cocientes => Sumas y restas

Se puede saltar el orden de evaluación utilizando paréntesis ( ).
~~~~ python
>>> 2+3
5
>>> 5*-2
-10
>>> 5/2
2.5
>>> 10//2
5
>>> 10%2
0
>>> (2+3)**2
25
~~~~
> ⚠️ Para obtener el resultado en tipo flotante, uno de los operandos también debe ser de tipo flotante.

#### Operadores de asignación
Asignan a una variable un valor, pudiéndose mezclar con operadores aritméticos y bit a bit

|Operador|Equivalencia|
|:-:|:-|
|=|Otorga valor a una variable|
|+=| a = a + n|
|-=| a = a - n|
|*=| a = a * n|
|/=| a = a / n|
|//=| a = a // n|
|%=|a = a % n|
|**=|a = a ** n|
|\|=|a = a \| n|
|&=|a = a & n|
|^=|a = a ^ n|
|<<=|a = a << n|
|>>=|a = a >> n|

#### Operadores bit a bit
Realizan operaciones en los operandos bit a bit (en binario)

|Operador|Equivalencia|
|:-:|:-|
|\||**OR** bit a bit|
|^|**XOR** bit a bit|
|&|**AND** bit a bit|
|~|**NOT** - Obtiene los bits invertidos|
|>>n|Desplaza n bits a la derecha|
|<<n|Desplaza n bits a la izquierda|

~~~~ python
>>> x = 10  # 01010
>>> y = 7   # 00111
>>> x | y   # 01010 OR 00111 --> 01111
15
>>> x ^ y   # 01010 XOR 00111 --> 01101
13
>>> x & y   # 01010 AND 00111 --> 00010
2
>>> y << 1    # 00111 --> 01110
14
>>> y >> 1    # 00111 --> 00011
3
>>> ~x      # 01010 --> -(01010 + 00001) = -01011
-11
~~~~

### Cadenas (clase *str*)
Secuencia de caracteres alfanuméricos que representan texto. Se escriben entre comillas sencillas ’ o dobles “.
~~~~ python
'Python'
"123"
'True'
# Cadena vacía
''
# Cadena con un espacio en blanco
' '
# Cambio de línea
'\n'
# Tabulador
'\t'
~~~~

#### Acceso a los elementos de una cadena
Cada carácter tiene asociado un índice que permite acceder a él.

|Cadena|P|y|t|h|o|n|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|Índice positivo|0|1|2|3|4|5|
|Índice negativo|-6|-5|-4|-3|-2|-1|

- *c[i]* devuelve el carácter de la cadena *c* con el índice *i*.

> ⚠️ El índice del primer carácter de la cadena es *0*.

También se pueden utilizar índices negativos para recorrer la cadena del final al principio.

> ⚠️ El índice del último carácter de la cadena es *-1*.

~~~~ python
>>> 'Python'[0]
'P'
>>> 'Python'[1]
'y'
>>> 'Python'[-1]
'n'
>>> 'Python'[6]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
~~~~

#### Subcadenas
- *c[i:j:k]* : Devuelve la subcadena de c desde el carácter con el índice *i* hasta el carácter anterior al índice *j*, tomando caracteres cada *k*.
~~~~ python
>>> 'Python'[1:4]
'yth'
>>> 'Python'[1:1]
''
>>> 'Python'[2:]
'thon'
>>> 'Python'[:-2]
'Pyth'
>>> 'Python'[:]
'Python'
>>> 'Python'[0:6:2]
'Pto'
~~~~

#### Operaciones con cadenas
- *c1 + c2* : Devuelve la cadena resultado de concatenar las cadenas c1 y c2.
- *c * n* : Devuelve la cadena resultado de concatenar n copias de la cadena c.
- *c1 in c2* : Devuelve *\<True>* si c1 es una cadena concenida en c2 y *\<False>* en caso contrario.
- *c1 not in c2* : Devuelve *\<True>* si c1 es una cadena no concenida en c2 y *\<False>* en caso contrario.
~~~~ python
>>> 'Me gusta ' + 'Python'
'Me gusta Python'
>>> 'Python' * 3
'PythonPythonPython'
>>> 'y' in 'Python'
True
>>> 'tho' in 'Python'
True
>>> 'to' not in 'Python'
True
~~~~

#### Operaciones de comparación de cadenas
- *c1 == c2* : Devuelve *\<True>* si la cadena *c1* es igual que la cadena *c2* y *\<False>* en caso contrario.
- *c1 > c2* : Devuelve *\<True>* si la cadena *c1* sucede a la cadena *c2* y *\<False>* en caso contrario.
- *c1 < c2* : Devuelve *\<True>* si la cadena *c1* antecede a la cadena *c2* y *\<False>* en caso contrario.
- *c1 >= c2* : Devuelve *\<True>* si la cadena *c1* sucede o es igual a la cadena *c2* y *\<False>* en caso contrario.
- *c1 <= c2* : Devuelve *\<True>* si la cadena *c1* antecede o es igual a la cadena *c2* y *\<False>* en caso contrario.
- *c1 != c2* : Devuelve *\<True>* si la cadena *c1* es distinta de la cadena *c2* y *\<False>* en caso contrario.

> ⚠️ Utilizan el orden establecido en el *[código ASCII](https://elcodigoascii.com.ar/)*.

~~~~ python
>>> 'Python' == 'python'
False
>>> 'Python' < 'python'
True
>>> 'a' > 'Z'
True
>>> 'A' >= 'Z'
False
>>> '' < 'Python'
True
~~~~

#### Funciones de cadenas
- *len(c)* : Devuelve el número de caracteres de la cadena *c*.
- *min(c)* : Devuelve el carácter menor de la cadena *c*.
- *max(c)* : Devuelve el carácter mayor de la cadena *c*.
- *c.upper()* : Devuelve la cadena con los mismos caracteres que la cadena *c* pero en mayúsculas.
- *c.lower()* : Devuelve la cadena con los mismos caracteres que la cadena *c* pero en minúsculas.
- *c.title()* : Devuelve la cadena con los mismos caracteres que la cadena *c* con el primer caracter de cada elemento en mayúsculas y el resto en minúsculas.
- *c.capitalize()* : Devuelve la cadena con los mismos caracteres que la cadena *c* con el primer caracter en mayúsculas y el resto en minúsculas.
- *c.swapcase()* :Devuelve la cadena con los mismos caracteres que la cadena *c* pero pasando las minúsculas a mayúsculas y viceversa.
- *c.ljust(n)* / *c.rjust(n)*: Devuleve una cadena de longitud *n* con la cadena *c* a la derecha/izquierda.
- *c.center(n)* : Devulve una cadena de longitud *n* con la cedena *c* en el centro.
- *c1.find(c2)* : Devuelve la posición de la cadena *c2* dentro de la cadena *c1* la primera vez que aparece. Si no encuentra nada devuelve un -1.
- *c1.rfind(c2)* : Devuelve la posición de la cadena *c2* dentro de la cadena *c1* la última vez que aparece. Si no encuentra nada devuelve un -1.
- *c.split(delimitador)* : Devuelve la lista formada por las subcadenas que resultan de partir la cadena *c* usando como delimitador la cadena *delimitador*. Si no se especifica el delimitador utiliza por defecto el espacio en blanco.
- *c.strip(caracteres)* : Devuelve la cadena formada tras borrar los caracteres *caracteres* de la cadena *c*. Primero borra desde la izquierda mientras haya caracteres que se encuentren en *caracteres* y después lo mismo por la derecha.
- *c1.replace(c2 , c3)* : Devuelve una cadena a partir de reemplazar todas las cadena *c2* por la cadena *c3* dentro de la cadena *c1*.

~~~~ python
>>> len('Python')
6
>>> min('Python')
'P'
>>> max('Python')
'y'
>>> 'Python'.upper()
'PYTHON'
>>> 'Python'.lower()
'python'
>>> 'i love python'.title()
'I Love Python'
>>> 'i love python'.capitalize()
'I love python'
>>> 'left'.ljust(10)
'left      '
>>> 'right'.rjust(10)
'     right'
>>> 'center'.center(10)
'  center  '
>>> 'Hello world'.find('world')
6
>>> 'Hello world'.find('x')
-1
>>> 'Hello world'.rfind('o')
7
>>> 'A,B,C'.split(',')
['A', 'B', 'C']
>>> 'I love Python'.split()
['I', 'love', 'Python']
>>> '***///>>>*Hola*<<<-+-+-+'.strip('*/+-')
'>>>*Hola*<<<'
>>> 'Te quiero'.replace(' quiero' , 'quila')
'Tequila'
~~~~

#### Verificadores de cadenas
- *c1.endswith(c2)* : Devuelve *\<True>* si la cadena *c1* termina con la cadena *c2* y *\<False>* en caso contrario.
- *c.isalnum()* : Devuelve *\<True>* si todos los caracteres de la cadena *c* son alfanuméricos y *\<False>* en caso contrario. El caracter espacio no cuenta como alfanumérico.
- *c.isalpha()* : Devuelve *\<True>* si todos los caracteres de la cadena *c* son alfabetos y *\<False>* en caso contrario.
- *c.isdecimal()* : Devuelve *\<True>* si todos los caracteres de la cadena *c* son decimales y *\<False>* en caso contrario.
- *c.islower()* : Devuelve *\<True>* si todos los caracteres en la cadena *c* están en minúsculas y *\<False>* en caso contrario.
- *c.isupper()* : Devuelve *\<True>* si todos los caracteres en la cadena *c* están en mayúsculas y *\<False>* en caso contrario.
- *c.isprintable()* : Devuelve *\<True>* si la cadena *c* se puede imprimir y *\<False>* en caso contrario. Los caracteres como '\ t' o '\ n' no se pueden imprimir.

#### Cadenas formateadas (*format()*)
- *c.format(valores)* : Devuelve la cadena *c* tras sustituir los valores de la secuencia valores en los marcadores de posición de *c*. Los marcadores de posición se indican mediante llaves *{}* en la cadena *c*, y el reemplazo de los valores se puede realizar por posición, indicando en número de orden del valor dentro de las llaves, o por nombre, indicando el nombre del valor, siempre y cuando los valores se pasen con el formato nombre = valor.

~~~~ python
>>> 'Un {} vale {} {}'.format('€', 1.12, '$')
'Un € vale 1.12 $'
>>> 'Un {2} vale {1} {0}'.format('€', 1.12, '$')
'Un $ vale 1.12 €'
>>> 'Un {moneda1} vale {cambio} {moneda2}'.format(moneda1 = '€', cambio = 1.12, moneda2 = '$')
'Un € vale 1.12 $'
~~~~

Los marcadores de posición, a parte de indicar la posición de los valores de reemplazo, pueden indicar también el formato de estos. Para ello se utiliza la siguiente sintaxis:

- *\{:n}* : Alinea el valor a la izquierda rellenando con espacios por la derecha hasta los *n* caracteres.
- *\{:>n}* : Alinea el valor a la derecha rellenando con espacios por la izquierda hasta los *n* caracteres.
- *\{:^n}* : Alinea el valor en el centro rellenando con espacios por la izquierda y por la derecha hasta los *n* caracteres.
- *\{:nd}* : Formatea el valor como un número entero con *n* caracteres rellenando con espacios blancos por la izquierda.
- *\{:n.mf}* : Formatea el valor como un número real con un tamaño de *n* caracteres (incluído el separador de decimales) y *m* cifras decimales, rellenando con espacios blancos por la izquierda.

~~~~ python
>>> 'Hoy es {:^10}, mañana {:10} y pasado {:>10}'.format('lunes', 'martes', 'miércoles')
'Hoy es   lunes   , mañana martes     y pasado  miércoles'
>>> 'Cantidad {:5d}'.format(12)'
'Cantidad    12'
>>> 'Pi vale {:8.4f}'.format(3.141592)
'Pi vale   3.1416'
~~~~

### Datos lógicos o booleanos (clase *bool*)
Contiene únicamente dos elementos *\<True>* y *\<False>* que representan los valores lógicos verdadero y falso respectivamente.

False tiene asociado el valor *0* y *\<True>* tiene asociado el valor *1*.

#### Operaciones con valores lógicos
- Operadores lógicos: == (igual que), > (mayor), < (menor), >= (mayor o igual que), \<= (menor o igual que), != (distinto de).
- not b (negación) : Devuelve *\<True>* si el dato booleano *b* es *\<False>*, y *\<False>* en caso contrario.
- b1 and b2 : Devuelve *\<True>* si los datos booleanos *b1* y *b2* son *\<True>*, y *\<False>* en caso contrario.
- b1 or b2 : Devuelve *\<True>* si alguno de los datos booleanos *b1* o *b2* son *\<True>*, y *\<False>* en caso contrario.

#### Tabla de verdad
|x|y|not x|x and y|x or y|
|:-:|:-:|:-:|:-:|:-:|
|False|False|True|False|False|
|False|True|True|False|True|
|True|False|False|False|True|
|True|True|False|True|True|

~~~~ python
>>> not True
False
>>> False or True
True
>>> True and False
False
>>> True and True
True
~~~~

### Conversión de datos primitivos simples
Las siguientes funciones convierten un dato de un tipo en otro, siempre y cuando la conversión sea posible.

- int() convierte a entero.
> int('12') => 12  
> int(True) => 1  
> int('c') => Error
- float() convierte a real.
> float('3.14') => 3.14  
> float(True) => 1.0  
> float('III') => Error
- str() convierte a cadena.
> str(3.14) => '3.14'  
> str(True) => 'True'
- bool() convierte a lógico.
> bool('0') => False  
> bool('3.14') => True  
> bool('') => False  
> bool('Hola') => True

### Variables
Una variable es un identificador ligado a algún valor.

Reglas para nombrarlas:
- Comienzan siempre por una letra, seguida de otras letras o números.
- No se pueden utilizarse palabras reservadas del lenguaje.

A diferencia de otros lenguajes no tienen asociado un tipo y no es necesario declararlas antes de usarlas (tipado dinámico).

Para asignar un valor a una variable se utiliza el operador = y para borrar una variable se utiliza la instrucción *del*.
~~~~ python
lenguaje = 'Python'
x = 3.14
y = 3 + 2
# Asignación múltiple
a1, a2 = 1, 2
# Intercambio de valores
a, b = b, a
# Incremento (equivale a x = x + 2)
x += 2
# Decremento (equivale a x = x - 1)
x -= 1
# Valor no definido
x = None
del x
~~~~

## Entrada y Salida por Terminal
---
### Entrada por terminal (*input()*)
Para asignar a una variable un valor introducido por el usuario en la consola se utiliza la instrucción

- *input(mensaje)* : Muestra la cadena *mensaje* por la terminal y devuelve una cadena con la entrada del usuario.

> ⚠️ El valor devuelto siempre es una cadena, incluso si el usuario introduce un dato numérico.

~~~~ python
>>> language = input('¿Cuál es tu lenguaje favorito? ')
¿Cuál es tu lenguaje favorito? Python
>>> language
'Python'
>>> age = input('¿Cuál es tu edad? ')
¿Cuál es tu edad? 20
>>> age
'20'
~~~~

#### Salida por terminal (*print()*)
Para mostrar un dato por la terminal se utiliza la instrucción
~~~~ python
print(dato1, ..., sep=' ', end='\n', file=sys.stdout)
~~~~
donde:
- *dato1, ...* son los datos a imprimir y pueden indicarse tantos como se quieran separados por comas.
- *sep* establece el separador entre los datos, que por defecto es un espacio en blanco *' '*.
- *end* indica la cadena final de la impresión, que por defecto es un cambio de línea *\n*.
- *file* indica la dirección del flujo de salida, que por defecto es la salida estándar *sys.stdout*.

~~~~ python
>>> print('Hola')
Hola
>>> name = 'Yeibi'
>>> print('Hola', name)
Hola Yeibi
>>> print('El valor de pi es', 3.1415)
El valor de pi es 3.1415
>>> print('Hola', name, sep='')
HolaYeibi
>>> print('Hola', name, end='!\n')
Hola Yeibi!

~~~~

> Si se quiere escribir varios textos seguidos, para no tener que definir la función *print()* por cada línea, se pueden emplear *triples comillas* [*print("""...""")*]. Esto hará que todo lo que se encuentre entre los dos pares de triples comillas se eintrepretene como texto y como salto de línea un nuevo texto en una línea diferente.
> ~~~~ python
> >>> print("""
> >>> Aprende a vivir 
> >>> y sabrás morir bien 
> >>> 
> >>> (Confucio)
> >>> """)
>
> Aprende a vivir 
> y sabrás morir bien 
>  
> (Confucio)
> ~~~~

## Condicionales
---
### Condicionales (*if*)
~~~~ python
if condición1:
    bloque código
elif condición2:
    bloque código
…
else :
    bloque código
~~~~

Evalúa la expresión lógica *condición1* y ejecuta el primer bloque de código si es *\<True>*; si no, evalúa la siguientes condiciones hasta llegar a la primera que es *\<True>* y ejecuta el bloque de código asociado. Si ninguna condición es *\<True>* ejecuta el bloque de código después de *else*:.

Pueden aparecer varios bloques *elif* pero solo uno else al final.

> ⚠️ Los bloques de código deben estar indentados por 4 espacios.

La instrucción condicional permite evaluar el estado del programa y tomar decisiones sobre qué código ejecutar en función del mismo.

~~~~ python
>>> edad = 14
>>> if edad <= 18 : 
...     print('Menor')
... elif edad > 65:
...     print('Jubilado')
... else:
...     print('Activo')
...
Menor
>>> age = 20
>>> if edad <= 18 : 
...     print('Menor')
... elif edad > 65:
...     print('Jubilado')
... else:
...     print('Activo')
...
Activo
~~~~

## Bucles
---
### Bucles condicionales (*while*)
~~~~ python
while condición:
    bloque código
~~~~

Repite la ejecución del bloque de código mientras la expresión lógica *condición* sea cierta.

Se puede interrumpir en cualquier momento la ejecución del bloque de código con la instrucción *break*.

> ⚠️ El bloque de código debe estar indentado por 4 espacios.

~~~~ python
>>> # Pregunta al usuario por un número hasta que introduce 0.
>>> num = None
>>> while num != 0:
...     num = int(input('Introduce un número: '))
... 
Introduce un número: 2
Introduce un número: 1
Introduce un número: 0
>>> 
~~~~

Alternativa:
~~~~ python
>>> # Pregunta al usuario por un número hasta que introduce 0.
>>> while True:
...     num = int(input('Introduce un número: '))
...     if num == 0:
...         break
...
Introduce un número: 2
Introduce un número: 1
Introduce un número: 0
>>>
~~~~

### Bucles iterativos (*for*)
~~~~ python
for i in secuencia:
    bloque código
~~~~

Repite la ejecución del bloque de código para cada elemento de la secuencia *secuencia*, asignado dicho elemento a *i* en cada repetición.

Se puede interrumpir en cualquier momento la ejecución del bloque de código con la instrucción *break* o saltar la ejecución para un determinado elemento de la secuencia con la instrucción *continue*.

> ⚠️ El bloque de código debe estar indentado por 4 espacios.

Se utiliza fundamentalmente para recorrer colecciones de objetos como cadenas, listas, tuplas o diccionarios.

A menudo se usan con la instrucción *range*:

- *range(fin)* : Genera una secuencia de números enteros desde *0* hasta *fin-1*.
- *range(inicio, fin, salto)* : Genera una secuencia de números enteros desde *inicio* hasta *fin-1* con un incremento de *salto*.

~~~~ python
>>> palabra = 'Python'
>>> for letra in palabra:
...     print(letra)
... 
P
y
t
h
o
n
~~~~
~~~~ python
>>> for i in range(1, 10, 2):
...     print(i, end=", ")
...
1, 3, 5, 7, 9, >>>
~~~~
~~~~ python
>>> for i in range(1, 10):
...     if i == 5:
...         continue
...     if i == 9:
...         break
...     print(i, end=", ")
...
1, 2, 3, 4, 6, 7, 8, >>>
~~~~

## Listas
---
### Listas
Una *lista* es una secuencia ordenada de objetos de distintos tipos.

Se construyen poniendo los elementos entre corchetes *[ ]* separados por comas.

Se caracterizan por:
- Tienen orden.
- Pueden contener elementos de distintos tipos.
- Son mutables, es decir, pueden alterarse durante la ejecución de un programa.

~~~~ python
# Lista vacía
>>> type([])
<class 'list'>
# Lista con elementos de distintos tipos
>>> [1, "dos", True]
# Listas anidadas
>>> [1, [2, 3], 4]
~~~~

#### Creación de listas mediante la función *list()*
Otra forma de crear listas es mediante la función *list()*.

- *list(c)* : Crea una lista con los elementos de la secuencia o colección *c*.

Se pueden indicar los elementos separados por comas, mediante una cadena, o mediante una colección de elementos iterable.

~~~~ python
>>> list()
[]
>>> list(1, 2, 3)
[1, 2, 3]
>>> list("Python")
['P', 'y', 't', 'h', 'o', 'n']
~~~~

#### Acceso a los elementos de una lista
Se utilizan los mismos operadores de acceso que para cadenas de caracteres.

- *l[i]* : Devuelve el elemento de la lista *l* con el índice *i*.

> ⚠️ El índice del primer elemento de la lista es *0*.

~~~~ python
>>> a = ['P', 'y', 't', 'h', 'o', 'n']
>>> a[0]
'P'
>>> a[5]
'n'
>>> a[6]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
>>> a[-1]
'n'
~~~~

#### Sublistas
- *l[i:j:k]* : Devuelve la sublista desde el elemento de *l* con el índice *i* hasta el elemento anterior al índice *j*, tomando elementos cada *k*.
~~~~ python
>>> a = ['P', 'y', 't', 'h', 'o', 'n']
>>> a[1:4]
['y', 't', 'h']
>>> a[1:1]
[]
>>> a[:-3]
['P', 'y', 't']
>>> a[:]
['P', 'y', 't', 'h', 'o', 'n']
>>> a[0:6:2]
['P', 't', 'o']
~~~~

#### Operaciones que no modifican una lista
- *len(l)* : Devuelve el número de elementos de la lista *l*.
- *min(l)* : Devuelve el mínimo elemento de la lista *l*, siempre que los datos sean comparables.
- *max(l)* : Devuelve el máximo elemento de la lista *l*, siempre que los datos sean comparables.
- *sum(l)* : Devuelve la suma de los elementos de la lista *l*, siempre que los datos se puedan sumar.
- *dato in l* : Devuelve *\<True>* si el *dato* dato pertenece a la lista *l* y *\<False>* en caso contrario.
- *l.index(dato)* : Devuelve la posición que ocupa en la lista *l* el primer elemento con valor *dato*. Si no encunetra nada devuelve un *ValueError*.
- *l.count(dato)* : Devuelve el número de veces que el valor *dato* está contenido en la lista *l*.
- *all(l)* : Devuelve *\<True>* si todos los elementos de la lista *l* son *\<True>* y *\<False>* en caso contrario.
- *any(l)* : Devuelve *\<True>* si algún elemento de la lista *l* es *\<True>* y *\<False>* en caso contrario.
- *separador.join(l)* : Devuelve una cadena formada por los datos de la lista *l* con el separador *separador* entre cada uno, siempre que los datos sean del tipo *string*.

~~~~ python
>>> a = [1, 2, 2, 3]
>>> len(a)
4
>>> min(a)
1
>>> max(a)
3
>>> sum(a)
8
>>> 3 in a
True
>>> a.index(2)
1
>>> a.count(2)
2
>>> all(a)
True
>>> any([0, False, 3<2])
False
>>> '#'.join(['a', 'b', 'c'])
'a#b#c'
~~~~

#### Operaciones que modifican una lista
- *l1 + l2* : Crea una nueva lista concatenando los elementos de la listas *l1* y *l2*.
- *l.append(dato)* : Añade *dato* al final de la lista *l*.
- *l.extend(sequencia)* : Añade los datos de *sequencia* al final de la lista *l*.
- *l.insert(índice, dato)* : Inserta *dato* en la posición *índice* de la lista *l* y desplaza los elementos una posición a partir de la posición *índice*. Si la posición *índice* está fuera del rango de la lista *l*, el dato *dato* se insertará en uno de los extremos de la lista *l*.
- *l.remove(dato)* : Elimina el primer elemento con valor *dato* en la lista *l* y desplaza los que están por detrás de él una posición hacia delante.
- *l.pop([índice])* : Devuelve el dato en la posición *índice* y lo elimina de la lista *l*, desplazando los elementos por detrás de él una posición hacia delante. Por defecto elimina el último valor de la lista.
- *l.sort()* : Ordena los elementos de la lista *l* de acuerdo al orden predefinido, siempre que los elementos sean comparables.
- *l.reverse()* : invierte el orden de los elementos de la lista *l*.

~~~~ python
>>> a = [1, 3]
>>> b = [2, 4, 6]
>>> a+b
[1, 2, 3, 4]
>>> a.append(5)
>>> a
[1, 3, 5]
>>> a.remove(3)
>>> a
[1, 5]
>>> a.insert(1, 3)
>>> a
[1, 3, 5]
>>> a.insert(6, 8)
[1, 3, 5, 8]
>>> a.insert(-5, 0)
[0, 1, 3, 5, 8]
>>> b.pop()
6
>>> c = a + b
>>> c
[1, 3, 5, 2, 4]
>>> c.sort()
>>> c
[1, 2, 3, 4, 5]
>>> c.reverse()
>>> c
[5, 4, 3, 2, 1]
~~~~

#### Copia de listas
Existen dos formas de copiar listas:
- **Copia por referencia** *l1 = l2* : Asocia la la variable *l1* la misma lista que tiene asociada la variable *l2*; es decir, ambas variables apuntan a la misma dirección de memoria. Cualquier cambio que hagamos a través de *l1* o *l2* afectará a la misma lista.
- **Copia por valor** *l1 = list(l2)* : Crea una copia de la lista asociada a *l2* en una dirección de memoria diferente y se la asocia a *l1*. Las variables apuntan a direcciones de memoria diferentes que contienen los mismos datos. Cualquier cambio que hagamos a través de *l1* no afectará a la lista de *l2* y viceversa, salvo que la propia lista tenga una lista como valor. En este último caso, la copia de dicho valor será como una *copia por referencia*. (*l1 = l2.copy()* causará el mismo caso).
~~~~ python
>>> a = [1, 2, 3]
>>> # copia por referencia
>>> b = a
>>> b
[1, 2, 3]
>>> b.remove(2)
>>> b
[1, 3]
>>> a
[1, 3]
~~~~
~~~~ python
>>> a = [1, 2, 3, [4, 5]]
>>> # copia por valor
>>> b = list(a)
>>> b
[1, 2, 3, [4, 5]]
>>> b.remove(2)
>>> b
[1, 3, [4, 5]]
>>> a
[1, 2, 3, [4, 5]]
>>> b[2][1] = 6
>>> b
[1, 3, [4, 6]]
>>> a
[1, 2, 3, [4, 6]]
~~~~

Para solucionar el sub-problema de referencia de la copia debemos usar *l1 = copy.deepcopy(l2)* de la librería *copy*.
~~~~ python
>>> import copy
>>> a = [1, 2, 3, [4, 5]]
>>> b = copy.deepcopy(a)
>>> b
[1, 2, 3, [4, 5]]
>>> b.remove(2)
>>> b[2][1] = 6
>>> b
[1, 3, [4, 6]]
>>> a
[1, 2, 3, [4, 5]]
~~~~

## Tuplas
---
### Tuplas
Una tupla es una secuencia ordenada de objetos de distintos tipos.

Se construyen poniendo los elementos entre corchetes *( )* separados por comas.

Se caracterizan por:
- Tienen orden.
- Pueden contener elementos de distintos tipos.
- Son inmutables, es decir, no pueden alterarse durante la ejecución de un programa.

Se usan habitualmente para representar colecciones de datos una determinada estructura semántica, como por ejemplo un vector o una matriz.

~~~~ python
# Tupla vacía
type(())
<class 'tuple'>
# Tupla con elementos de distintos tipos
(1, "dos", True)
# Vector
(1, 2, 3)
# Matriz
((1, 2, 3), (4, 5, 6))
~~~~

#### Creación de tuplas mediante la función *tuple()*
Otra forma de crear tuplas es mediante la función *tuple()*.

- *tuple(c)* : Crea una tupla con los elementos de la secuencia o colección *c*.

Se pueden indicar los elementos separados por comas, mediante una cadena, o mediante una colección de elementos iterable.

~~~~ python
>>> tuple()
()
>>> tuple(1, 2, 3)
(1, 2, 3)
>>> tuple("Python")
('P', 'y', 't', 'h', 'o', 'n')
>>> tuple([1, 2, 3])
(1, 2, 3)
~~~~

#### Operaciones con tuplas
El acceso a los elementos de una tupla se realiza del mismo modo que en las listas. También se pueden obtener subtuplas de la misma manera que las sublistas.

Las operaciones de listas que no modifican la lista también son aplicables a las tuplas.

~~~~ python
>>> a = (1, 2, 3)
>>> a[1]
2
>>> len(a)
3
>>> a.index(3)
2
>>> 0 in a
False
>>> b = ((1, 2, 3), (4, 5, 6))
>>> b[1]
(4, 5, 6)
>>> b[1][2]
6
~~~~

## Diccionarios
---
### Diccionarios
Un diccionario es una colección de pares formados por una clave y un valor asociado a la clave.

Se construyen poniendo los pares entre llaves *{ }* separados por comas, y separando la clave del valor con dos puntos *:*.

Se caracterizan por:
- No tienen orden.
- Pueden contener elementos de distintos tipos.
- Son mutables, es decir, pueden alterarse durante la ejecución de un programa.
- Las claves son únicas, es decir, no pueden repetirse en un mismo diccionario, y pueden ser de cualquier tipo de datos inmutable.

~~~~ python
# Diccionario vacío
type({})
<class 'dict'>
# Diccionario con elementos de distintos tipos
{'nombre':'Javier', 'despacho': 218, 'email':'jgc4297@gmail.com'}
# Diccionarios anidados
{'nombre_completo':{'nombre': 'Javier', 'Apellidos': 'González Carreiro'}}
~~~~

#### Acceso a los elementos de un diccionario
- *d[clave]* devuelve el valor del diccionario *d* asociado a la clave *clave*. Si en el diccionario no existe esa clave devuelve un error.
- *d.get(clave, valor)* devuelve el valor del diccionario *d* asociado a la clave *clave*. Si en el diccionario no existe esa clave devuelve valor, y si no se especifica un valor por defecto devuelve *None*.

~~~~ python
>>> a = {'nombre':'Javier', 'despacho': 218, 'email':'jgc4297@gmail.com'}
>>> a['nombre']
'Javier'
>>> a['despacho'] = 210
>>> a
{'nombre':'Javier', 'despacho': 210, 'email':'jgc4297@gmail.com'}
>>> a.get('email')
'jgc4297@gmail.com'
>>> a.get('universidad', 'ETSIB')
'ETSIB'
~~~~

#### Operaciones que no modifican un diccionario
- *len(d)* : Devuelve el número de elementos del diccionario *d*.
- *min(d)* : Devuelve la mínima clave del diccionario *d* siempre que las claves sean comparables.
- *max(d)* : Devuelve la máxima clave del diccionario *d* siempre que las claves sean comparables.
- *sum(d)* : Devuelve la suma de las claves del diccionario *d*, siempre que las claves se puedan sumar.
- *clave in d* : Devuelve *\<True>* si la clave *clave* pertenece al diccionario *d* y *\<False>* en caso contrario.
- *d.keys()* : Devuelve un iterador sobre las claves de un diccionario.
- *d.values()* : Devuelve un iterador sobre los valores de un diccionario.
- *d.items()* : Devuelve un iterador sobre los pares clave-valor de un diccionario.

~~~~ python
>>> a = {'nombre':'Javier', 'despacho': 218, 'email':'jgc4297@gmail.com'}
>>> len(a)
3
>>> min(a)
'despacho'
>>> 'email' in a
True
>>> a.keys()
dict_keys(['nombre', 'despacho', 'email'])
>>> a.values()
dict_values(['Javier', 218, 'jgc4297@gmail.com'])
>>> a.items()
dict_items([('nombre', 'Javier'), ('despacho', 218), ('email', 'jgc4297@gmail.com')])
~~~~

#### Operaciones que modifican un diccionario
- *d[clave] = valor* : Añade al diccionario *d* el par formado por la clave *clave* y el valor *valor*.
- *d.update(d2)* :: Añade los pares del diccionario *d2* al diccionario *d*.
- *d.pop(clave, alternativo)* : Devuelve del valor asociado a la clave *clave* del diccionario *d* y lo elimina del diccionario. Si la clave no está devuelve el valor *alternativo*.
- *d.popitem()* : Devuelve la tupla formada por la clave y el valor del último par añadido al diccionario *d* y lo elimina del diccionario.
- *del d[clave]* : Elimina del diccionario *d* el par con la clave *clave*.
- *d.clear()* : Elimina todos los pares del diccionario *d* de manera que se queda vacío.

~~~~ python
>>> a = {'nombre':'Javier', 'despacho': 218, 'email':'jgc4297@gmail.com'}
>>> a['universidad'] = 'ETSIB'
>>> a
{'nombre': 'Javier', 'despacho': 218, 'email': 'jgc4297@gmail.com', 'universidad': 'ETSIB'}
>>> a.pop('despacho')
218
>>> a
{'nombre': 'Javier', 'email': 'jgc4297@gmail.com', 'universidad': 'ETSIB'}
>>> a.popitem()
('universidad', 'ETSIB')
>>> a
{'nombre': 'Javier', 'email': 'jgc4297@gmail.com'}
>>> del a['email']
>>> a
{'nombre': 'Javier'}
>>> a.clear()
>>> a
{}
~~~~

#### Copia de diccionarios
Existen dos formas de copiar diccionarios:
- **Copia por referencia** *d1 = d2* : Asocia la la variable *d1* el mismo diccionario que tiene asociado la variable *d2*, es decir, ambas variables apuntan a la misma dirección de memoria. Cualquier cambio que hagamos a través de *l1* o *l2* afectará al mismo diccionario.
- **Copia por valor** *d1 = dict(d2)* : Crea una copia del diccionario asociado a *d2* en una dirección de memoria diferente y se la asocia a *d1*. Las variables apuntan a direcciones de memoria diferentes que contienen los mismos datos. Cualquier cambio que hagamos a través de *l1* no afectará al diccionario de *l2* y viceversa.

~~~~ python
>>> a = {1:'A', 2:'B', 3:'C'}
>>> # copia por referencia
>>> b = a
>>> b
{1:'A', 2:'B', 3:'C'}
>>> b.pop(2)
>>> b
{1:'A', 3:'C'}
>>> a
{1:'A', 3:'C'}
~~~~
~~~~ python
>>> a = {1:'A', 2:'B', 3:'C'}
>>> # copia por valor
>>> b = dict(a)
>>> b
{1:'A', 2:'B', 3:'C'}
>>> b.pop(2)
>>> b
{1:'A', 3:'C'}
>>> a
{1:'A', 2:'B', 3:'C'}
~~~~

## Funciones
---
### Funciones (def)
Una función es un bloque de código que tiene asociado un nombre, de manera que cada vez que se quiera ejecutar el bloque de código basta con invocar el nombre de la función.

Para declarar una función se utiliza la siguiente sintaxis:

~~~~ python
def <nombre-funcion> (<parámetros>):
     bloque código
     return <objeto>
~~~~

~~~~ python
>>> def bienvenida():
...     print('¡Bienvenido a Python!')
...     return
...
>>> type(bienvenida)
<class 'function'>
>>> bienvenida()
¡Bienvenido a Python!
~~~~

#### Parámetros y argumentos de una función
Una función puede recibir valores cuando se invoca a través de unas variables conocidas como *parámetros* que se definen entre paréntesis en la declaración de la función. En el cuerpo de la función se pueden usar estos parámetros como si fuesen variables.

Los valores que se pasan a la función en una llamada o invocación concreta de ella se conocen como *argumentos* y se asocian a los parámetros de la declaración de la función.

~~~~ python
>>> def bienvenida(nombre):
...     print('¡Bienvenido a Python', nombre + '!')
...     return
...
>>> bienvenida('Yeibi')
¡Bienvenido a Python Yeibi!
~~~~

#### Paso de argumentos a una función
Los argumentos se pueden pasar de dos formas:

- **Argumentos posicionales** : Se asocian a los parámetros de la función en el mismo orden que aparecen en la definición de la función.
- **Argumentos nominales** : Se indica explícitamente el nombre del parámetro al que se asocia un argumento de la forma *parametro = argumento*.

~~~~ python
>>> def bienvenida(nombre, apellido):
...     print('¡Bienvenido a Python', nombre, apellido + '!')
...     return
...
>>> bienvenida('Javier', 'González')
¡Bienvenido a Python Javier González!
>>> bienvenida(apellido = 'González', nombre = 'Javier')
¡Bienvenido a Python Javier González!
~~~~

#### Retorno de una función
Una función puede devolver un objeto de cualquier tipo tras su invocación. Para ello el objeto a devolver debe escribirse detrás de la palabra reservada *return*. Si no se indica ningún objeto, la función no devolverá nada.
~~~~ python
>>> def area_triangulo(base, altura):
...     return base * altura / 2
...
>>> area_triangulo(2, 3)
3
>>> area_triangulo(4, 5)
10
~~~~

Una función puede devolver más de un objeto separándolos por comas tras la palabra reservada *return*. En tal caso, la función agrupará los objetos en una tupla y devolverá la tupla.

### Argumentos por defecto
En la definición de una función se puede asignar a cada parámetro un argumento por defecto, de manera que si se invoca la función sin proporcionar ningún argumento para ese parámetro, se utiliza el argumento por defecto.

~~~~ python
>>> def bienvenida(nombre, lenguaje = 'Python'):
...     print('¡Bienvenido a', lenguaje, nombre + '!')
...     return
...
>>> bienvenida('Yeibi')
¡Bienvenido a Python Yeibi!
>>> bienvenida('Yeibi', 'Java')
¡Bienvenido a Java Yeibi!
~~~~

> ⚠️ Los parámetros con un argumento por defecto deben indicarse después de los parámetros sin argumentos por defectos. De lo contrario se produce un error.

### Pasar un número indeterminado de argumentos
Por último, es posible pasar un número variable de argumentos a un parámetro. Esto se puede hacer de dos formas:

- **parametro* : Se antepone un asterisco al nombre del parámetro y en la invocación de la función se pasa el número variable de argumentos separados por comas. Los argumentos se guardan en una lista que se asocia al parámetro.
~~~~ python
>>> def menu(*platos):
...     print('Hoy tenemos: ', end='')
...     for plato in platos:
...         print(plato, end=', ')
...     return
...
>>> menu('pasta', 'pizza', 'ensalada')
Hoy tenemos: pasta, pizza, ensalada,
~~~~

- ***parametro* : Se anteponen dos asteriscos al nombre del parámetro y en la invocación de la función se pasa el número variable de argumentos por pares *nombre = valor*, separados por comas. Los argumentos se guardan en un diccionario que se asocia al parámetro.
~~~~ python
>>> def contacto(**info):
...     print('Datos del contacto')
...     for clave, valor in info.items():
...         print(clave, ":", valor)
...     return
...
>>> contacto(Nombre = "Yeibi", Email = "jgc4297@gmail.com")
Datos del contacto
Nombre : Yeibi
Email : jgc4297@gmail.com
>>> contacto(Nombre = "Yeibi", Email = "jgc4297@gmail.com", Dirección = "Bilbao")
Datos del contacto
Nombre : Yeibi
Email : jgc4297@gmail.com
Dirección : Bilbao
~~~~

### Ámbito de los parámetros y variables de una función
Los parámetros y las variables declaradas dentro de una función son de **ámbito local**, mientras que las definidas fuera de ella son de ámbito **ámbito global**.

Tanto los parámetros como las variables del ámbito local de una función sólo están accesibles durante la ejecución de la función, es decir, cuando termina la ejecución de la función estas variables desaparecen y no son accesibles desde fuera de la función.

~~~~ python
>>> def bienvenida(nombre):
...     lenguaje = 'Python'
...     print('¡Bienvenido a ', lenguaje, nombre + '!')
...     return
...
>>> bienvenida('Yeibi')
¡Bienvenido a Python Yeibi!
>>> lenguaje
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'lenguaje' is not defined
~~~~

Si en el ámbito local de una función existe una variable que también existe en el ámbito global, durante la ejecución de la función la variable global queda eclipsada por la variable local y no es accesible hasta que finaliza la ejecución de la función.

~~~~ python
>>> lenguaje = 'Java'
>>> def bienvenida():
...     lenguaje = 'Python'
...     print('¡Bienvenido a', lenguaje + '!')
...     return
...
>>> bienvenida()
¡Bienvenido a Python!
>>> print(lenguaje)
Java
~~~~

### Paso de argumentos por asignación
En Python los argumentos se pasan a una función por asignación, es decir, se asignan a los parámetros de la función como si fuesen variables locales. De este modo, cuando los argumentos son objetos mutables (listas, diccionarios, etc.) se pasa al parámetro una referencia al objeto, de manera que cualquier cambio que se haga dentro de la función mediante el parámetro asociado afectará al objeto original.

~~~~ python
>>> primer_curso = ['Matemáticas', 'Física']
>>> def añade_asignatura(curso, asignatura):
...     curso.append(asignatura)
...     return
...
>>> añade_asignatura(primer_curso, 'Química')
>>> print(primer_curso)
['Matemáticas', 'Física', 'Química']
~~~~

### Las funciones son objetos
En Python las funciones son objetos como el resto de tipos de datos, de manera que es posible asignar una función a una variable y luego utilizar la variable para hacer la llamada a la función.

~~~~ python
>>> def saludo(nombre):
...     print("Hola", nombre)
...     return
... 
>>> bienvenida = saludo
>>> bienvenida("Yeibi")
Hola Yeibi
~~~~

Esto permite, por tanto, pasar funciones como argumentos en la llamada a una función y que una función pueda devolver otras funciones.

~~~~ python
>>> def impuesto(porcentaje):
...     def aplicar(base):
...             return base * porcentaje / 100
...     return aplicar
... 
>>> iva = impuesto(21)
>>> iva(1000)
210.0
~~~~

### Funciones recursivas
Una función recursiva es una función que en su cuerpo contiene una llama a si misma.

La recursión es una práctica común en la mayoría de los lenguajes de programación ya que permite resolver las tareas recursivas de manera más natural.

Para garantizar el final de una función recursiva, las sucesivas llamadas tienen que reducir el grado de complejidad del problema, hasta que este pueda resolverse directamente sin necesidad de volver a llamar a la función.

~~~~ python
>>> def factorial(n):
...     if n == 0:
...         return 1
...     else:
...         return n * factorial(n-1)
...
>>> f(5)
120
~~~~

#### Funciones recursivas múltiples
Una función recursiva puede invocarse a si misma tantas veces como quiera en su cuerpo.
~~~~ python
>>> def fibonacci(n):
...     if n <= 1:
...         return n
...     else:
...         return fibonacci(n - 1) + fibonacci(n - 2)
...
>>> fibonacci(6)
8
~~~~

#### Los riesgos de la recursión
Aunque la recursión permite resolver las tareas recursivas de forma más natural, hay que tener cuidado con ella porque suele consumir bastante memoria, ya que cada llamada a la función crea un nuevo ámbito local con las variables y los parámetros de la función.

En muchos casos es más eficiente resolver la tarea recursiva de forma iterativa usando bucles.
~~~~ python
>>> def fibonacci(n):
...     a, b = 0, 1
...     for i in range(n):
...         a, b = b, a + b
...     return a
...
>>> fibonacci(6)
8
~~~~

### Generadores (*yield*)
Cuando trabajamos con funciones, la ejecución comienza en la primera línea y continúa hasta que encuentra un *return*, *exception* o el fin de la función. Estas subrutinas devuelven un solo valor a la vez y retornan el control de la ejecución.

En Python, los generadores son funciones que: 
- Tienen la capacidad de producir series de valores en tiempo de ejecución. 
- Pueden ser pausadas para recuperar más tarde el control de la ejecución. 
- Permiten acelerar búsquedas.
- Permiten crear bucles más rápidos.

A diferencia de las funciones anteriores, los generadores terminan con *yield* en vez de *return*. 

~~~~ python
def <nombre-generador>(<parametros>):
    bloque código
    yield <objeto>    
~~~~
 
#### Llamar a los elementos de un generador
- *next(i)* : Devuelve el siguiente elemento de un iterador *i*. 
- *next(i, ifin)* : Devuelve el siguiente elemento de un iterador *i*. Cuando se llega al final del iterador *i* se devuelve el valor *ifin*.
> ⚠️ Cuando se llama a la función *next()* para una lista *i*, la próxima que se emplee la función para la misma lista *i* el valor que devuelva será el siguiente al anterior valor devuleto. Por defecto, cuando se llega al final de la lista *i*, se devuelve el error *StopIteration*.

~~~~ python
>>> def pares():    # generador de números pares
...     i = 1
...     while True:     # bucle infinito de números pares
...         yield i*2
...         i += 1
...
>>> for i in pares():   # imprime los números pares a la vez que se generan
...     print(i)
2
4
6
..
1000
1002
1004
..
~~~~
~~~~ python
>>> def pares():    # generador de números pares
...     i = 1
...     while i < 4:
...         yield i*2
...         i += 1
...
>>> list = pares()  # lista con los primeros 3 números pares
[2, 4, 6]
>>> print(next(list))
2
>>> print(next(list))
4
>>> print(next(list))
6
>>> print(next(list , 'Fin de la generación'))
'Fin de la generación'
~~~~

- *g.send(valor)* : Introduce un valor *valor* en el generador *g* a partir de la última línea ejecutada. La primera vez que se emplea esta función se debe introducir el valor *None* en *valor* al no existir ningún *yield* previo.

~~~~ python
>>> def primeros_primos():
...     n = 1
...     while True:
...         if es_primo(n):
...             n = yield n
...         n += 1
...       
>>> def es_primo(n):    # función que verifica si un número es primo
...     if n > 1:
...         if n == 2:
...             return True
...         if n % 2 == 0:
...             return False
...         for i in range(3, ((n // 2) + 1), 2):
...             if n % i == 0:
...                 return False
...         return True
...     return False
...  
>>> numeros = [10 , 20 , 30 , 40 , 50]
>>> generador = primeros_primos()
>>> generador.send(None)    # Inicialización de .send()
...
>>> for numero in numeros:
...     print(numero , '-->' , generador.send(numero))
10 --> 11
20 --> 23
30 --> 31
40 --> 41
50 --> 53
~~~~

Si quisiermaos simplicar un *yield* en un bucle anidado de una "lista de listas" se podría emplear la salida *yield from*.
> Bucle anidado:
~~~~ python
def generador(elementos):
    for elemento in elementos:
        for subelemento in elemento:
            yield subelemento 
~~~~
> Bucle simplificado:
~~~~ python
def generador(elementos):
    for elemento in elementos:
        yield from elemento 
~~~~

~~~~ python
>>> def cities(*ciudades):
...     for ciudad in ciudades:
...         yield from ciudad   # yield sobre letra de cada ciudad de lista ciudades

>>> lista_ciudades = cities("Madrid", "Sevilla", "Barcelona")
>>> print(next(lista_ciudades))
'M'
>>> print(next(lista_ciudades))
'a'
>>> print(next(lista_ciudades))
'd'
~~~~

### Documentación de funciones
Una práctica muy recomendable cuando se define una función es describir lo que la función hace en un comentario.

En Python esto se hace con un **docstring** que es un tipo de comentario especial se hace en la línea siguiente al encabezado de la función entre tres comillas simples *'''* o dobles *"""*.

Después se puede acceder a la documentación de la función con la función *help(<nombre-función>)*.

~~~~ python
>>> def area_triangulo(base, altura):
... """
... Función que calcula el área de un triángulo.
...
... Parámetros:
...     - base: Un número real con la base del triángulo.
...     - altura: Un número real con la altura del triángulo.
... Salida:
...     Un número real con el área del triángulo de base y altura especificadas.
... """
...     return base * altura / 2
...
>>> help(area_triangulo)
area_triangulo(base, altura)
    Función que calcula el área de un triángulo.

    Parámetros:
        - base: Un número real con la base del triángulo.
        - altura: Un número real con la altura del triángulo.
    Salida:
        Un número real con el área del triángulo de base y altura especificadas.
~~~~

## Programación funcional
---
### Programación funcional
En Python las funciones son objetos de primera clase, es decir, que pueden pasarse como argumentos de una función, al igual que el resto de los tipos de datos.
~~~~ python
>>> def aplica(funcion, argumento):
...     return funcion(argumento)
...
>>> def cuadrado(n):
...     return n*n
...
>>> def cubo(n):
...     return n**3
...
>>> aplica(cuadrado, 5)
25
>>> aplica(cubo, 5)
125
~~~~

#### Funciones anónimas (*lambda*)
Existe un tipo especial de funciones que no tienen nombre asociado y se conocen como **funciones anónimas** o **funciones lambda**.

La sintaxis para definir una función anónima es
~~~~ python
lambda <parámetros> : <expresión>
~~~~

Estas funciones se suelen asociar a una variable o parámetro desde la que hacer la llamada.
~~~~ python
>>> area = lambda base, altura : base * altura
>>> area(4, 5)
10
~~~~

#### Aplicar una función a todos los elementos de una colección iterable (*map*)
- *map(f, c)* : Devuelve una objeto iterable con los resultados de aplicar la función *f* a los elementos de la colección *c*. Si la función *f* requiere *n* argumentos entonces deben pasarse *n* colecciones con los argumentos. Para convertir el objeto en una lista, tupla o diccionario hay que aplicar explícitamente las funciones *list()*, *tuple()* o *dic()* respectivamente.
~~~~ python
>>> def cuadrado(n):
...     return n * n
...
>>> list(map(cuadrado, [1, 2, 3])
[1, 4, 9]
~~~~
~~~~ python
>>> def rectangulo(a, b):
...     return a * b
...
>>> tuple(map(rectangulo, (1, 2, 3), (4, 5, 6)))
(4, 10, 18)
~~~~

#### Filtrar los elementos de una colección iterable (*filter*)
- *filter(f, c)* : Devuelve una objeto iterable con los elementos de la colección *c* que devuelven *\<True>* al aplicarles la función *f*. Para convertir el objeto en una lista, tupla o diccionario hay que aplicar explícitamente las funciones *list()*, *tuple()* o *dic()* respectivamente.
> ⚠️ *f* debe ser una función que recibe un argumento y devuelve un valor booleano.
~~~~ python
>>> def par(n):
...     return n % 2 == 0
...
>>> list(filter(par, range(10))
[0, 2, 4, 6, 8]
~~~~

#### Combinar los elementos de varias colecciones iterables (*zip*)
- *zip(c1, c2, ...)* : Devuelve un objeto iterable cuyos elementos son tuplas formadas por los elementos que ocupan la misma posición en las colecciones *c1*, *c2*, etc. El número de elementos de las tuplas es el número de colecciones que se pasen. Para convertir el objeto en una lista, tupla o diccionario hay que aplicar explícitamente las funciones *list()*, *tuple()* o *dic()* respectivamente.
~~~~ python
>>> asignaturas = ['Matemáticas', 'Física', 'Química', 'Economía']
>>> notas = [6.0, 3.5, 7.5, 8.0]
>>> list(zip(asignaturas, notas))
[('Matemáticas', 6.0), ('Física', 3.5), ('Química', 7.5), ('Economía', 8.0)]
>>> dict(zip(asignaturas, notas[:3]))
{'Matemáticas': 6.0, 'Física': 3.5, 'Química': 7.5}
~~~~

#### Operar todos los elementos de una colección iterable (*reduce*)
- *reduce(f, l, i)* : Aplicar la función *f* a los dos primeros elementos de la secuencia *l*. Con el valor obtenido vuelve a aplicar la función *f* a ese valor y el siguiente de la secuencia, y así hasta que no quedan más elementos en la lista. Devuelve el valor resultante de la última aplicación.  Si se indica un inicio *i*, emepezará entre el valor *i* y el primer elemento de la lista.
> ⚠️ La función *reduce* está definida en el módulo *functools*.
~~~~ python
>>> from functools import reduce
>>> reduce(lambda x,y : x+y, range(1, 5))
10
>>> reduce(lambda x,y : x*y, range(1, 5), 5)
120
>>> reduce(lambda x,y : x+y, 'Python', 'Java < '))
Java < Python
~~~~

## Comprensión de Colecciones
---
### Comprensión de colecciones
En muchas aplicaciones es habitual aplicar una función o realizar una operación con los elementos de una colección (lista, tupla o diccionario) y obtener una nueva colección de elementos transformados. Aunque esto se puede hacer recorriendo la secuencia con un bucle iterativo, y en programación funcional mediante la función *map*, Python incorpora un mecanismo muy potente que permite esto mismo de manera más simple.

#### Comprensión de listas
~~~~ python
[expresion for variable in lista if condicion]
~~~~

Esta instrucción genera la lista cuyos elementos son el resultado de evaluar la expresión *expresion*, para cada valor que toma la variable *variable*, donde variable toma todos los valores de la lista *lista* que cumplen la condición *condición*.
~~~~ python
>>> [x ** 2 for x in range(10)]
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> [x for x in range(10) if x % 2 == 0]
[0, 2, 4, 6, 8]
>>> [x ** 2 for x in range(10) if x % 2 == 0]
[0, 4, 16, 36, 64]
>>> notas = {'Carmen':5, 'Antonio':4, 'Juan':8, 'Mónica':9, 'María': 6, 'Pablo':3}
>>> [nombre for (nombre, nota) in notas.items() if nota >= 5]
['Carmen', 'Juan', 'Mónica', 'María']
~~~~

#### Comprensión de diccionarios
~~~~ python
{expresion-clave:expresion-valor for variables in lista if condicion}
~~~~

Esta instrucción genera el diccionario formado por los pares cuyas claves son el resultado de evaluar la expresión *expresion-clave* y cuyos valores son el resultado de evaluar la expresión *expresion-valor*, para cada valor que toma la variable *variable*, donde variable toma todos los valores de la lista *lista* que cumplen la condición *condición*.
~~~~ python
>>> {palabra:len(palabra) for palabra in ['I', 'love', 'Python']}
{'I': 1, 'love': 4, 'Python': 6}
>>> notas = {'Carmen':5, 'Antonio':4, 'Juan':8, 'Mónica':9, 'María': 6, 'Pablo':3}
>>> {nombre: nota+1 for (nombre, nota) in notas.items() if nota >= 5])
{'Carmen': 6, 'Juan': 9, 'Mónica': 10, 'María': 7}
~~~~

## Ficheros
---
### Ficheros
Hasta ahora hemos visto como interactuar con un programa a través del teclado (entrada de datos) y la terminal (salida), pero en la mayor parte de las aplicaciones reales tendremos que leer y escribir datos en ficheros.

Al utilizar ficheros para guardar los datos estos perdurarán tras la ejecución del programa, pudiendo ser consultados o utilizados más tarde.

Las operaciones más habituales con ficheros son:
- Crear un fichero.
- Escribir datos en un fichero.
- Leer datos de un fichero.
- Borrar un fichero.

#### Creación y escritura de ficheros
Para crear un fichero nuevo se utiliza la siguiente función:

- *open(ruta, 'w')* : Crea el fichero con la ruta *ruta*, lo abre en modo escritura (el argumento *‘w’* significa *write*) y devuelve un objeto que lo referencia.
> ⚠️ Si el fichero indicado por la ruta ya existe en el sistema, se reemplazará por el nuevo.

Una vez creado el fichero, para escribir datos en él se utiliza el siguiente método:
- *f.write(c)* : Escribe la cadena *c* en el fichero referenciado por *f* y devuelve el número de caracteres escritos.
~~~~ python
>>> f = open('saludo.txt', 'w')
>>> f.write('¡Bienvenido a Python!')
21
~~~~

#### Añadir datos a un fichero
Si en lugar de crear un fichero nuevo queremos añadir datos a un fichero existente se debe utilizar la siguiente función:

- *open(ruta, 'a')* : Abre el fichero con la ruta *ruta* en modo añadir (el argumento *‘a’* significa *append*) y devuelve un objeto que lo referencia.

Una vez abierto el fichero, se utiliza el método de escritura anterior y los datos se añaden al final del fichero.
~~~~ python
>>> f = open('saludo.txt', 'a')
>>> f.write('\n¡Hasta pronto!')
15
~~~~

#### Leer datos de un fichero
Para abrir un fichero en modo lectura se utiliza la siguiente función:

- *open(ruta, 'r')* : Abre el fichero con la ruta *ruta* en modo lectura (el argumento *‘r’* significa *read*) y devuelve un objeto que lo referencia.

Una vez abierto el fichero, se puede leer todo el contenido del fichero o se puede leer línea a línea. Para ello se utilizan las siguientes funciones:

- *f.read()* : Devuelve todos los datos contenidos en el fichero referenciado por *f* como una cadena de caracteres.

- *f.readlines()* : Devuelve una lista de cadenas de caracteres donde cada cadena es una linea del fichero referenciado por *f*.
~~~~ python
>>> f = open('saludo.txt', 'r')
>>> print(f.read())
¡Bienvenido a Python!
¡Hasta pronto!
~~~~
~~~~ python
>>> f = open('saludo.txt', 'r')
>>> lineas = f.readlines()
>>> print(lineas)
['Bienvenido a Python!\n', '¡Hasta pronto!']
~~~~

#### Cerrar un fichero
Para cerrar un fichero se utiliza el siguiente método:

- *f.close()* : Cierra el fichero referenciado por el objeto *f*.

Cuando se termina de trabajar con un fichero conviene cerrarlo, sobre todo si se abre en modo escritura, ya que mientras está abierto en este modo no se puede abrir por otra aplicación. Si no se cierra explícitamente un fichero, Python intentará cerrarlo cuando estime que ya no se va a usar más.
~~~~ python
>>> f = open('saludo.txt'):
>>> print(f.read())
¡Bienvenido a Python!
¡Hasta pronto!
>>> f.close()  # Cierre del fichero
>>> print(f.read())  # Produce un error
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: I/O operation on closed file.
~~~~

#### La estructura *with open(...) as*
Para despreocuparnos del cierre de un fichero cuando ya no es necesario y no tener que cerrarlo explícitamente, se utiliza la siguiente estructura:
~~~~ python
with open(ruta, modo) as f:
    bloque código
~~~~

Esta estructura abre el fichero con la ruta *ruta* en el modo *modo* (*'w'* para escribir, *'a'* para añadir y *'r'* para leer) y devuelve una referencia al mismo en la variable *f*. El fichero permanece abierto mientras se ejecuta el bloque de código asociado y se cierra automáticamente cuando termina la ejecución del bloque.
~~~~ python
>>> with open('saludo.txt', 'w') as f:
...     f.write("Hola de nuevo")
... 
13
>>> with open('saludo.txt', 'r') as f:
...     print(f.read())
... 
Hola de nuevo
>>> print(f.read())  # Produce un error al estar el fichero cerrado
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: I/O operation on closed file.
~~~~

#### Renombrado y borrado de un fichero
Para renombra o borrar un fichero se utilizan funciones del módulo *os*.

- *os.rename(ruta1, ruta2)* : Renombra y mueve el fichero de la ruta *ruta1* a la ruta *ruta2*.
- *os.remove(ruta)* : Borra el fichero de la ruta *ruta*.

Antes de borrar o renombra un directorio conviene comprobar que existe para que no se produzca un error. Para ello se utiliza la función
- *os.path.isfile(ruta)* : Devuelve *\<True>* si existe un fichero en la ruta ruta y *\<False>* en caso contrario.

~~~~ python
>>> import os
>>> f = 'saludo.txt'
>>> if os.path.isfile(f):
...     os.rename(f, 'bienvenida.txt') # renombrado
... else:
...     print('¡El fichero', f, 'no existe!')
...
>>> f = 'bienvenida.txt'
>>> if os.path.isfile(f):
...     os.remove(f) # borrado
... else:
...     print('¡El fichero', f, 'no existe!')
...
~~~~

#### Creación, cambio y eliminación de directorios
Para trabajar con directorios también se utilizan funciones del módulo *os*.
- *os.listdir(ruta)* : Devuelve una lista con los ficheros y directiorios contenidos en la ruta *ruta*.
- *os.mkdir(ruta)* : Crea un nuevo directorio en la ruta *ruta*.
- *os.chdir(ruta)* : Cambia el directorio actual al indicado por la ruta *ruta*.
- *os.getcwd()* : Devuelve una cadena con la ruta del directorio actual.
- *os.rmdir(ruta)* : Borra el directorio de la ruta *ruta*, siempre y cuando esté vacío.

#### Leer un fichero de internet
Para leer un fichero de internet hay que utilizar la función *urlopen* del módulo *urllib.request*.
- *urlopen(url)* : Abre el fichero con la *url* especificada y devuelve un objeto del tipo fichero al que se puede acceder con los métodos de lectura de ficheros anteriores.
~~~~ python
>>> from urllib import request
>>> f = request.urlopen('https://raw.githubusercontent.com/asalber/asalber.github.io/master/README.md')
>>> datos = f.read()
>>> print(datos.decode('utf-8'))
Manuales de Yeibi
===============

Este es el repositorio de manuales de Yeibi: https://github.com/yeibi-aholic
~~~~

## Excepciones
---
### Control de errores mediante excepciones
Python utiliza un objeto especial llamado **excepción** para controlar cualquier error que pueda ocurrir durante la ejecución de un programa.

Cuando ocurre un error durante la ejecución de un programa, Python crea una excepción. Si no se controla esta excepción la ejecución del programa se detiene y se muestra el error (*traceback*).
~~~~ python
>>> print(1 / 0)  # Error al intentar dividir por 0.
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: division by zero
~~~~

#### Tipos de excepciones
Los principales excepciones definidas en Python son:
- *TypeError* : Ocurre cuando se aplica una operación o función a un dato del tipo inapropiado.
- *ZeroDivisionError* : Ocurre cuando se itenta dividir por cero.
- *OverflowError* : Ocurre cuando un cálculo excede el límite para un tipo de dato numérico.
- *IndexError* : Ocurre cuando se intenta acceder a una secuencia con un índice que no existe.
- *KeyError* : Ocurre cuando se intenta acceder a un diccionario con una clave que no existe.
- *FileNotFoundError* : Ocurre cuando se intenta acceder a un fichero que no existe en la ruta indicada.
- *ImportError* : Ocurre cuando falla la importación de un módulo.

Consultar la documentación de Python para ver la [lista de exepciones predefinidas](https://docs.python.org/3/library/exceptions.html).

#### Control de excepciones
Para evitar la interrución de la ejecución del programa cuando se produce un error, es posible controlar la exepción que se genera con la siguiente instrucción:
~~~~ python
try:
     bloque código 1
except excepción:
     bloque código 2
else:
     bloque código 3
~~~~

Esta instrucción ejecuta el primer bloque de código y si se produce un error que genera una excepción del tipo *excepción* entonces ejecuta el segundo bloque de código, mientras que si no se produce ningún error, se ejecuta el tercer bloque de código.

~~~~ python
>>> def division(a, b):
...     try:
...         result = a / b
...     except ZeroDivisionError:
...         print('¡No se puede dividir por cero!')
...     else:
...         print(result)
...
>>> division(1, 0)
¡No se puede dividir por cero!
>>> division(1, 2)
0.5
~~~~
~~~~ python
>>> try:
...     f = open('fichero.txt')  # El fichero no existe
... except FileNotFoundError:
...     print('¡El fichero no existe!')
... else:
...     print(f.read())
¡El fichero no existe!
~~~~

#### Generación manual de excepciones
También se pueden generar manualmente excepciones específicas con la declaración *raise* dentro de una condición. El error de salida puede ser tanto uno predefinido por Python como uno totalmente nuevo.
~~~~ python
if <condicion>:
    raise NombreError ("Definición")
~~~~

Si se combina con *except* se puede renombrar un error ya predefinido con nuestro propio nombre y mensaje.
~~~~ python
try:
    bloque código 1
except exception as NombreError:
    print(NombreError)
~~~~

~~~~ python
>>> import math
...
>>> def CalcularRaiz(n):
...     if n < 0:
...         raise ValueError("El número no puede ser negativo")
...     else:
...         return math.sqrt(n)
...
>>> try:
...     print(CalcularRaiz(-1))
... except ValueError as ErrorNumeroNegativo:
...     print(ErrorNumeroNegativo)
El número no puede ser negativo
~~~~

## Programación Orientada a Objetos
---
### Objetos
Python también permite la *programación orientada a objetos*, que es un paradigma de programación en la que los datos y las operaciones que pueden realizarse con esos datos se agrupan en unidades lógicas llamadas **objetos**.

Los objetos suelen representar conceptos del dominio del programa, como un estudiante, un coche, un teléfono, etc. Los datos que describen las características del objeto se llaman **atributos** y son la parte estática del objeto, mientras que las operaciones que puede realizar el objeto se llaman **métodos** y son la parte dinámica del objeto.

La programación orientada a objetos permite simplificar la estructura y la lógica de los grandes programas en los que intervienen muchos objetos que interactúan entre si.

> **Ejemplo.** Una tarjeta de crédito puede representarse como un objeto:
> - **Atributos** => Número de la tarjeta, titular, balance, fecha de caducidad, pin, entidad emisora, estado (activa o no), etc.
> - **Métodos** => Activar, pagar, renovar, anular.

![](Fotos/Manual_Python/Programacion_Orientada_Objetos/Ejemplo.PNG)

#### Acceso a los atributos y métodos de un objeto
- *dir(objeto)* : Devuelve una lista con los nombres de los atributos y métodos del objeto *objeto*.

Para ver si un objeto tiene un determinado atributo o método se utiliza la siguiente función:

- *hasattr(objeto, elemento)* : Devuelve *\<True>* si *elemento* es un atributo o un método del objeto *objeto* y *\<False>* en caso contrario.

Para acceder a los atributos y métodos de un objeto se pone el nombre del objeto seguido del operador punto y el nombre del atributo o el método.
- *objeto.atributo* : Accede al atributo *atributo* del objeto *objeto*.
- *objeto.método(parámetros)* : Ejecuta el método *método* del objeto *objeto* con los parámetros que se le pasen.

En Python los tipos de datos primitivos son también objetos que tienen asociados atributos y métodos.

> **Ejemplo.** Las cadenas tienen un método *upper* que convierte la cadena en mayúsculas. Para aplicar este método a la cadena *c* se utiliza la instrucción *c.upper()*.
~~~~ python
>>> c = 'Python'
>>> print(c.upper())    # Llamada al método upper del objeto c (cadena)
PYTHON
~~~~
> **Ejemplo.** Las listas tienen un método *append* que convierte añade un elemento al final de la lista. Para aplicar este método a la lista *l* se utiliza la instrucción *l.append(<elemento>)*.
~~~~ python
>>> l =  [1, 2, 3]     
>>> l.append(4)         # Llamada al método append del objeto l (lista)
>>> print(l)
[1, 2, 3, 4]
~~~~

### Clases (*class*)
Los objetos con los mismos atributos y métodos se agrupan **clases**. Las clases definen los atributos y los métodos, y por tanto, la semántica o comportamiento que tienen los objetos que pertenecen a esa clase. Se puede pensar en una clase como en un *molde* a partir del cuál se pueden crear objetos.

Para declarar una clase se utiliza la palabra clave *class* seguida del nombre de la clase y dos puntos, de acuerdo a la siguiente sintaxis:
~~~~ python
class <nombre-clase>:
     <atributos>
     <métodos>
~~~~

Los atributos se definen igual que las variables mientras que los métodos se definen igual que las funciones. Tanto unos como otros tienen que estar indentados por 4 espacios en el cuerpo de la clase.

> **Ejemplo.** El siguiente código define la clase *Saludo* sin atributos ni métodos. La palabra reservada *pass* indica que la clase está vacía.
~~~~ python
>>> class Saludo:
...     pass        # Clase vacía sin atributos ni métodos.
>>> print(Saludo)
<class '__main__.Saludo'>
~~~~
 > ⚠️ Es una buena práctica comenzar el nombre de una clase con mayúsculas.

#### Clases primitivas
En Python existen clases predefinidas para los tipos de datos primitivos:
- *int* : Clase de los números enteros.
- *float* : Clase de los números reales.
- *str* : Clase de las cadenas de caracteres.
- *list* : Clase de las listas.
- *tuple* : Clase de las tuplas.
- *dict* : Clase de los diccionarios.
~~~~ python
>>> type(1)
<class 'int'>
>>> type(1.5)
<class 'float'>
>>> type('Python')
<class 'str'>
>>> type([1,2,3])
<class 'list'>
>>> type((1,2,3))
<class 'tuple'>
>>> type({1:'A', 2:'B'})
<class 'dict'>
~~~~

#### Instanciación de clases
Para crear un objeto de una determinada clase se utiliza el nombre de la clase seguida de los parámetros necesarios para crear el objeto entre paréntesis.
- *clase(parámetros)* : Crea un objeto de la clase *clase* inicializado con los *parámetros* dados.

Cuando se crea un objeto de una clase se dice que el objeto es una instancia de la clase.
~~~~ python
>>> class Saludo:
...     pass        # Clase vacía sin atributos ni métodos.
>>> s = Saludo()    # Creación del objeto mediante instanciación de la clase.
>>> s
<__main__.Saludo object at 0x7fcfc7756be0>      # Dirección de memoria donde se crea el objeto
>>> type(s)
<class '__main__.Saludo'>     # Clase del objeto
~~~~

#### Definición de métodos
Los métodos de una clase son las funciones que definen el comportamiento de los objetos de esa clase.

Se definen como las funciones con la palabra reservada *def*. La única diferencia es que su primer parámetro es especial y se denomina *self*. Este parámetro hace siempre referencia al objeto desde donde se llama el método, de manera que para acceder a los atributos o métodos de una clase en su propia definición se puede utilizar la sintaxis *self.atributo* o *self.método*.
~~~~ python
>>> class Saludo:
...     mensaje = "Bienvenido "            # Definición de un atributo
...     def saludar(self, nombre):         # Definición de un método   
...         print(self.mensaje + nombre)
...         return
... 
>>> s = Saludo()
>>> s.saludar('Yeibi')
Bienvenido Yeibi
~~~~

La razón por la que existe el parámetro *self* es porque Python traduce la llamada a un método de un objeto *objeto.método(parámetros)* en la llamada *clase.método(objeto, parámetros)*, es decir, se llama al método definido en la clase del objeto, pasando como primer argumento el propio objeto, que se asocia al parámetro *self*.

#### El método *\_\_init__*
En la definición de una clase suele haber un método llamado *\_\_init__* que se conoce como inicializador. Este método es un método especial que se llama cada vez que se instancia una clase y sirve para inicializar el objeto que se crea. Este método crea los atributos que deben tener todos los objetos de la clase y por tanto contiene los parámetros necesarios para su creación, pero no devuelve nada. Se invoca cada vez que se instancia un objeto de esa clase.
~~~~ python
>>> class Tarjeta:
...     def __init__(self, id, cantidad = 0):    # Inicializador
            self.id = id                         # Creación del atributo id  
...         self.saldo = cantidad                # Creación del atributo saldo
...         return
...     def mostrar_saldo(self):
...         print('El saldo es', self.saldo, '€')
...         return
>>> t = Tarjeta('1111111111', 1000)     # Creación de un objeto con argumentos             
>>> t.mostrar_saldo()
El saldo es 1000 €
~~~~

#### Atributos de instancia vs atributos de clase
Los atributos que se crean dentro del método *\_\_init__* se conocen como atributos del objeto, mientras que los que se crean fuera de él se conocen como atributos de la clase. Mientras que los primeros son propios de cada objeto y por tanto pueden tomar valores distintos, los valores de los atributos de la clase son los mismos para cualquier objeto de la clase.
> ⚠️ En general, no deben usarse atributos de clase, excepto para almacenar valores constantes.
~~~~ python
>>> class Circulo:
...     pi = 3.14159                     # Atributo de clase
...     def __init__(self, radio):
...         self.radio = radio           # Atributo de instancia
...     def area(self):
...         return Circulo.pi * self.radio ** 2
... 
>>> c1 = Circulo(2)
>>> c2 = Circulo(3)
>>> print(c1.area())
12.56636
>>> print(c2.area())
28.27431
>>> print(c1.pi)
3.14159
>>> print(c2.pi)
3.14159
~~~~

#### El método *\_\_str__*
Otro método especial es el método llamado *\_\_str__* que se invoca cada vez que se llama a las funciones *print* o *str*. Devuelve siempre una cadena que se suele utilizar para dar una descripción informal del objeto. Si no se define en la clase, cada vez que se llama a estas funciones con un objeto de la clase, se muestra por defecto la posición de memoria del objeto.
~~~~ python
>>> class Tarjeta:
...     def __init__(self, numero, cantidad = 0):
...         self.numero = numero
...         self.saldo = cantidad
...         return
...     def __str__(self):
...         return 'Tarjeta número {} con saldo {:.2f}€'.format(self.numero, str(self.saldo))
>>> t = Tarjeta('0123456789', 1000) 
>>> print(t)
Tarjeta número 0123456789 con saldo 1000.00€
~~~~

### Herencia
Una de las características más potentes de la programación orientada a objetos es la herencia, que permite definir una especialización de una clase añadiendo nuevos atributos o métodos. La nueva clase se conoce como *clase hija* y hereda los atributos y métodos de la clase original que se conoce como *clase madre*.

Para crear un clase a partir de otra existente se utiliza la misma sintaxis que para definir una clase, pero poniendo detrás del nombre de la clase entre paréntesis los nombres de las clases madre de las que hereda.

> **Ejemplo.** A partir de la clase *Tarjeta* definida antes podemos crear mediante herencia otra clase *Tarjeta_Descuento* para representar las tarjetas de crédito que aplican un descuento sobre las compras.
~~~~ python
>>> class Tarjeta:
...     def __init__(self, id, cantidad = 0):
...         self.id = id
...         self.saldo = cantidad
...         return
...     def mostrar_saldo(self):       # Método de la clase Tarjeta que hereda la clase Tarjeta_descuento
...         print('El saldo es ', self.saldo, '€.')
...         return
... 
>>> class Tarjeta_descuento(Tarjeta):
...     def __init__(self, id, descuento, cantidad = 0):
...         self.id = id
...         self.descuento = descuento
...         self.saldo = cantidad
...         return
...     def mostrar_descuento(self):   # Método exclusivo de la clase Tarjeta_descuento
...         print('Descuento de ', self.descuento, '% en los pagos.')
...         return
... 
>>> t = Tarjeta_descuento('0123456789', 2, 1000)
>>> t.mostrar_saldo()
El saldo es 1000€.
>>> t.mostrar_descuento()
Descuento de 2% en los pagos.
~~~~

La principal ventaja de la herencia es que evita la repetición de código y por tanto los programas son más fáciles de mantener.

En el ejemplo de la tarjeta de crédito, el método *mostrar_saldo* solo se define en la clase madre. De esta manera, cualquier cambio que se haga en el cuerpo del método en la clase madre, automáticamente se propaga a las clases hijas. Sin la herencia, este método tendría que replicarse en cada una de las clases hijas y cada vez que se hiciese un cambio en él, habría que replicarlo también en las clases hijas.

#### Jerarquía de clases
A partir de una clase derivada mediante herencia se pueden crear nuevas clases hijas aplicando de nuevo la herencia. Ello da lugar a una jerarquía de clases que puede representarse como un árbol donde cada clase hija se representa como una rama que sale de la clase madre.

![](Fotos/Manual_Python/Programacion_Orientada_Objetos/JerarquiaClases.PNG)

Debido a la herencia, cualquier objeto creado a partir de una clase es una instancia de la clase, pero también lo es de las clases que son ancestros de esa clase en la jerarquía de clases.

El siguiente comando permite averiguar si un objeto es instancia de una clase:
- *isinstance(objeto, clase)* : Devuelve *\<True>* si el objeto *objeto* es una instancia de la clase *clase* y *\<False>* en caso contrario.
~~~~ python
# Asumiendo la definición de las clases Tarjeta y Tarjeta_descuento anteriores.
>>> t1 = Tarjeta('1111111111', 0)
>>> t2 = t = Tarjeta_descuento('2222222222', 2, 1000)
>>> isinstance(t1, Tarjeta)
True
>>> isinstance(t1, Tarjeta_descuento)
False
>>> isinstance(t2, Tarjeta_descuento)
True
>>> isinstance(t2, Tarjeta)
True
~~~~

#### Sobrecarga y polimorfismo
Los objetos de una clase hija heredan los atributos y métodos de la clase madre y, por tanto, a priori tienen tienen el mismo comportamiento que los objetos de la clase madre. Pero la clase hija puede definir nuevos atributos o métodos o reescribir los métodos de la clase madre de manera que sus objetos presenten un comportamiento distinto. Esto último se conoce como **sobrecarga**.

De este modo, aunque un objeto de la clase hija y otro de la clase madre pueden tener un mismo método, al invocar ese método sobre el objeto de la clase hija, el comportamiento puede ser distinto a cuando se invoca ese mismo método sobre el objeto de la clase madre. Esto se conoce como **polimorfismo** y es otra de las características de la programación orientada a objetos.
~~~~ python
>>> class Tarjeta:
...     def __init__(self, id, cantidad = 0):
...         self.id = id
...         self.saldo = cantidad
...         return
...     def mostrar_saldo(self):
...         print('El saldo es {:.2f}€.'.format(self.saldo))
...         return
...     def pagar(self, cantidad):
...         self.saldo -= cantidad
...         return
>>> class Tarjeta_Oro(Tarjeta):
...     def __init__(self, id, descuento, cantidad = 0):
...         self.id = id
...         self.descuento = descuento
...         self.saldo = cantidad
...         return
...     def pagar(self, cantidad):
...         self.saldo -= cantidad * (1 - self.descuento / 1...00)
>>> t1 = Tarjeta('1111111111', 1000)
>>> t2 = Tarjeta_Oro('2222222222', 1, 1000)
>>> t1.pagar(100)
>>> t1.mostrar_saldo()
El saldo es 900.00€.
>>> t2.pagar(100)
>>> t2.mostrar_saldo()
El saldo es 901.00€.
~~~~

### Principios de la programación orientada a objetos
La programación orientada a objetos se basa en los siguientes principios:

- **Encapsulación** : Agrupar datos (atributos) y procedimientos (métodos) en unidades lógicas (objetos) y evitar maninupar los atributos accediendo directamente a ellos, usando, en su lugar, métodos para acceder a ellos.
- **Abstracción** : Ocultar al usuario de la clase los detalles de implementación de los métodos. Es decir, el usuario necesita saber *qué* hace un método y con qué parámetros tiene que invocarlo (*interfaz*), pero no necesita saber *cómo* lo hace.
- **Herencia** : Evitar la duplicación de código en clases con comportamientos similares, definiendo los métodos comunes en una clase madre y los métodos particulares en clases hijas.
- **Polimorfismo** : Redefinir los métodos de la clase madre en las clases hijas cuando se requiera un comportamiento distinto. Así, un mismo método puede realizar operaciones distintas dependiendo del objeto sobre el que se aplique.

Resolver un problema siguiendo el paradigma de la programación orientada a objetos requiere un cambio de mentalidad con respecto a como se resuelve utilizando el paradigma de la programación procedimental.

La programación orientada a objetos es más un proceso de modelado, donde se identifican las entidades que intervienen en el problema y su comportamiento, y se definen clases que modelizan esas entidades. Por ejemplo, las entidades que intervienen en el pago con una tarjeta de crédito serían la tarjeta, el terminal de venta, la cuenta corriente vinculada a la tarjeta, el banco, etc. Cada una de ellas daría lugar a una clase.

Después se crean objetos con los datos concretos del problema y se hace que los objetos interactúen entre sí, a través de sus métodos, para resolver el problema. Cada objeto es responsable de una subtarea y colaboran entre ellos para resolver la tarea principal. Por ejemplo, la terminal de venta accede a los datos de la tarjeta y da la orden al banco para que haga un cargo en la cuenta vinculada a la tarjeta.

De esta forma se pueden abordar problemas muy complejos descomponiéndolos en pequeñas tareas que son más fáciles de resolver que el problema principal (*¡divide y vencerás!*).

### Documentación de clases
Al igual que las funciones, se puede definir una descripción de ayuda.
~~~~ python
>>> class Mates:
...     """ Esta clase calcula las operaciones básicas matemáticas."""
...     
...     def suma(a, b):
...         """ Función que calcula la suma de dos números."""
...         return a+b
...
...     def resta(a, b):
...         """ Función que calcula la resta de dos números."""
...         return a-b
...
...     def multi(a, b):
...         """ Función que calcula la multiplicación de dos números."""
...         return a*b
...
...     def divi(a, b):
...         """ Función que calcula la división entre dos números."""
...         return a/b
...
>>> help(Mates)
Help on class Mates in module __main__:

class Mates(builtins.object)
 |  Esta clase calcula las operaciones básicas matemáticas.
 |
 |  Methods defined here:
 |
 |  divi(a, b)
 |      Función que calcula la división entre dos números.
 |
 |  multi(a, b)
 |      Función que calcula la multiplicación de dos números.
 |
 |  resta(a, b)
 |      Función que calcula la resta de dos números.
 |
 |  suma(a, b)
 |      Función que calcula la suma de dos números.
 |
 |  ----------------------------------------------------------------------
 |  Data descriptors defined here:
 |
 |  __dict__
 |      dictionary for instance variables (if defined)
 |
 |  __weakref__
 |      list of weak references to the object (if defined)
~~~~

## Módulos
---
### Módulos
El código de un programa en Python puede reutilizarse en otro importándolo. Cualquier fichero con código de Python reutilizable se conoce como *módulo* o *librería*.

Los módulos suelen contener objetos (funciones, clases, excepciones, etc) reutilizables, pero también pueden definir variables con datos simples o compuestos (listas, diccionarios, etc), o cualquier otro código válido en Python.

Python permite importar un módulo completo o sólo algunas partes de él. Cuando se importa un módulo completo, el intérprete de Python ejecuta todo el código que contiene el módulo, mientras que si solo se importan algunas partes del módulo, solo se ejecutarán esas partes.

#### Importación completa de módulos (*import*)
- *import M* : Ejecuta el código que contiene *M* y crea una referencia a él, de manera que pueden invocarse un objeto o función *f* definida en él mediante la sintaxis *M.f*.
- *import M as N* : Ejecuta el código que contiene *M* y crea una referencia a él con el nombre *N*, de manera que pueden invocarse un objeto o función *f* definida en él mediante la sintaxis *N.f*. Esta forma es similar a la anterior, pero se suele usar cuando el nombre del módulo es muy largo para utilizar un alias más corto.

#### Importación parcial de módulos (*from import*)
- *from M import f, g, ...* : Ejecuta el código que contiene *M* y crea referencias a los objetos *f, g, ...*, de manera que pueden ser invocados por su nombre. De esta manera para invocar cualquiera de estos objetos no hace falta precederlos por el nombre del módulo, basta con escribir su nombre.
- *from M import \** : Ejecuta el código que contiene *M* y crea referencias a todos los objetos públicos (aquellos que no empiezan por el carácter *_*) definidos en el módulo, de manera que pueden ser invocados por su nombre.

> ⚠️ Cuando se importen módulos de esta manera hay que tener cuidado de que no haya coincidencias en los nombres de funciones, variables u otros objetos.
~~~~ python
>>> import calendar
>>> print(calendar.month(2019, 4))
April 2019
Mo Tu We Th Fr Sa Su
 1  2  3  4  5  6  7
 8  9 10 11 12 13 14
15 16 17 18 19 20 21
22 23 24 25 26 27 28
29 30
~~~~
~~~~ python
>>> from math import *
>>> cos(pi)
-1.0
~~~~

> ⚠️ Por defecto, el módulo que queremos utilizar debe estar en la misma dirección que el programa en el que queremos emplear el código o en la *sys.path*, un conjunto de directorios predeterminado en Python.
~~~~ python
>>> import sys
# imprimir todos los directorios
>>> sys.path
['C:\\Users\\usuario\\source\\repos\\Python', 
 'C:\\Users\\usuario\\AppData\\Local\\Programs\\Python\\Python36-32\\python36.zip', 
 'C:\\Users\\usuario\\AppData\\Local\\Programs\\Python\\Python36-32\\DLLs', 
 'C:\\Users\\usuario\\AppData\\Local\\Programs\\Python\\Python36-32\\lib', 
 'C:\\Users\\usuario\\AppData\\Local\\Programs\\Python\\Python36-32', 
 'C:\\Users\\usuario\\AppData\\Local\\Programs\\Python\\Python36-32\\lib\\site-packages']
~~~~

#### Módulos de la librería estándar más importantes
Python viene con una [biblioteca de módulos predefinidos](https://docs.python.org/3/py-modindex.html) que no necesitan instalarse. Algunos de los más utilizados son:
- *[sys](https://docs.python.org/3/library/sys.html)* : Funciones y parámetros específicos del sistema operativo.
- *[os](https://docs.python.org/3/library/os.html)* : Interfaz con el sistema operativo.
- *[os.path](https://docs.python.org/3/library/os.path.html)* : Funciones de acceso a las rutas del sistema.
- *[io](https://docs.python.org/3/library/io.html)* : Funciones para manejo de flujos de datos y ficheros.
- *[string](https://docs.python.org/3/library/string.html)* : Funciones con cadenas de caracteres.
- *[datetime](https://docs.python.org/3/library/datetime.html)* : Funciones para fechas y tiempos.
- *[math](https://docs.python.org/3/library/math.html)* : Funciones y constantes matemáticas.
- *[statistics](https://docs.python.org/3/library/statistics.html)* : Funciones estadísticas.
- *[random](https://docs.python.org/3/library/random.html)* : Generación de números pseudo-aleatorios.

#### Otras librerías imprescindibles
Estas librerías no vienen en la distribución estándar de Python y necesitan instalarse. También puede optarse por la distribución [Anaconda](https://www.anaconda.com/) que incorpora la mayoría de estas librerías.
- *[NumPy](https://www.numpy.org/)* : Funciones matemáticas avanzadas y arrays.
- *[SciPy](https://www.scipy.org/)* : Más funciones matemáticas para aplicaciones científicas.
- *[matplotlib](https://matplotlib.org/)* : Análisis y representación gráfica de datos.
- *[Pandas](https://pandas.pydata.org/)* : Funciones para el manejo y análisis de estructuras de datos.
- *[Request](http://www.python-requests.org/en/master/)* : Acceso a internet por http.

### Paquetes
Los módulos se pueden agrupar bajo una misma carpeta para que funcionen como una librería instalable de Python.

Para crear un paquete se debe crear un fichero especial *\_\_init__.py* vacío en el directorio donde pongamos todos los módulos que se quieren agrupar. 
De esta forma, cuando Python recorra tal directorio será capaz de interpretar una jerarquía de módulos.
~~~~ python
paquete/
    __init__.py
    modulo1.py
    modulo2.py
~~~~

Esta jerarquía se puede expandir tanto como se quiera creando subpaquetes, pero siempre añadiendo el fichero *\_\_init__.py* en cada uno de ellos.
~~~~ python
paquete/
    __init__.py
    subpaquete1/
        __init__.py
        modulo11.py
        modulo12.py
    subpaquete2/
        __init__.py
        modulo21.py
        modulo22.py
    subpaquete3/
        __init__.py
        modulo31.py
        modulo32.py
~~~~

> ⚠️ Pasa lo mismo con la ruta de los paquetes que pasa con los mósulos.

#### Importación de modulos
- *import P.M* : Ejecuta el código que contiene *M* en la ruta de carpetas *P* y crea una referencia a él, de manera que pueden invocarse un objeto o función *f* definida en él mediante la sintaxis *P.M.f*.
- *from P import M* : Ejecuta el código que contiene *M* en la ruta de carpetas *P* y crea una referencia a él, de manera que pueden invocarse un objeto o función *f* definida en él mediante la sintaxis *M.f*.
- *from P.M import f, g, ...* : Ejecuta el código que contiene *M* en la ruta de carpetas *P* y crea referencias a los objetos *f, g, ...*, de manera que pueden ser invocados por su nombre. De esta manera para invocar cualquiera de estos objetos no hace falta precederlos por el nombre del módulo, basta con escribir su nombre.

### Paquetes distribuibles
Los paquetes pueden ser distribuibles para poder instalarlos en Python sin la necesidad de tener el paquete y el programa en el que queremos emplear el código en la misma ruta.

Para crear un paquete distribuible tenemos que crear un fichero *setup.py* fuera de la raíz.
~~~~ python
setup.py
paquete/
    __init__.py
    subpaquete1/
        __init__.py
        modulo11.py
        modulo12.py
    subpaquete2/
        __init__.py
        modulo21.py
        modulo22.py
    subpaquete3/
        __init__.py
        modulo31.py
        modulo32.py
~~~~

Dentro del fichero hay que definir el distribuible con su información básica, incluyendo los paquetes y subpaquetes que lo forman, así como los posibles scripts.
~~~~ python
from setuptools import setup
setup(
    name="paquete",
    version="1.0",
    description="instalación de subpaquetes",
    author="usuario",
    author_email="usuario@mail.com",
    url="http://www.web.net",
    packages=['paquete','paquete.subpaquete1','paquete.subpaquete2','paquete.subpaquete3']
    scripts=[]
)
~~~~

Con *<Administrador: Símbolo del sistema>* o *<Windows: PowerShell>* nos posicionamos en la dirección del fichero *setup.py*.
~~~~ shell
C:\Users\Usuario> cd ../Python
C:\Users\Usuario\..\Python> python setup.py sdist
~~~~

Tras ejecutar el comando previo, se ha creado una nueva carpeta llamada *dist*. En ella encontraremos un fichero *.zip* en Windows o *.tar.gz* en Linux.
Este fichero es el distribuible y ahora se podría compartir con cualquiera que quiere instalar nuestro paquete.

Para instalar un paquete en Python, y finalmente hacer que se pueda utilizar desde cualquier lugar, desde el directorio donde tenemos el paquete comprimido abrimos de nuevo *<Administrador: Símbolo del sistema>* o *<Windows: PowerShell>* y ejecutamos su instalación.
~~~~ shell
C:\Users\Usuario\..\Python> cd dist
C:\Users\Usuario\..\Python\dist> pip install paquete-1.0.zip
~~~~

Con el comando *pip3 list*, se puede consultar todos los paquetes instalados en nuestro Python. 
Todos los paquetes de la lista se pueden utilizar desde cualquier script, pues se encuentran instalados dentro de Python.
~~~~ shell
C:\Users\Usuario> pip3 list
Package         Version
--------------- --------
cycler          0.11.0
kiwisolver      1.3.1
matplotlib      3.3.4
numpy           1.19.5
pandas          1.1.5
paquete         1.0.0
Pillow          8.4.0
pip             21.3.1
pyparsing       3.0.7
python-dateutil 2.8.2
pytz            2022.2.1
setuptools      28.8.0
six             1.16.0
~~~~

Finalmente, para desinstalar un paquete:
~~~~ shell
C:\Users\Usuario> pip uninstall paquete
..
Proceed (y/n)? y
~~~~

### Documentación de módulos
Al igual que las funciones y módulos, es recomendable describir para que sirve el módulo y sus respectivas funciones. 
~~~~ python
>>> import datetime
>>> help(datetime)
Help on module datetime:

NAME
    datetime - Fast implementation of the datetime type.

MODULE REFERENCE
https://docs.python.org/3.8/library/datetime
    
    The following documentation is automatically generated from the Python
    source files.  It may be incomplete, incorrect or include features that
    are considered implementation detail and may vary between Python
    implementations.  When in doubt, consult the module reference at the
    location listed above.

CLASSES
    builtins.object
        date
            datetime
        time
        timedelta
        tzinfo
            timezone
    
--More--
~~~~

## Librería Datetime
---
Para manejar fechas en Python se suele utilizar la librería *datetime* que incorpora los tipos de datos *date*, *time* y *datetime* para representar fechas y funciones para manejarlas. Algunas de las operaciones más habituales que permite son:

- Acceder a los distintos componentes de una fecha (año, mes, día, hora, minutos, segundos y microsegundos).
- Convertir cadenas con formato de fecha en los tipos *date*, *time* o *datetime*.
- Convertir fechas de los tipos *date*, *time* o *datetime* en cadenas formateadas de acuerdo a diferentes formatos de fechas.
- Hacer aritmética de fechas (sumar o restar fechas).
- Comparar fechas.

### Los tipos de datos date, time y datetime
- *date(año, mes, dia)* : Devuelve un objeto de tipo *date* que representa la fecha con el *año*, *mes* y *dia* indicados.
- *time(hora, minutos, segundos, microsegundos)* : Devuelve un objeto de tipo time que representa un tiempo la *hora*, *minutos*, *segundos* y *microsegundos* indicados.
- *datetime(año, mes, dia, hora, minutos, segundos, microsegundos)* : Devuelve un objeto de tipo *datetime* que representa una fecha y hora con el *año*, *mes*, *dia*, *hora*, *minutos*, *segundos* y *microsegundos* indicados.
~~~~ python
from datetime import date, time, datetime
>>> date(2020, 12, 25)
datetime.date(2020, 12, 25)
>>> time(13,30,5)
datetime.time(13, 30, 5)
>>> datetime(2020, 12, 25, 13, 30, 5)
datetime.datetime(2020, 12, 25, 13, 30, 5)
>>> print(datetime(2020, 12, 25, 13, 30, 5))
2020-12-25 13:30:05
~~~~

### Acceso a los componentes de una fecha
- *date.today()* : Devuelve un objeto del tipo *date* la fecha del sistema en el momento en el que se ejecuta.
- *datetime.now()* : Devuelve un objeto del tipo *datetime* con la fecha y la hora del sistema en el momento exacto en el que se ejecuta.
- *d.year* : Devuelve el año de la fecha *d*, puede ser del tipo *date* o *datetime*.
- *d.month* : Devuelve el mes de la fecha *d*, que puede ser del tipo *date* o *datetime*.
- *d.day* : Devuelve el día de la fecha *d*, que puede ser del tipo *date* o *datetime*.
- *d.weekday()* : Devuelve el día de la semana de la fecha *d*, que puede serpuede ser del tipo *date* o *datetime*.
- *t.hour* : Devuelve las horas del tiempo *t*, que puede ser del tipo *time* o *datetime*.
- *t.minute* : Devuelve los minutos del tiempo *t*, que puede ser del tipo *time* o datetime*.
- *t.second* : Devuelve los segundos del tiempo *t*, que puede ser del tipo *time* o datetime*.
- *t.microsecond* : Devuelve los microsegundos del tiempo *t*, que puede ser del tipo *time* o *datetime*.
~~~~ python
>>> from datetime import date, time, datetime
>>> print(date.today())
2020-04-11
>>> dt = datetime.now()
>>> dt.year
2020
>>> dt.month
4
>>> dt.day
11
>>> dt.hour
22
>>> dt.minute
5
>>> dt.second
45
>>> dt.microsecond
1338
~~~~

### Conversión de fechas en cadenas con diferentes formatos
- *d.strftime(formato)* : Devuelve la cadena que resulta de transformar la fecha *d* con el formato indicado en la cadena *formato*. La cadena *formato* puede contener los siguientes marcadores de posición: 
    + *%Y* (año completo)
    + *%y* (últimos dos dígitos del año)
    + *%m* (mes en número)
    + *%B* (mes en palabra)
    + *%d* (día)
    + *%A* (día de la semana)
    + *%a* (día de la semana abrevidado)
    + *%H* (hora en formato 24 horas)
    + *%I* (hora en formato 12 horas)
    + *%M* (minutos)
    + *%S* (segundos)
    + *%p* (AM o PM)
    + *%C* (fecha y hora completas)
    + *%x* (fecha completa)
    + *%X* (hora completa)
~~~~ python
>>> from datetime import date, time, datetime
>>> d = datetime.now()
>>> print(d.strftime('%d-%m-%Y'))
13-04-2020
>>> print(d.strftime('%A, %d %B, %y'))
Monday, 13 April, 20
>>> print(d.strftime('%H:%M:%S'))
20:55:53
>>> print(d.strftime('%H horas, %M minutos y %S segundos'))
20 horas, 55 minutos y 53 segundos
~~~~

### Conversión de cadenas en fechas
- *strptime(s, formato)* : Devuelve el objeto de tipo *date*, *time* o *datetime* que resulta de convertir la cadena *s* de acuerdo al formato indicado en la cadena *formato*. La cadena *formato* puede contener los siguientes marcadores de posición: 
    + *%Y* (año completo)
    + *%y* (últimos dos dígitos del año)
    + *%m* (mes en número)
    + *%B* (mes en palabra)
    + *%d* (día)
    + *%A* (día de la semana)
    + *%a* (día de la semana abrevidado)
    + *%H* (hora en formato 24 horas)
    + *%I* (hora en formato 12 horas)
    + *%M* (minutos)
    + *%S* (segundos)
    + *%p* (AM o PM)
    + *%C* (fecha y hora completas)
    + *%x* (fecha completa)
    + *%X* (hora completa)
~~~~ python
>>> from datetime import date, time, datetime
>>> datetime.strptime('15/4/2020', '%d/%m/%Y')
datetime.datetime(2020, 4, 15, 0, 0)
>>> datetime.strptime('2020-4-15 20:50:30', '%Y-%m-%d %H:%M:%S')
datetime.datetime(2020, 4, 15, 20, 50, 30)
~~~~

### Aritmética de fechas
Para representar el tiempo transcurrido entre dos fechas se utiliza el tipo *timedelta*.

- *timedelta(dias, segundos, microsegundos)* : Devuelve un objeto del tipo timedelta que representa un intervalo de tiempo con los *dias*, *segundos* y *microsegundos* indicados.
- *d1 - d2* : Devuelve un objeto del tipo *timedelta* que representa el tiempo transcurrido entre las fechas *d1* y *d2* del tipo *datetime*.
- *d + delta* : Devuelve la fecha del tipo *datetime* que resulta de sumar a la fecha *d* el intervalo de tiempo *delta*, donde *delta* es del tipo *timedelta*.
~~~~ python
>>> from datetime import date, time, datetime, timedelta
>>> d1 = datetime(2020, 1, 1)
>>> d1 + timedelta(31, 3600)
datetime.datetime(2020, 2, 1, 1, 0)
>>> datetime.now() - d1
datetime.timedelta(days=132, seconds=1826, microseconds=895590)
~~~~

## Librería Numpy
---
[NumPy](https://www.numpy.org/) es una librería de Python especializada en el cálculo numérico y el análisis de datos, especialmente para un gran volumen de datos.

Incorpora una nueva clase de objetos llamados **arrays** que permite representar colecciones de datos de un mismo tipo en varias dimensiones, y funciones muy eficientes para su manipulación.

La ventaja de Numpy frente a las listas predefinidas en Python es que el procesamiento de los arrays se realiza mucho más rápido (hasta 50 veces más) que las listas, lo cual la hace ideal para el procesamiento de vectores y matrices de grandes dimensiones.

![](Fotos/Manual_Python/Libreria_Numpy/NumpyLogo.PNG)

### La clase de objetos *array*
Un array es una estructura de datos de un mismo tipo organizada en forma de tabla o cuadrícula de distintas dimensiones.

Las dimensiones de un array también se conocen como **ejes**.

![](Fotos/Manual_Python/Libreria_Numpy/Arrays.PNG)

### Para crear un array se utiliza la siguiente función de NumPy
- *np.array(lista)* : Crea un array a partir de la lista o tupla *lista* y devuelve una referencia a él. El número de dimensiones del array dependerá de las listas o tuplas anidadas en *lista*:
    + Para una lista de valores se crea un array de una dimensión, también conocido como **vector**.
    + Para una lista de listas de valores se crea un array de dos dimensiones, también conocido como **matriz**.
    + Para una lista de listas de listas de valores se crea un array de tres dimensiones, también conocido como **cubo**.
    + Y así sucesivamente. No hay límite en el número de dimensiones del array más allá de la memoria disponible en el sistema.

 > ⚠️ Los elementos de la lista o tupla deben ser del mismo tipo.

~~~~ python
>>> # Array de una dimensión
>>> a1 = np.array([1, 2, 3])
>>> print(a1)
[1 2 3]
>>> # Array de dos dimensiones
>>> a2 = np.array([[1, 2, 3], [4, 5, 6]])
>>> print(a2)
[[1 2 3]
 [4 5 6]]
>>> # Array de tres dimensiones
>>> a3 = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])
>>> print(a3)
[[[ 1  2  3]
  [ 4  5  6]]

 [[ 7  8  9]
  [10 11 12]]]
~~~~

Otras funciones útiles que permiten generar arrays son:

- *np.empty(dimensiones)* : Crea y devuelve una referencia a un array vacío con las dimensiones especificadas en la tupla *dimensiones*.
- *np.zeros(dimensiones)* : Crea y devuelve una referencia a un array con las *dimensiones* especificadas en la tupla dimensiones cuyos elementos son todos ceros.
- *np.ones(dimensiones)* : Crea y devuelve una referencia a un array con las *dimensiones* especificadas en la tupla dimensiones cuyos elementos son todos unos.
- *np.full(dimensiones, valor)* : Crea y devuelve una referencia a un array con las *dimensiones* especificadas en la tupla dimensiones cuyos elementos son todos *valor*.
- *np.identity(n)* : Crea y devuelve una referencia a la matriz identidad de dimensión *n*.
- *np.arange(inicio, fin, salto)* : Crea y devuelve una referencia a un array de una dimensión cuyos elementos son la secuencia desde *inicio* hasta *fin* tomando valores cada *salto*.
- *np.linspace(inicio, fin, n)* : Crea y devuelve una referencia a un array de una dimensión cuyos elementos son la secuencia de *n* valores equidistantes desde *inicio* hasta *fin*.
- *np.random.random(dimensiones)* : Crea y devuelve una referencia a un array con las *dimensiones* especificadas en la tupla dimensiones cuyos elementos son aleatorios.
~~~~ python
>>> print(np.zeros(3,2))
[[0. 0. 0.]
 [0. 0. 0.]]
>>> print(np.idendity(3))
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
>>> print(np.arange(1, 10, 2))
[1 3 5 7 9]
>>> print(np.linspace(0, 10, 5))
[ 0.   2.5  5.   7.5 10. ]
~~~~

### Atributos de un array
Existen varios atributos y funciones que describen las características de un array.
- *a.ndim* : Devuelve el número de dimensiones del array *a*.
- *a.shape* : Devuelve una tupla con las dimensiones del array *a*.
- *a.size* : Devuelve el número de elementos del array *a*.
- *a.dtype* : Devuelve el tipo de datos de los elementos del array *a*.

### Acceso a los elementos de un array
Para acceder a los elementos contenidos en un array se usan índices al igual que para acceder a los elementos de una lista, pero indicando los índices de cada dimensión separados por comas.

Al igual que para listas, los índices de cada dimensión comienzan en 0.

También es posible obtener subarrays con el operador dos puntos *:* indicando el índice inicial y el siguiente al final para cada dimensión, de nuevo separados por comas.
~~~~ python
>>> a = np.array([[1, 2, 3], [4, 5, 6]])
>>> print(a[1, 0])  # Acceso al elemento de la fila 1 columna 0
4
>>> print(a[1][0])  # Otra forma de acceder al mismo elemento
4
>>> print(a[:, 0:2])  # Declaración de subarrays desde la primera columna hasta la segunda
[[1 2]
 [4 5]]
 ~~~~

 ### Filtrado de elementos de un array
Una característica muy útil de los arrays es que es muy fácil obtener otro array con los elementos que cumplen una condición.
- *a[condicion]* : Devuelve una lista con los elementos del array *a* que cumplen la condición *condicion*.
~~~~ python
>>> a = np.array([[1, 2, 3], [4, 5, 6]])
>>> print(a[(a % 2 == 0)])
[2 4 6]
>>> print(a[(a % 2 == 0) &  (a > 2)])
[4 6]
~~~~

### Operaciones matemáticas con arrays
Existen dos formas de realizar operaciones matemáticas con arrays: a nivel de elemento y a nivel de array.

Las operaciones a nivel de elemento operan los elementos que ocupan la misma posición en dos arrays. Se necesitan, por tanto, dos arrays con las mismas dimensiones y el resultado es una array de la misma dimensión.

Los operadores mamemáticos *+*, *-*, *\**, */*, *%*, *\*\** se utilizan para la realizar suma, resta, producto, cociente, resto y potencia a nivel de elemento.
~~~~ python
>>> a = np.array([[1, 2, 3], [4, 5, 6]])
>>> b = np.array([[1, 1, 1], [2, 2, 2]])
>>> print(a + b )
[[2 3 4]
 [6 7 8]]
>>> print(a / b)
[[1.  2.  3. ]
 [2.  2.5 3. ]]
>>> print(a ** 2)
[[ 1  4  9]
 [16 25 36]]
 ~~~~

### Álgebra matricial
Numpy incorpora funciones para realizar las principales operaciones algebraicas con vectores y matrices. La mayoría de los métodos algebráicos se agrupan en el submódulo *linalg*.

#### Producto escalar de dos vectores
Para realizar el producto escalar de dos vectores se utiliza el operador *@* o el siguiente método:
- *u.dot(v)* : Devuelve el producto escalar de los vectores *u* y *v*.
~~~~ python
>>> import numpy as np
>>> a = np.array([1, 2, 3])
>>> b = np.array([1, 0, 1])
>>> print(a @ b)
4
>>> print(a.dot(b))
4
~~~~

#### Módulo de un vector
Para calcular el módulo de un vector se utiliza el siguiente método:
- *norm(v)* : Devuelve el módulo del vector *v*.
~~~~ python
>>> import numpy as np
>>> a = np.array([3, 4])
>>> print(np.linalg.norm(a))
5.0
~~~~

#### Producto de dos matrices
Para realizar el producto matricial se utiliza el mismo operador *@* y método que para el producto escalar de vectores:
- *a.dot(b)* : Devuelve el producto matricial de las matrices *a* y *b* siempre y cuando sus dimensiones sean compatibles.
~~~~ python
>>> import numpy as np
>>> a = np.array([[1, 2, 3], [4, 5, 6]])
>>> b = np.array([[1, 1], [2, 2], [3, 3]])
>>> print(a @ b)
[[14 14]
 [32 32]]
>>> print(a.dot(b))
[[14 14]
 [32 32]]
~~~~

#### Matriz traspuesta
Para trasponer una matriz se utiliza el método
- *a.T* : Devuelve la matriz traspuesta de la matriz *a*.
~~~~ python
>>> import numpy as np
>>> a = np.array([[1, 2, 3], [4, 5, 6]])
>>> print(a.T)
[[1 4]
 [2 5]
 [3 6]]
~~~~

#### Traza de una matriz
La traza de una matriz cuadrada se calcula con el siguiente método:
- *a.trace()* : Devuelve la traza (suma de la diagonal principal) de la matriz cuadrada *a*.
~~~~ python
>>> import numpy as np
>>> a = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
>>> print(a.trace())
15
~~~~

#### Determinante de una matriz
El determinante de una matriz cuadrada se calcula con la siguiente función:
- *det(a)* : Devuelve el determinante de la matriz cuadrada *a*.
~~~~ python
>>> import numpy as np
>>> a = np.array([[1, 2], [3, 4]])
>>> print(np.linalg.det(a))
-2.0
~~~~

#### Matriz inversa
La inversa de una matriz se calcula con la siguiente función:
- *inv(a)* : Devuelve la matriz inversa de la matriz cuadrada *a*.
~~~~ python
>>> import numpy as np
>>> a = np.array([[1, 2], [3, 4]])
>>> print(np.linalg.inv(a))
[[-2.   1. ]
 [ 1.5 -0.5]]
~~~~

#### Autovalores de una matriz
Los autovalores de una matriz cuadrada se calculan con la siguiente función:
- *eigvals(a)* : Devuelve los autovalores de la matriz cuadrada *a*.
~~~~ python
>>> import numpy as np
>>> a = np.array([[1, 1, 0], [1, 2, 1], [0, 1, 1]])
>>> print(np.linalg.eigvals(a))
[ 3.00000000e+00  1.00000000e+00 -3.36770206e-17]
~~~~

#### Autovectores de una matriz
Los autovectores de una matriz cuadrada se calculan con la siguiente función:
- *eig(a)* : Devuelve los autovalores y los autovectores asociados de la matriz cuadrada *a*.
~~~~ python
>>> import numpy as np
>>> a = np.array([[1, 1, 0], [1, 2, 1], [0, 1, 1]])
>>> print(np.linalg.eig(a))
(array([ 3.00000000e+00,  1.00000000e+00, -3.36770206e-17]), 
 array([[-4.08248290e-01,  7.07106781e-01,  5.77350269e-01],
        [-8.16496581e-01,  2.61239546e-16, -5.77350269e-01],
        [-4.08248290e-01, -7.07106781e-01,  5.77350269e-01]]))
~~~~

#### Solución de un sistema de ecuaciones
Para resolver un sistema de ecuaciones lineales se utiliza la función siguiente:
- *solve(a, b)* : Devuelve la solución del sistema de ecuaciones lineales con los coeficientes de la matriz *a* y los términos independientes de la matriz *b*.
~~~~ python
>>> import numpy as np
# Sistema de dos ecuaciones y dos incógnitas
# x + 2y = 1
# 3x + 5y = 2 
>>> a = np.array([[1, 2], [3, 5]])
>>> b = np.array([1, 2])
>>> print(np.linalg.solve(a, b))
[-1.  1.]
~~~~

## Bases de datos (SQLite)
SQLite es un gestor de bases de datos relacional pero con objetivos muy diferentes a los gestores como MySQL, SQLServer, Oracle, PostgreSQL etc.

![](Fotos/Manual_Python/Bases_de_datos/SQLiteLogo.JPG)

Este gestor de base de datos tiene por objetivo ser parte de la misma aplicación con la que colabora, es decir no cumple los conceptos de cliente y servidor.

Para entender sus usos podemos dar algunos ejemplos donde se utiliza el gestor SQLite:
- Firefox usa SQLite para almacenar los favoritos, el historial, las cookies etc.
- Los navegadores Opera y Chrome.
- La aplicación de comunicaciones Skype de Microsoft.
- Los sistemas operativos Android y iOS adoptan SQLite para permitir el almacenamiento y recuperación de datos.

Podemos conocer otras empresas famosas que hacen uso de SQLite visitando el [sitio oficial de SQLite](https://www.sqlite.org/famous.html).

SQLite es Open Source y colabora con el almacenamiento de datos cuando hacemos aplicaciones con lenguajes como Python, Java, C#, C, C++, Delphi etc.

|Ventajas|Inconvenientes|
|:-|:-|
|Ocupa muy poco espacio en disco y memoria.|No admite clausulas anidadas (where).|
|Muy eficiente y rápido.|No existen usuarios (no acceso simultáneo por parte de varios usuarios a la vez).|
|Multiplataforma.|Falta de clave foránea cuando se crea en modo consola.|
|Sin administración / configuración.||
|Dominio público.||

### Pasos a seguir para conectar BBDD
1. Abrir-Crear conexión.
2. Crear puntero.
3. Ejecutar query (consulta) SQL.
4. Manejar los resultados de la query (consulta).
    - **C**reate (Insertar)
    - **R**ead (Leer)
    - **U**pdate (Actualizar)
    - **D**elete (Borrar)
5. Cerrar puntero.
6. Cerrar conexión.   

~~~~ python
import sqlite3 as sql

#1
conexion = sql.connect("Base")
#2
cursor = conexion.cursor()
#3
cursor.execute("CREATE TABLE PRODUCTOS (NOMBRE_ARTICULO VARCHAR(50), PRECIO INTEGER, SECCION VARCHAR(20))")
cursor.execute("INSERT INTO  PRODUCTOS VALUES('BALON', 15, 'DEPORTES')")
#4
conexion.commit()
#5
cursor.close()
#6
conexion.close()
~~~~

Si se quieren ejecutar varios registros se podría tanto ejecutar una query para cada registro como utilizar el comando *".executemany()"* con la ayuda de una lista de tuplas.
~~~~ python
ListaProductos = [('CAMISETA', 10, 'ROPA')    ,
                  ('JARRÓN'  , 90, 'JARDIN')  ,
                  ('PELUCHE' , 20, 'JUGUETES')]

cursor.executemany("INSERT INTO PRODUCTOS VALUES(?, ?, ?)" , ListaProductos)
~~~~

Para seleccionar y mostrar registros de nuestra tabla primero hay que seleccionar con una query los registros deseados y después "traerlos" con el comando *.fetchone()*, *.fetchmany(cantidad)* ó *.fetchall()* del cursor.
~~~~ python
>>> cursor.execute("SELECT * FROM PRODUCTOS")
>>> for producto in cursor.fetchall()
...     print(producto)
('BALON', 15, 'DEPORTES')
('CAMISETA', 10, 'ROPA')
('JARRÓN'  , 90, 'JARDIN')
('PELUCHE' , 20, 'JUGUETES')
~~~~

En caso de que se quiera trabajar con una columna de acceso de valores únicos (como el DNI de cada persona) es necesario declararlo en la creación de la tabla.
~~~~ python
import sqlite3 as sql

conexion = sql.connect("Base")
cursor = conexion.cursor()

cursor.execute('''
    CREATE TABLE PRODUCTOS_2 (
        CODIGO_ARTICULO VARCHAR(4) PRIMARY KEY,
        NOMBRE_ARTICULO VARCHAR(50),
        PRECIO INTEGER,
        SECCION VARCHAR(20))
''')

productos = [('AR01', 'PELOTA'        , 20, 'JUGUETES')  ,
             ('AR02', 'PANTALÓN'      , 15, 'ROPA' )     ,
             ('AR03', 'DESTORNILLADOR', 25, 'FERRETERÍA'),
             ('AR04', 'JARRÓN'        , 45, 'JARDÍN')]

cursor.executemany("INSERT INTO PRODUCTOS_2 VALUES (?, ?, ?, ?)", productos)
conexion.commit()

curosr.close()
conexion.close()
~~~~
> ⚠️ Si se quiere que una clave se autogestione automáticamente, hay que declarar *AUTOINCREMENT* después de declarar su tipo de dato. Normalmente se suele declarar como *'ID'* de valor entero. 
Después de esta declaración, al insertar, la columna de la clave autoincrementada debe contener el valor *NULL*.
> ~~~~ python
> cursor.execute('''
>     CREATE TABLE PRODUCTOS_2 (
>         ID INTEGER PRIMARY KEY AUTOINCREMENT,
>         NOMBRE_ARTICULO VARCHAR(50),
>         PRECIO INTEGER,
>         SECCION VARCHAR(20))
> ''')
>
> productos = [('PELOTA'        , 20, 'JUGUETES')  ,
>              ('PANTALÓN'      , 15, 'ROPA' )     ,
>              ('DESTORNILLADOR', 25, 'FERRETERÍA'),
>              ('JARRÓN'        , 45, 'JARDÍN')]
>
> cursor.executemany("INSERT INTO PRODUCTOS_2 VALUES (NULL, ?, ?, ?)", productos)
> conexion.commit()
> ~~~~

En caso que se quiera trabajar con una columna de valores únicos (a parte de la *PRIMARY KEY*), se declara el parámetro *UNIQUE* después del tipo de dato.
~~~~ python
cursor.execute('''
    CREATE TABLE PRODUCTOS_2 (
        CODIGO_ARTICULO VARCHAR(4)  PRIMARY KEY,
        NOMBRE_ARTICULO VARCHAR(50) UNIQUE,
        PRECIO INTEGER,
        SECCION VARCHAR(20))
''')
~~~~

## Librería Pandas
---
[Pandas](https://pandas.pydata.org/) es una librería de Python especializada en el manejo y análisis de estructuras de datos.

![](Fotos/Manual_Python/Libreria_Pandas/PandasLogo.PNG)

Las principales características de esta librería son:
- Define nuevas estructuras de datos basadas en los arrays de la librería NumPy pero con nuevas funcionalidades.
- Permite leer y escribir fácilmente ficheros en formato CSV, Excel y bases de datos SQL.
- Permite acceder a los datos mediante índices o nombres para filas y columnas.
- Ofrece métodos para reordenar, dividir y combinar conjuntos de datos.
- Permite trabajar con series temporales.
- Realiza todas estas operaciones de manera muy eficiente.

### Tipos de datos de Pandas
Pandas dispone de tres estructuras de datos diferentes:
- **Series**: Estructura de una dimensión.
- **DataFrame** : Estructura de dos dimensiones (tablas).
- **Panel** : Estructura de tres dimensiones (cubos).

Estas estructuras se construyen a partir de arrays de la librería NumPy, añadiendo nuevas funcionalidades.

### La clase de objetos Series
Son estructuras similares a los arrays de una dimensión. Son homogéneas, es decir, sus elementos tienen que ser del mismo tipo, y su tamaño es inmutable, es decir, no se puede cambiar, aunque si su contenido.

Dispone de un índice que asocia un nombre a cada elemento del la serie, a través de la cuál se accede al elemento.

> **Ejemplo.** La siguiente serie contiene las asignaturas de un curso.
![](Fotos/Manual_Python/Libreria_Pandas/Series.PNG)

### Creación de series
#### Creación de una serie a partir de una lista
- *Series(data=lista, index=indices, dtype=tipo)* : Devuelve un objeto de tipo Series con los datos de la lista *lista*, las filas especificados en la lista *indices* y el tipo de datos indicado en *tipo*. Si no se pasa la lista de índices se utilizan como índices los enteros del *0* al *n-1*, done  es el tamaño de la serie. Si no se pasa el tipo de dato se infiere.
~~~~ python
>>> import pandas as pd
>>> s = pd.Series(['Matemáticas', 'Historia', 'Economía', 'Programación', 'Inglés'], dtype='string')
>>> print(s)
0     Matemáticas
1        Historia
2        Economía
3    Programación
4          Inglés
dtype: string
~~~~

#### Creación de una serie a partir de un diccionario
- *Series(data=diccionario, index=indices)* : Devuelve un objeto de tipo Series con los valores del diccionario *diccionario* y las filas especificados en la lista *indices*. Si no se pasa la lista de índices se utilizan como índices las claves del diccionario.
~~~~ python
>>> import pandas as pd
>>> s = pd.Series({'Matemáticas': 6.0,  'Economía': 4.5, 'Programación': 8.5})
>>> print(s)
Matemáticas     6.0
Economía        4.5
Programación    8.5
dtype: float64
~~~~

### Atributos de una serie
Existen varias propiedades o métodos para ver las características de una serie.
- *s.size* : Devuelve el número de elementos de la serie *s*.
- *s.index* : Devuelve una lista con los nombres de las filas del DataFrame *s*.
- *s.dtype* : Devuelve el tipo de datos de los elementos de la serie *s*.
~~~~ python
>>> import pandas as pd
>>> s = pd.Series([1, 2, 2, 3, 3, 3, 4, 4, 4, 4])
>>> s.size
10
>>> s.index
RangeIndex(start=0, stop=10, step=1)
>>> s.dtype
dtype('int64')
~~~~

### Acceso a los elementos de una serie
El acceso a los elementos de un objeto del tipo Series puede ser a través de posiciones o través de índices (nombres).

#### Acceso por posición
Se realiza de forma similar a como se accede a los elementos de un array.
- *s[i]* : Devuelve el elemento que ocupa la posición *i+1* en la serie *s*.
- *s[posiciones]* : Devuelve otra serie con los elementos que ocupan las posiciones de la lista *posiciones*.

#### Acceso por índice
- *s[nombre]* : Devuelve el elemento con el nombre *nombre* en el índice.
- *s[nombres]* : Devuelve otra serie con los elementos correspondientes a los nombres indicadas en la lista *nombres* en el índice.
~~~~ python
>>> s[1:3]
Economía        4.5
Programación    8.5
dtype: float64
>>> s['Economía']
4.5
>>> s[['Programación', 'Matemáticas']]
Programación    8.5
Matemáticas     6.0
dtype: float64
~~~~

### Resumen descriptivo de una serie
Las siguientes funciones permiten resumir varios aspectos de una serie:
- *s.count()* : Devuelve el número de elementos que no son nulos ni *NaN* en la serie *s*.
- *s.sum()* : Devuelve la suma de los datos de la serie *s* cuando los datos son de un tipo numérico, o la concatenación de ellos cuando son del tipo cadena *str*.
- *s.cumsum()* : Devuelve una serie con la suma acumulada de los datos de la serie *s* cuando los datos son de un tipo numérico.
- *s.value_counts()* : Devuelve una serie con la frecuencia (número de repeticiones) de cada valor de la serie *s*.
- *s.min()* : Devuelve el menor de los datos de la serie *s*.
- *s.max()* : Devuelve el mayor de los datos de la serie *s*.
- *s.mean()* : Devuelve la media de los datos de la serie *s* cuando los datos son de un tipo numérico.
- *s.var()* : Devuelve la varianza de los datos de la serie *s* cuando los datos son de un tipo numérico.
- *s.std()* : Devuelve la desviación típica de los datos de la serie *s* cuando los datos son de un tipo numérico.
- *s.describe()* : Devuelve una serie con un resumen descriptivo que incluye el número de datos, su suma, el mínimo, el máximo, la media, la desviación típica y los cuartiles.
~~~~ python
>>> import pandas as pd
>>> s = pd.Series([1, 1, 1, 1, 2, 2, 2, 3, 3, 4])
>>> s.count()  # Tamaño muestral
10
>>> s.sum()  # Suma
20
>>> s.cumsum()  # Suma acumulada
0     1
1     2
2     3
3     4
4     6
5     8
6    10
7    13
8    16
9    20
dtype: int64
>>> s.value_counts()  # Frecuencias absolutas
1    4
2    3
3    2
4    1
dtype: int64
>>> s.value_counts(normalize=True)  # Frecuencias relativas
1    0.4
2    0.3
3    0.2
4    0.1
dtype: float64
>>> s.min()  # Mínimo
1
>>> s.max()  # Máximo
4
>>> s.mean()  # Media
2.0
>>> s.var()  # Varianza
1.1111111111111112
>>> s.std()  # Desviación típica
1.0540925533894598
>>> s.describe()  # Resume descriptivo
count    10.000000
mean      2.000000
std       1.054093
min       1.000000
25%       1.000000
50%       2.000000
75%       2.750000
max       4.000000
dtype: float64
~~~~

### Aplicar operaciones a una serie
Los operadores binarios (*+*, *\**, */*, etc.) pueden utilizarse con una serie, y devuelven otra serie con el resultado de aplicar la operación a cada elemento de la serie.
~~~~ python
>>> import pandas as pd
s = pd.Series([1, 2, 3, 4])
>>> s * 2
0    2
1    4
2    6
3    8
dtype: int64
>>> s % 2
0    1
1    0
2    1
3    0
dtype: int64
>>> s = pd.Series(['a', 'b', 'c'])
>>> s * 5
0    aaaaa
1    bbbbb
2    ccccc
dtype: object
~~~~

### Aplicar funciones a una serie
También es posible aplicar una función a cada elemento de la serie mediante el siguiente método:

- *s.apply(f)* : Devuelve una serie con el resultado de aplicar la función *f* a cada uno de los elementos de la serie *s*.
~~~~ python
>>> import pandas as pd
>>> from math import log
>>> s = pd.Series([1, 2, 3, 4])
>>> s.apply(log)
0    0.000000
1    0.693147
2    1.098612
3    1.386294
dtype: float64
>>> s = pd.Series(['a', 'b', 'c'])
>>> s.apply(str.upper)
0    A
1    B
2    C
dtype: object
~~~~

### Filtrar una serie
Para filtrar una serie y quedarse con los valores que cumplen una determinada condición se utiliza el siguiente método:

- *s[condicion]* : Devuelve una serie con los elementos de la serie *s* que se corresponden con el valor *\<True>* de la lista booleana *condicion*. *condicion* debe ser una lista de valores booleanos de la misma longitud que la serie.
~~~~ python
>>> import pandas as pd
>>> s = pd.Series({'Matemáticas': 6.0,  'Economía': 4.5, 'Programación': 8.5})
>>> print(s[s > 5])
Matemáticas     6.0
Programación    8.5
dtype: float64
~~~~

### Ordenar una serie
Para ordenar una serie se utilizan los siguientes métodos:
- *s.sort_values(ascending=booleano)* : Devuelve la serie que resulta de ordenar los valores la serie *s*. Si argumento del parámetro *ascending* es *\<True>* el orden es creciente y si es *\<False>* decreciente.
- *df.sort_index(ascending=booleano)* : Devuelve la serie que resulta de ordenar el índice de la serie s. Si el argumento del parámetro *ascending* es *\<True>* el orden es creciente y si es *\<False>* decreciente.
~~~~ python
>>> import pandas as pd
>>> s = pd.Series({'Matemáticas': 6.0,  'Economía': 4.5, 'Programación': 8.5})
>>> print(s.sort_values())
Economía        4.5
Matemáticas     6.0
Programación    8.5
dtype: float64
>>> print(s.sort_index(ascending = False))
Programación    8.5
Matemáticas     6.0
Economía        4.5
dtype: float64
~~~~

### Eliminar los dados desconocidos en una serie
Los datos desconocidos representan en Pandas por *NaN* y los nulos por *None*. Tanto unos como otros suelen ser un problema a la hora de realizar algunos análisis de datos, por lo que es habitual eliminarlos. Para eliminarlos de una serie se utiliza el siguiente método:
- *s.dropna()* : Elimina los datos desconocidos o nulos de la serie *s*.
~~~~ python
>>> import pandas as pd
>>> import numpy as np
>>> s = pd.Series(['a', 'b', None, 'c', np.NaN,  'd'])
>>> s
0       a
1       b
2    None
3       c
4     NaN
5       d
dtype: object
>>> s.dropna()
0    a
1    b
3    c
5    d
dtype: object
~~~~

### La clase de objetos DataFrame
Un objeto del tipo DataFrame define un conjunto de datos estructurado en forma de tabla donde cada columna es un objeto de tipo Series, es decir, todos los datos de una misma columna son del mismo tipo, y las filas son registros que pueden contender datos de distintos tipos.

Un DataFrame contiene dos índices, uno para las filas y otro para las columnas, y se puede acceder a sus elementos mediante los nombres de las filas y las columnas.

> **Ejemplo.** El siguiente DataFrame contiene información sobre los alumnos de un curso. Cada fila corresponde a un alumno y cada columna a una variable.

![](Fotos/Manual_Python/Libreria_Pandas/Dataframe.PNG)

### Creación de un DataFrame
#### Creación de un DataFrame a partir de un diccionario de listas
Para crear un DataFrame a partir de un diccionario cuyas claves son los nombres de las columnas y los valores son listas con los datos de las columnas se utiliza el método:
- *DataFrame(data=diccionario, index=filas, columns=columnas, dtype=tipos)* : Devuelve un objeto del tipo DataFrame cuyas columnas son las listas contenidas en los valores del diccionario *diccionario*, los nombres de filas indicados en la lista *filas*, los nombres de columnas indicados en la lista *columnas* y los tipos indicados en la lista *tipos*. La lista *filas* tiene que tener el mismo tamaño que las listas del diccionario, mientras que las listas *columnas* y *tipos* tienen que tener el mismo tamaño que el diccionario. Si no se pasa la lista de filas se utilizan como nombres los enteros empezando en 0. Si no se pasa la lista de columnas se utilizan como nombres las claves del diccionario. Si no se pasa la lista de tipos, se infiere.
 
> ⚠️ Los valores asociados a las claves del diccionario deben ser listas del mismo tamaño.
~~~~ python
>>> import pandas as pd
>>> datos = {'nombre':['María', 'Luis', 'Carmen', 'Antonio'],
... 'edad':[18, 22, 20, 21],
... 'grado':['Economía', 'Medicina', 'Arquitectura', 'Economía'],
... 'correo':['maria@gmail.com', 'luis@yahoo.es', 'carmen@gmail.com', 'antonio@gmail.com']
... }
>>> df = pd.DataFrame(datos)
>>> print(df)
    nombre  edad         grado             correo
0    María    18      Economía    maria@gmail.com
1     Luis    22      Medicina      luis@yahoo.es
2   Carmen    20  Arquitectura   carmen@gmail.com
3  Antonio    21      Economía  antonio@gmail.com
~~~~

#### Creación de un DataFrame a partir de una lista de listas
Para crear un DataFrame a partir de una lista de listas con los datos de las columnas se utiliza el siguiente método:
- *DataFrame(data=listas, index=filas, columns=columnas, dtype=tipos)* : Devuelve un objeto del tipo DataFrame cuyas columnas son los valores de las listas de la lista *listas*, los nombres de filas indicados en la lista *filas*, los nombres de columnas indicados en la lista *columnas* y los tipos indicados en la lista *tipos*. La lista *filas*, tiene que tener el mismo tamaño que la lista *listas* mientras que las listas *columnas* y *tipos* tienen que tener el mismo tamaño que las listas anidadas en *listas*. Si no se pasa la lista de filas o de columnas se utilizan enteros empezando en 0. Si no se pasa la lista de tipos, se infiere.
> ⚠️ Si las listas anidadas en *listas* no tienen el mismo tamaño, las listas menores se rellenan con valores *NaN*.
~~~~ python
>>> import pandas as pd
>>> df = pd.DataFrame([['María', 18], ['Luis', 22], ['Carmen', 20]], columns=['Nombre', 'Edad'])
>>> print(df)
   Nombre   Edad
0   María     18
1    Luis     22
2  Carmen     20
~~~~

#### Creación de un DataFrame a partir de una lista de diccionarios
Para crear un DataFrame a partir de una lista de diccionarios con los datos de las filas, se utiliza el siguiente método:
- *DataFrame(data=diccionarios, index=filas, columns=columnas, dtype=tipos)* : Devuelve un objeto del tipo DataFrame cuyas filas contienen los valores de los diccionarios de la lista *diccionarios*, los nombres de filas indicados en la lista *filas*, los nombres de columnas indicados en la lista *columnas* y los tipos indicados en la lista *tipos*. La lista *filas* tiene que tener el mismo tamaño que la lista *lista*. Si no se pasa la lista de filas se utilizan enteros empezando en 0. Si no se pasa la lista de columnas se utilizan las claves de los diccionarios. Si no se pasa la lista de tipos, se infiere.
> ⚠️ Si los diccionarios no tienen las mismas claves, las claves que no aparecen en el diccionario se rellenan con valores *NaN*.
~~~~ python
>>> import pandas as pd
>>> df = pd.DataFrame([{'Nombre':'María', 'Edad':18}, {'Nombre':'Luis', 'Edad':22}, {'Nombre':'Carmen'}])
>>> print(df)
0   María  18.0
1    Luis  22.0
2  Carmen   NaN
~~~~

#### Creación de un DataFrame a partir de un array
Para crear un DataFrame a partir de un array de NumPy se utiliza el siguiente método:
- *DataFrame(data=array, index=filas, columns=columnas, dtype=tipo)* : Devuelde un objeto del tipo DataFrame cuyas filas y columnas son las del array *array*, los nombres de filas indicados en la lista *filas*, los nombres de columnas indicados en la lista *columnas* y el tipo indicado en *tipo*. La lista *filas* tiene que tener el mismo tamaño que el número de filas del array y la lista *columnas* el mismo tamaño que el número de columnas del array. Si no se pasa la lista de filas se utilizan enteros empezando en 0. Si no se pasa la lista de columnas se utilizan las claves de los diccionarios. Si no se pasa la lista de tipos, se infiere.
~~~~ python
>>> import pandas as pd
>>> df = pd.DataFrame(np.random.randn(4, 3), columns=['a', 'b', 'c'])
>>> print(df)
          a         b         c
0 -1.408238  0.644706  1.077434
1 -0.279264 -0.249229  1.019137
2 -0.805470 -0.629498  0.935066
3  0.236936 -0.431673 -0.177379
~~~~

#### Creación de un DataFrame a partir de un fichero CSV o Excel
Dependiendo del tipo de fichero, existen distintas funciones para importar un DataFrame desde un fichero.
- *read_csv(fichero.csv, sep=separador, header=n, index_col=m, na_values=no-validos, decimal=separador-decimal)* : Devuelve un objeto del tipo DataFrame con los datos del fichero CSV *<fichero.csv>* usando como separador de los datos la cadena *separador*. Como nombres de columnas se utiliza los valores de la fila *n* y como nombres de filas los valores de la columna *m*. Si no se indica m se utilizan como nombres de filas los enteros empezando en *0*. Los valores incluídos en la lista *no-validos* se convierten en *NaN*. Para los datos numéricos se utiliza como separador de decimales el carácter indicado en *separador-decimal*.
- *read_excel(fichero.xlsx, sheet_name=hoja, header=n, index_col=m, na_values=no-validos, decimal=separador-decimal)* : Devuelve un objeto del tipo DataFrame con los datos de la hoja de cálculo *hoja* del fichero Excel *<fichero.xlsx>*. Como nombres de columnas se utiliza los valores de la fila *n* y como nombres de filas los valores de la columna *m*. Si no se indica *m* se utilizan como nombres de filas los enteros empezando en *0*. Los valores incluídos en la lista *no-validos* se convierten en *NaN*. Para los datos numéricos se utiliza como separador de decimales el carácter indicado en *separador-decimal*.
~~~~ python
>>> import pandas as pd
>>> # Importación del fichero datos-colesteroles.csv
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesteroles.csv', sep=';', decimal=',')
>>> print(df.head())
                              nombre  edad sexo    peso    altura  colesterol
0       José Luis Martínez Izquierdo    18    H    85.0    1.79         182.0
1                     Rosa Díaz Díaz    32    M    65.0    1.73         232.0
2              Javier García Sánchez    24    H     NaN    1.81         191.0
3                Carmen López Pinzón    35    M    65.0    1.70         200.0
4               Marisa López Collado    46    M    51.0    1.58         148.0
~~~~

### Exportación de ficheros
También existen funciones para exportar un DataFrame a un fichero con diferentes formatos.
- *df.to_csv(fichero.csv, sep=separador, columns=booleano, index=booleano)* : Exporta el DataFrame *df* al fichero *<fichero.csv>* en formato CSV usando como separador de los datos la cadena *separador*. Si se pasa *\<True>* al parámetro *columns* se exporta también la fila con los nombres de columnas y si se pasa *<\True>* al parámetro *index* se exporta también la columna con los nombres de las filas.
- *df.to_excel(fichero.xlsx, sheet_name = hoja, columns=booleano, index=booleano)* : Exporta el DataFrame *df* a la hoja de cálculo *hoja* del fichero *<fichero.xlsx>* en formato Excel. Si se pasa *\<True>* al parámetro *columns* se exporta también la fila con los nombres de columnas y si se pasa *\<True>* al parámetro *index* se exporta también la columna con los nombres de las filas.

### Atributos de un DataFrame
Existen varias propiedades o métodos para ver las características de un DataFrame.
- *df.info()* : Devuelve información (número de filas, número de columnas, índices, tipo de las columnas y memoria usado) sobre el DataFrame *df*.
- *df.shape* : Devuelve una tupla con el número de filas y columnas del DataFrame *df*.
- *df.size* : Devuelve el número de elementos del DataFrame.
- *df.columns* : Devuelve una lista con los nombres de las columnas del DataFrame *df*.
- *df.index* : Devuelve una lista con los nombres de las filas del DataFrame *df*.
- *df.dtypes* : Devuelve una serie con los tipos de datos de las columnas del DataFrame *df*.
- *df.head(n)* : Devuelve las *n* primeras filas del DataFrame *df*.
- *df.tail(n)* : Devuelve las *n* últimas filas del DataFrame *df*.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> df.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 14 entries, 0 to 13
Data columns (total 6 columns):
 #   Column      Non-Null Count  Dtype  
---  ------      --------------  -----  
 0   nombre      14 non-null     object 
 1   edad        14 non-null     int64  
 2   sexo        14 non-null     object 
 3   peso        13 non-null     float64
 4   altura      14 non-null     float64
 5   colesterol  13 non-null     float64
dtypes: float64(3), int64(1), object(2)
memory usage: 800.0+ bytes
>>> df.shape
(14, 6)
>>> df.size
84
>>> df.columns
Index(['nombre', 'edad', 'sexo', 'peso', 'altura', 'colesterol'], dtype='object')
>>> df.index
RangeIndex(start=0, stop=14, step=1)
>>> df.dtypes
nombre         object
edad            int64
sexo           object
peso          float64
altura        float64
colesterol    float64
dtype: object
~~~~

### Renombrar los nombres de las filas y columnas
Para cambiar el nombre de las filas y las columnas de un DataFrame se utiliza el siguiente método:
- *df.rename(columns=columnas, index=filas)* : Devuelve el DataFrame que resulta de renombrar las columnas indicadas en las claves del diccionario *columnas* con sus valores y las filas indicadas en las claves del diccionario *filas* con sus valores en el DataFrame *df*.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.rename(columns={'nombre':'nombre y apellidos', 'altura':'estatura'}, index={0:1000, 1:1001, 2:1002}))
                    nombre y apellidos  edad sexo    peso  estatura    colesterol
1000      José Luis Martínez Izquierdo    18    H    85.0      1.79         182.0
1001                    Rosa Díaz Díaz    32    M    65.0      1.73         232.0
1002             Javier García Sánchez    24    H     NaN      1.81         191.0
3                  Carmen López Pinzón    35    M    65.0      1.70         200.0
4                 Marisa López Collado    46    M    51.0      1.58         148.0
...
~~~~

### Cambiar el índice de un DataFrame
Aunque el índice de un DataFrame suele fijarse en la creación del mismo, en ocasiones puede ser necesario cambiar el índice una vez creado el DataFrame. Para ello se utiliza el siguiente método:
- *df.set_index(keys = columnas, verify_integrity = bool)* : Devuelve el DataFrame que resulta de eliminar las columnas de la lista *columnas* y convertirlas en el nuevo índice. El parámetro *verify_integrity* recibe un booleano (*\<False>* por defecto) y realiza una comprobación para evitar duplicados en la clave cuando recibe *\<True>*.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.set_index("nombre").head())
                              edad sexo  peso  altura  colesterol
nombre                                                           
José Luis Martínez Izquierdo    18    H  85.0    1.79       182.0
Rosa Díaz Díaz                  32    M  65.0    1.73       232.0
Javier García Sánchez           24    H   NaN    1.81       191.0
Carmen López Pinzón             35    M  65.0    1.70       200.0
Marisa López Collado            46    M  51.0    1.58       148.0
>>> 
~~~~

### Reindexar un DataFrame
Para reordenar los índices de las filas y las columnas de un DataFrame, así como añadir o eliminar índices, se utiliza el siguiente método:
- *df.reindex(index=filas, columns=columnas, fill_value=relleno)* : Devuelve el DataFrame que resulta de tomar del DataFrame *df* las filas con nombres en la lista *filas* y las columnas con nombres en la lista *columnas*. Si alguno de los nombres indicados en *filas* o *columnas* no existía en el DataFrame *df*, se crean filan o columnas nuevas rellenas con el valor *relleno*.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.reindex(index=[4, 3, 1], columns=['nombre', 'tensión', 'colesterol']))
                  nombre  tensión  colesterol
4   Marisa López Collado      NaN       148.0
3    Carmen López Pinzón      NaN       200.0
1         Rosa Díaz Díaz      NaN       232.0
~~~~

### Acceso a los elementos de un DataFrame
El acceso a los datos de un DataFrame se puede hacer a través de posiciones o través de los nombres de las filas y columnas.

#### Accesos mediante posiciones
- *df.iloc[i, j]* : Devuelve el elemento que se encuentra en la fila *i* y la columna *j* del DataFrame *df*. Pueden indicarse secuencias de índices para obtener partes del DataFrame.
- *df.iloc[filas, columnas]* : Devuelve un DataFrame con los elementos de las filas de la lista *filas* y de las columnas de la lista *columnas*.
- *df.iloc[i]* : Devuelve una serie con los elementos de la fila *i* del DataFrame *df*.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.iloc[1, 3])
65
>>> print(df.iloc[1, :2])
nombre     Rosa Díaz Díaz
edad                   32
~~~~

#### Acceso a los elementos mediante nombres
- *df.loc[fila, columna]* : Devuelve el elemento que se encuentra en la fila con nombre *fila* y la columna de con nombre *columna* del DataFrame *df*.
- *df.loc[filas, columnas]* : Devuelve un DataFrame con los elemento que se encuentra en las filas con los nombres de la lista *filas* y las columnas con los nombres de la lista *columnas* del DataFrame *df*.
- *df[columna]* : Devuelve una serie con los elementos de la columna de nombre *columna* del DataFrame *df*.
- *df.columna* : Devuelve una serie con los elementos de la columna de nombre *columna* del DataFrame *df*. Es similar al método anterior pero solo funciona cuando el nombre de la columna no tiene espacios en blanco.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.loc[2, 'colesterol'])
191
>>> print(df.loc[:3, ('colesterol','peso')])
     colesterol    peso
1         232.0    65.0
2         191.0     NaN
3         200.0    65.0
>>> print(df['colesterol'])
0     182.0
1     232.0
2     191.0
3     200.0
...
~~~~

### Operaciones con las columnas de un DataFrame
#### Añadir columnas a un DataFrame
El procedimiento para añadir una nueva columna a un DataFrame es similar al de añadir un nuevo par a un diccionario, pero pasando los valores de la columna en una lista o serie.
- *d[nombre] = lista* : Añade al DataFrame *df* una nueva columna con el nombre *nombre* y los valores de la lista *lista*. La lista debe tener el mismo tamaño que el número de filas de *df*.
- *d[nombre] = serie* : Añade al DataFrame *df* una nueva columna con el nombre *nombre* y los valores de la serie *serie*. Si el tamaño de la serie es menor que el número de filas de *df* se rellena con valores *NaN* mientras que si es mayor se recorta.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> df['diabetes'] = pd.Series([False, False, True, False, True])
>>> print(df)
                              nombre  edad sexo    peso  altura    colesterol diabetes
0       José Luis Martínez Izquierdo    18    H    85.0    1.79         182.0    False
1                     Rosa Díaz Díaz    32    M    65.0    1.73         232.0    False
2              Javier García Sánchez    24    H   NaN.0    1.81         191.0     True
3                Carmen López Pinzón    35    M    65.0    1.70         200.0    False
4               Marisa López Collado    46    M    51.0    1.58         148.0     True
5                  Antonio Ruiz Cruz    68    H    66.0    1.74         249.0      NaN
...
~~~~

#### Operaciones sobre columnas
Puesto que los datos de una misma columna de un DataFrame son del mismo tipo, es fácil aplicar la misma operación a todos los elementos de la columna.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df['altura']*100)
0     179
1     173
2     181
...

>>> print(df['sexo']=='M')
0     False
1      True
2     False
...
~~~~

#### Aplicar funciones a columnas
Para aplicar funciones a todos los elementos de una columna se utiliza el siguiente método:
- *df[columna].apply(f)* : Devuelve una serie con los valores que resulta de aplicar la función *f* a los elementos de la columna con nombre *columna* del DataFrame *df*.
~~~~ python
>>> import pandas as pd
>>> from math import log
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df['altura'].apply(log))
0     0.582216
1     0.548121
2     0.593327
...
~~~~

#### Convertir una columna al tipo datetime
A menudo una columna contiene cadenas que representan fechas. Para convertir estas cadenas al tipo *datetime* se utiliza el siguiente método:
- *to_datetime(columna, formato)* : Devuelve la serie que resulta de convertir las cadenas de la columna con el nombre *columna* en fechas del tipo *datetime* con el formado especificado en *formato*.
~~~~ python
>>> import pandas as pd
>>> df = pd.DataFrame({'Name': ['María', 'Carlos', 'Carmen'], 'Nacimiento':['05-03-2000', '20-05-2001', '10-12-1999']})
>>> print(pd.to_datetime(df.Nacimiento, format = '%d-%m-%Y'))
0   2000-03-05
1   2001-05-20
2   1999-12-10
Name: Nacimiento, dtype: datetime64[ns]
~~~~

#### Resumen descriptivo de un DataFrame
Al igual que para las series, los siguientes métodos permiten resumir la información de un DataFrame por columnas:
- *df.count()* : Devuelve una serie con el número de elementos que no son nulos ni *NaN* en cada columna del DataFrame *df*.
- *df.sum()* : Devuelve una serie con la suma de los datos de las columnas del DataFrame *df* cuando los datos son de un tipo numérico, o la concatenación de ellos cuando son del tipo cadena *str*.
- *df.cumsum()* : Devuelve un DataFrame con la suma acumulada de los datos de las columnas del DataFrame *df* cuando los datos son de un tipo numérico.
- *df.min()* : Devuelve una serie con los menores de los datos de las columnas del DataFrame *df*.
- *df.max()* : Devuelve una serie con los mayores de los datos de las columnas del DataFrame *df*.
- *df.mean()* : Devuelve una serie con las medias de los datos de las columnas numéricas del DataFrame *df*.
- *df.var()* : Devuelve una serie con las varianzas de los datos de las columnas numéricas del DataFrame *df*.
- *df.std()* : Devuelve una serie con las desviaciones típicas de los datos de las columnas numéricas del DataFrame *df*.
- *df.cov()* : Devuelve un DataFrame con las covarianzas de los datos de las columnas numéricas del DataFrame *df*.
- *df.corr()* : Devuelve un DataFrame con los coeficientes de correlación de Pearson de los datos de las columnas numéricas del DataFrame *df*.
- *df.describe(include = tipo)* : Devuelve un DataFrame con un resumen estadístico de las columnas del DataFrame *df* del tipo *tipo*. Para los datos numéricos (*number*) se calcula la media, la desviación típica, el mínimo, el máximo y los cuartiles. Para los datos no numéricos (*object*) se calcula el número de valores, el número de valores distintos, la moda y su frecuencia. Si no se indica el tipo solo se consideran las columnas numéricas.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>>df.edad.count()  # Tamaño muestral
14
>>> print(df.edad.mean())  # Media
38.214285714285715
>>> print(df.edad.var())  # Varianza
244.02747252747255
>>> print(df.edad.std())  # Desviación típica
15.62137870123737
>>> df.cov()  # Matriz de covarianzas
                  edad        peso    altura   colesterol
edad        244.027473  -69.891026 -0.326593   279.717949
peso        -69.891026  260.076923  1.764615    -2.424242
altura       -0.326593    1.764615  0.013229     0.563269
colesterol  279.717949   -2.424242  0.563269  1587.858974
>>> df.corr()  # Matriz de correlación
                edad      peso    altura  colesterol
edad        1.000000 -0.276185 -0.181774    0.452391
peso       -0.276185  1.000000  0.918984   -0.003621
altura     -0.181774  0.918984  1.000000    0.122694
colesterol  0.452391 -0.003621  0.122694    1.000000
>>> print(df.describe())  # Resumen descriptivo
            edad        peso     altura  colesterol
count  14.000000   13.000000  14.000000   13.000000
mean   38.214286   70.923077   1.768571  220.230769
std    15.621379   16.126901   0.115016   39.847948
min    18.000000   51.000000   1.580000  148.000000
25%    24.750000   61.000000   1.705000  194.000000
50%    35.000000   65.000000   1.755000  210.000000
75%    49.750000   78.000000   1.840000  249.000000
max    68.000000  109.000000   1.980000  280.000000
>>> print(df.describe(include='object'))
                          nombre sexo
count                         14   14
unique                        14    2
top      Antonio Fernández Ocaña    H
freq                           1    8
~~~~

#### Eliminar columnas de un DataFrame
Para eliminar columnas de un DataFrame se utilizan los siguientes métodos:
- *del d[nombre]* : Elimina la columna con nombre *nombre* del DataFrame *df*.
- *df.pop(nombre)* : Elimina la columna con nombre *nombre* del DataFrame *df* y la devuelve como una serie.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> edad = df.pop('edad')
>>> print(df)
                              nombre    sexo  peso  altura    colesterol
0       José Luis Martínez Izquierdo     H    85.0    1.79         182.0
1                     Rosa Díaz Díaz     M    65.0    1.73         232.0
2              Javier García Sánchez     H     
NaN    1.81         191.0
...
print(edad)
0     18
1     32
2     24
...
~~~~

### Operaciones con las filas de un DataFrame
#### Añadir una fila a un DataFrame
Para añadir una fila a un DataFrame se utiliza el siguiente método:
- *df.append(serie, ignore_index=True)* : Devuelve el DataFrame que resulta de añadir una fila al DataFrame *df* con los valores de la serie *serie*. Los nombres del índice de la serie deben corresponderse con los nombres de las columnas de *df*. Si no se pasa el parámetro *ignore_index* entonces debe pasarse el parámetro *name* a la serie, donde su argumento será el nombre de la nueva fila.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> df = df.append(pd.Series(['Carlos Rivas', 28, 'H', 89.0, 1.78, 245.0], index=['nombre','edad','sexo','peso','altura','colesterol']), ignore_index=True)
>>> print(df.tail())
                              nombre  edad sexo    peso  altura    colesterol
10             Macarena Álvarez Luna    53    M    55.0    1.62         262.0
11        José María de la Guía Sanz    58    H    78.0    1.87         198.0
12   Miguel Angel Cuadrado Gutiérrez    27    H   109.0    1.98         210.0
13             Carolina Rubio Moreno    20    M    61.0    1.77         194.0
14                      Carlos Rivas    28    H    89.0    1.78         245.0
~~~~

#### Eliminar filas de un DataFrame
Para eliminar filas de un DataFrame se utilizan el siguiente método:
- *df.drop(filas)* : Devuelve el DataFrame que resulta de eliminar las filas con los nombres indicados en la lista *filas* del DataFrame *df*.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.drop([1, 3]))
                              nombre  edad sexo   peso  altura  colesterol
0       José Luis Martínez Izquierdo    18    H   85.0    1.79       182.0
2              Javier García Sánchez    24    H    NaN    1.81       191.0
4               Marisa López Collado    46    M   51.0    1.58       148.0
...
~~~~

#### Filtrar las filas de un DataFrame
Una operación bastante común con un DataFrame es obtener las filas que cumplen una determinada condición.
- *df[condicion]* : Devuelve un DataFrame con las filas del DataFrame *df* que se corresponden con el valor *\<True>* de la lista booleana *condicion*. *condicion* debe ser una lista de valores booleanos de la misma longitud que el número de filas del DataFrame.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df[(df['sexo']=='H') & (df['colesterol'] > 260)])
                     nombre  edad sexo    peso  altura    colesterol
6   Antonio Fernández Ocaña    51    H    62.0    1.72         276.0
9   Santiago Reillo Manzano    46    H    75.0    1.85         280.0
~~~~

#### Ordenar un DataFrame
Para ordenar un DataFrame de acuerdo a los valores de una determinada columna se utilizan los siguientes métodos:
- *df.sort_values(columna, ascending=booleano)* : Devuelve el DataFrame que resulta de ordenar las filas del DataFrame *df* según los valores del la columna con nombre *columna*. Si argumento del parámetro *ascending* es *\<True>* el orden es creciente y si es *\<False>* decreciente.
- *df.sort_index(ascending=booleano)* : Devuelve el DataFrame que resulta de ordenar las filas del DataFrame *df* según los nombres de las filas. Si el argumento del parámetro *ascending* es *\<True>* el orden es creciente y si es *\<False>* decreciente.
~~~~
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.sort_values('colesterol'))
                              nombre  edad sexo   peso  altura  colesterol
4               Marisa López Collado    46    M   51.0    1.58       148.0
0       José Luis Martínez Izquierdo    18    H   85.0    1.79       182.0
2              Javier García Sánchez    24    H    NaN    1.81       191.0
13             Carolina Rubio Moreno    20    M   61.0    1.77       194.0
...
~~~~

#### Eliminar las filas con dados desconocidos en un DataFrame
Para eliminar las filas de un DataFrame que contienen datos desconocidos *NaN* o nulos None se utiliza el siguiente método:
- *s.dropna(subset=columnas)* : Devuelve el DataFrame que resulta de eliminar las filas que contienen algún dato desconocido o nulo en las columnas de la lista *columna* del DataFrame *df*. Si no se pasa un argumento al parámetro *subset* se aplica a todas las columnas del DataFrame.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.dropna())
                              nombre  edad sexo   peso  altura  colesterol
0       José Luis Martínez Izquierdo    18    H   85.0    1.79       182.0
1                     Rosa Díaz Díaz    32    M   65.0    1.73       232.0
3                Carmen López Pinzón    35    M   65.0    1.70       200.0
4               Marisa López Collado    46    M   51.0    1.58       148.0
...
~~~~

### Agrupación de un DataFrame
En muchas aplicaciones es útil agrupar los datos de un DataFrame de acuerdo a los valores de una o varias columnas (categorías), como por ejemplo el sexo o el país.

![](Fotos/Manual_Python/Libreria_Pandas/Grupos.PNG)

#### Dividir un DataFrame en grupos
Para dividir un DataFrame en grupos se utiliza el siguiente método:
- *df.groupby(columnas).groups* : Devuelve un diccionario con cuyas claves son las tuplas que resultan de todas las combinaciones de los valores de las columnas con nombres en la lista *columnas*, y valores las listas de los nombres de las filas que contienen esos valores en las correspondientes columnas del DataFrame *df*.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.groupby('sexo').groups)
{'H': Int64Index([0, 2, 5, 6, 8, 9, 11, 12], dtype='int64'), 'M': Int64Index([1, 3, 4, 7, 10, 13], dtype='int64')}
>>> print(df.groupby(['sexo','edad']).groups)
{('H', 18): Int64Index([0], dtype='int64'), ('H', 24): Int64Index([2], dtype='int64'), ('H', 27): Int64Index([12], dtype='int64'), ('H', 35): Int64Index([8], dtype='int64'), ('H', 46): Int64Index([9], dtype='int64'), ('H', 51): Int64Index([6], dtype='int64'), ('H', 58): Int64Index([11], dtype='int64'), ('H', 68): Int64Index([5], dtype='int64'), ('M', 20): Int64Index([13], dtype='int64'), ('M', 22): Int64Index([7], dtype='int64'), ('M', 32): Int64Index([1], dtype='int64'), ('M', 35): Int64Index([3], dtype='int64'), ('M', 46): Int64Index([4], dtype='int64'), ('M', 53): Int64Index([10], dtype='int64')}
~~~~

Para obtener un grupo concreto se utiliza el siguiente método:
- *df.groupby(columnas).get_group(valores)* : Devuelve un DataFrame con las filas del DataFrame *df* que cumplen que las columnas de la lista *columnas* presentan los valores de la tupla *valores*. La lista *columnas* y la tupla *valores* deben tener el mismo tamaño.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.groupby('sexo').get_group('M'))
                    nombre  edad sexo    peso   altura    colesterol
1           Rosa Díaz Díaz    32    M    65.0     1.73         232.0
3      Carmen López Pinzón    35    M    65.0     1.70         200.0
4     Marisa López Collado    46    M    51.0     1.58         148.0
7    Pilar Martín González    22    M    60.0     1.66           NaN
10   Macarena Álvarez Luna    53    M    55.0     1.62         262.0
13   Carolina Rubio Moreno    20    M    61.0     1.77         194.0
~~~~

#### Aplicar una función de agregación por grupos
Una vez dividido el DataFame en grupos, es posible aplicar funciones de agregación a cada grupo mediante el siguiente método:
- *df.groupby(columnas).agg(funciones)* : Devuelve un DataFrame con el resultado de aplicar las funciones de agregación de la lista *funciones* a cada uno de los DataFrames que resultan de dividir el DataFrame según las columnas de la lista *columnas*.

Una función de agregación toma como argumento una lista y devuelve una único valor. Algunas de las funciones de agregación más comunes son:
- *np.min* : Devuelve el mínimo de una lista de valores.
- *np.max* : Devuelve el máximo de una lista de valores.
- *np.count_nonzero* : Devuelve el número de valores no nulos de una lista de valores.
- *np.sum* : Devuelve la suma de una lista de valores.
- *np.mean* : Devuelve la media de una lista de valores.
- *np.std* : Devuelve la desviación típica de una lista de valores.
~~~~ python
>>> import pandas as pd
>>> df = pd.read_csv(
'https://raw.githubusercontent.com/asalber/manual-python/master/datos/colesterol.csv')
>>> print(df.groupby('sexo').agg(np.mean))
           edad       peso    altura  colesterol
sexo                                            
H     40.875000  80.714286  1.837500     228.375
M     34.666667  59.500000  1.676667     207.200
~~~~

### Reestructurar un DataFrame
A menudo la disposición de los datos en un DataFrame no es la adecuada para su tratamiento y es necesario reestructurar el DataFrame. Los datos que contiene un DataFrame pueden organizarse en dos formatos: ancho y largo.

![](Fotos/Manual_Python/Libreria_Pandas/FormatosDataframe.PNG)

#### Convertir un DataFrame a formato largo
Para convertir un DataFrame de formato ancho a formato largo (columnas a filas) se utiliza el siguiente método:
- *df.melt(id_vars=id-columnas, value_vars=columnas, var_name=nombre-columnas, var_value=nombre-valores)* : Devuelve el DataFrame que resulta de convertir el DataFrame *df* de formato ancho a formato largo. Todas las columnas de lista *columnas* se reestructuran en dos nuevas columnas con nombres *nombre-columnas* y *nombre-valores* que contienen los nombres de las columnas originales y sus valores, respectivamente. Las columnas en la lista *id-columnas* se mantienen sin reestructurar. Si no se pasa la lista *columnas* entonces se reestructuran todas las columnas excepto las columnas de la lista *id-columnas*.
~~~~ python
>>> import pandas as pd
>>> datos = {'nombre':['María', 'Luis', 'Carmen'],
... 'edad':[18, 22, 20],
... 'Matemáticas':[8.5, 7, 3.5],
... 'Economía':[8, 6.5, 5],
... 'Programación':[6.5, 4, 9]}
>>> df = pd.DataFrame(datos)
>>> df1 = df.melt(id_vars=['nombre', 'edad'], var_name='asignatura', value_name='nota')
>>> print(df1)
   nombre  edad    asignatura  nota
0   María    18   Matemáticas   8.5
1    Luis    22   Matemáticas   7.0
2  Carmen    20   Matemáticas   3.5
3   María    18      Economía   8.0
4    Luis    22      Economía   6.5
5  Carmen    20      Economía   5.0
6   María    18  Programación   6.5
7    Luis    22  Programación   4.0
8  Carmen    20  Programación   9.0
~~~~

#### Convertir un DataFrame a formato ancho
Para convertir un DataFrame de formato largo a formato ancho (filas a columnas) se utiliza el siguiente método:
- *df.pivot(index=filas, columns=columna, values=valores)* : Devuelve el DataFrame que resulta de convertir el DataFrame *df* de formato largo a formato ancho. Se crean tantas columnas nuevas como valores distintos haya en la columna *columna*. Los nombres de estas nuevas columnas son los valores de la columna *columna* mientras que sus valores se toman de la columna *valores*. Los nombres del índice del nuevo DataFrame se toman de los valores de la columna *filas*.
~~~~ python
# Continuación del código anterior
>>> print(df1.pivot(index='nombre', columns='asignatura', values='nota'))
asignatura  Economía  Matemáticas  Programación
nombre                                  
Carmen           5.0          3.5           9.0
Luis             6.5          7.0           4.0
María            8.0          8.5           6.5
~~~~

### Combinar varios DataFrames
Dos o más DataFrames pueden combinarse en otro DataFrame. La combinación puede ser de varias formas:
- **Concatenación** : Combinación de varios DataFrames concatenando sus filas o columnas.
- **Mezcla** : Combinación de varios DataFrames usando columnas o índices comunes.

#### Concatenación de DataFrames
- **Concatenación de filas**. Las filas de los DataFrames se concatenan unas a continuación de las otras para formar el nuevo DataFrame. Para ello es necesario que los DataFrames que se combinen tengan el mismo índice de columnas.

![](Fotos/Manual_Python/Libreria_Pandas/ConcatenacionFilas.PNG)

- **Concatenación de columnas**. Las columnas de los DataFrames se concatenan unas a continuación de las otras para formar el nuevo DataFrame. Para ello es necesario que los DataFrames que se combinen tengan el mismo índice de filas.

![](Fotos/Manual_Python/Libreria_Pandas/ConcatenacionColumnas.PNG)

Para concatenar dos o más DataFrames se utiliza el siguiente método:
- *df.concat(dataframes, axis = eje)* : Devuelve el DataFrame que resulta de concatenar los DataFrames de la lista *dataframes*. Si eje es *0* (valor por defecto) la concatenación se realiza por filas, y si *eje* es 1 se realiza por columnas.

> ⚠️ Si los DataFrames que se concatenan por filas no tienen el mismo índice de columnas, el DataFrame resultante incluirá todas las columnas existentes en los DataFrames y rellenará con valores *NaN* los datos no disponibles. Si los DataFrames que se concatenan por columnas no tienen el mismo índice de filas, el DataFrame resultante incluirá todas las filas existentes en los DataFrames y rellenará con valores *NaN* los datos no disponibles.

~~~~ python
>>> import pandas as pd
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis"], 
... "Sexo":["Mujer", "Hombre"], "Edad":[22, 18]}).set_index("Nombre")
>>> df2 = pd.DataFrame({"Nombre":["María", "Pedro"], 
... "Sexo":["Mujer", "Hombre"], "Edad":[25, 30]}).set_index("Nombre")
>>> df = pd.concat([df1, df2])
>>> df
          Sexo  Edad
Nombre              
Carmen   Mujer    22
Luis    Hombre    18
María    Mujer    25
Pedro   Hombre    30
~~~~
~~~~ python
>>> import pandas as pd
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"], 
... "Sexo":["Mujer", "Hombre", "Mujer"]}).set_index("Nombre")
>>> df2 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"], 
... "Edad":[22, 18, 25]}).set_index("Nombre")
>>> df = pd.concat([df1, df2], axis = 1)
>>> df
          Sexo  Edad
Nombre              
Carmen   Mujer    22
Luis    Hombre    18
María    Mujer    25
~~~~

#### Mezcla de DataFrames
La mezcla de DataFrames permite integrar filas de dos DataFrames que contienen información en común en una o varias columnas o índices que se conocen como clave.

Para mezclar dos DataFrames se utiliza el siguiente método:
- *df.merge(df1, df2, on = clave, how = tipo)* : Devuelve el DataFrame que resulta de mezclar el DataFrame *df2* con el DataFrame *df1*, usando como claves las columnas de la lista *clave* y siguiendo el método de mezcla indicado por *tipo*.

El tipo de mezcla puede ser
- *"inner"* (por defecto) : El DataFrame resultante solo contiene las filas cuyos valores en la clave están en los dos DataFrames. Es equivalente a la intersección de conjuntos.
~~~~ python
>>> import pandas as pd
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"],  "Sexo":["Mujer", "Hombre", "Mujer"]})
>>> df2 = pd.DataFrame({"Nombre":["María", "Pedro", "Luis"], "Edad":[25, 30, 18]]})
>>> df = pd.merge(df1, df2, on="Nombre")
>>> print(df)
  Nombre    Sexo  Edad
0   Luis  Hombre    18
1  María   Mujer    25
~~~~

- *"outer"* : El DataFrame resultante contiene todas las filas de los dos DataFrames. Si una fila de un DataFrame no puede emparejarse con otra los mismos valores en la clave en el otro DataFrame, la fila se añade igualmente al DataFrame resultante rellenando las columnas del otro DataFrame con el valor *NaN*. Es equivalente a la unión de conjuntos.
~~~~ python
>>> import pandas as pd
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"],  "Sexo":["Mujer", "Hombre", "Mujer"]})
>>> df2 = pd.DataFrame({"Nombre":["María", "Pedro", "Luis"], "Edad":[25, 30, 18]]})
>>> df = pd.merge(df1, df2, on="Nombre", how="outer")
>>> print(df)
   Nombre    Sexo  Edad
0  Carmen   Mujer   NaN
1    Luis  Hombre  18.0
2   María   Mujer  25.0
3   Pedro     NaN  30.0
~~~~

- *"left"* : El DataFrame resultante contiene todas las filas del primer DataFrame y descarta las filas del segundo DataFrame que no pueden emparejarse con alguna fila del primer DataFrame a través de la clave.
~~~~ python
>>> import pandas as pd
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"],  "Sexo":["Mujer", "Hombre", "Mujer"]})
>>> df2 = pd.DataFrame({"Nombre":["María", "Pedro", "Luis"], "Edad":[25, 30, 18]]})
>>> df = pd.merge(df1, df2, on="Nombre", how="left")
>>> print(df)
   Nombre    Sexo  Edad
0  Carmen   Mujer   NaN
1    Luis  Hombre  18.0
2   María   Mujer  25.0
~~~~ 

- *"right"* : El DataFrame resultante contiene todas las filas del segundo DataFrame y descarta las filas del primer DataFrame que no pueden emparejarse con alguna fila del segundo DataFrame a través de la clave.
~~~~ python
>>> import pandas as pd
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"],  "Sexo":["Mujer", "Hombre", "Mujer"]})
>>> df2 = pd.DataFrame({"Nombre":["María", "Pedro", "Luis"], "Edad":[25, 30, 18]]})
>>> df = pd.merge(df1, df2, on="Nombre", how="right")
>>> print(df)
  Nombre    Sexo  Edad
0  María   Mujer    25
1  Pedro     NaN    30
2   Luis  Hombre    18
~~~~ 

## Librería Matplotlib
---
[Matplotlib](https://matplotlib.org/) es una librería de Python especializada en la creación de gráficos en dos dimensiones.

![](Fotos/Manual_Python/Libreria_Matplotlib/MatplotlibLogo.PNG)

Permite crear y personalizar los tipos de gráficos más comunes, entre ellos:
- Diagramas de barras
- Histograma
- Diagramas de sectores
- Diagramas de caja y bigotes
- Diagramas de violín
- Diagramas de dispersión o puntos
- Diagramas de lineas
- Diagramas de areas
- Diagramas de contorno
- Mapas de color

y combinaciones de todos ellos.

En la siguiente [galería de gráficos](https://matplotlib.org/gallery/index.html) pueden apreciarse todos los tipos de gráficos que pueden crearse con esta librería.

### Creación de gráficos con matplotlib
Para crear un gráfico con matplotlib es habitual seguir los siguientes pasos:
1. Importar el módulo *pyplot*.
2. Definir la figura que contendrá el gráfico, que es la region (ventana o página) donde se dibujará y los ejes sobre los que se dibujarán los datos. Para ello se utiliza la función *subplots()*.
3. Dibujar los datos sobre los ejes. Para ello se utilizan distintas funciones dependiendo del tipo de gráfico que se quiera.
4. Personalizar el gráfico. Para ello existen multitud de funciones que permiten añadir un título, una leyenda, una rejilla, cambiar colores o personalizar los ejes.
5. Guardar el gráfico. Para ello se utiliza la función *savefig()*.
6. Mostrar el gráfico. Para ello se utiliza la función *show()*.
~~~~ python
# Importar el módulo pyplot con el alias plt
import matplotlib.pyplot as plt
# Crear la figura y los ejes
fig, ax = plt.subplots()
# Dibujar puntos
ax.scatter(x = [1, 2, 3], y = [3, 2, 1])
# Guardar el gráfico en formato png
plt.savefig('diagrama-dispersion.png')
# Mostrar el gráfico
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/DiagramaDispersion.PNG)

### Diagramas de dispersión o puntos
- *scatter(x, y)* : Dibuja un diagrama de puntos con las coordenadas de la lista *x* en el eje X y las coordenadas de la lista *y* en el eje Y. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.scatter.html#matplotlib.pyplot.scatter)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.scatter([1, 2, 3, 4], [1, 2, 0, 0.5])
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/DiagramaPuntos.PNG)

### Diagramas de líneas
- *plot(x, y)* : Dibuja un polígono con los vértices dados por las coordenadas de la lista *x* en el eje X y las coordenadas de la lista *y* en el eje Y. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.plot.html#matplotlib.pyplot.plot)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.plot([1, 2, 3, 4], [1, 2, 0, 0.5])
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/DiagramaLineas.PNG)

### Diagramas de areas
- *fill_between(x, y)* : Dibuja el area bajo el polígono con los vértices dados por las coordenadas de la lista *x* en el eje X y las coordenadas de la lista *y* en el eje Y. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.fill_between.html#matplotlib.pyplot.fill_between)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.fill_between([1, 2, 3, 4], [1, 2, 0, 0.5])
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/DiagramaAreas.PNG)

### Diagramas de barras verticales
- *bar(x, y)* : Dibuja un diagrama de barras verticales donde *x* es una lista con la posición de las barras en el eje X, e *y* es una lista con la altura de las barras en el eje Y. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.bar.html#matplotlib.pyplot.bar)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.bar([1, 2, 3], [3, 2, 1])
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/DiagramaBarras.PNG)

### Diagramas de barras horizontales
- *barh(x, y)* : Dibuja un diagrama de barras horizontales donde *x* es una lista con la posición de las barras en el eje Y, e *y* es una lista con la longitud de las barras en el eje X. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.barh.html#matplotlib.pyplot.barh)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.barh([1, 2, 3], [3, 2, 1])
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/DiagramaBarrasHorizontales.PNG)

### Histogramas
- *hist(x, bins)* : Dibuja un histograma con las frecuencias resultantes de agrupar los datos de la lista *x* en las clases definidas por la lista *bins*. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.hist.html#matplotlib.pyplot.hist)
~~~~ python
import numpy as np
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
x = np.random.normal(5, 1.5, size=1000)
ax.hist(x, np.arange(0, 11))
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/Histograma.PNG)

### Diagramas de sectores
- *pie(x)* : Dibuja un diagrama de sectores con las frecuencias de la lista *x*. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.pie.html#matplotlib.pyplot.pie)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.pie([5, 4, 3, 2, 1])
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/DiagramaSectores.PNG)

### Diagramas de caja y bigotes
- *boxplot(x)* : Dibuja un diagrama de caja y bigotes con los datos de la lista *x*. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.boxplot.html#matplotlib.pyplot.boxplot)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.boxplot([1, 2, 1, 2, 3, 4, 3, 3, 5, 7])
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/DiagramaCaja.PNG)

### Diagramas de violín
- *violinplot(x)* : Dibuja un diagrama de violín con los datos de la lista x. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.violinplot.html#matplotlib.pyplot.violinplot)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.violinplot([1, 2, 1, 2, 3, 4, 3, 3, 5, 7])
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/DiagramaViolin.PNG)

### Diagramas de contorno
- *contourf(x, y, z)* : Dibuja un diagrama de contorno con las curvas de nivel de la superficie dada por los puntos con las coordenadas de las listas *x*, *y* y *z* en los ejes X, Y y Z respectivamente. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.contourf.html#matplotlib.pyplot.contourf)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
x = np.linspace(-3.0, 3.0, 100)
y = np.linspace(-3.0, 3.0, 100)
x, y = np.meshgrid(x, y)
z = np.sqrt(x**2 + 2*y**2)
ax.contourf(x, y, z)
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/DiagramaContorno.PNG)

### Mapas de color
- *imshow(x)* : Dibuja un mapa de color a partir de una matriz (array bidimensiona) *x*. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.imshow.html#matplotlib.pyplot.imshow)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
x = np.random.random((16, 16))
ax.imshow(x)
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/MapaColor.PNG)

- *hist2d(x, y)* : Dibuja un mapa de color que simula un histograma bidimensional, donde los colores de los cuadrados dependen de las frecuencias de las clases de la muestra dada por las listas *x* e *y*. [ℹ️](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.hist2d.html#matplotlib.pyplot.hist2d)
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
x, y = np.random.multivariate_normal(mean=[0.0, 0.0], cov=[[1.0, 0.4], [0.4, 0.5]], size=1000).T
ax.hist2d(x, y)
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/Histograma2D.PNG)

### Cambiar el aspecto de los gráficos
Los gráficos creados con Matplotlib son personalizables y puede cambiarse el aspecto de casi todos sus elementos. Los elementos que suelen modificarse más a menudo son:
- Colores
- Marcadores de puntos
- Estilo de líneas
- Títulos
- Ejes
- Leyenda
- Rejilla

#### Colores
Para cambiar el color de los objetos se utiliza el parámetro *color = nombre-color*, donde *nombre-color* es una cadena con el nombre del color de entre los [colores disponibles](https://matplotlib.org/3.2.1/gallery/color/named_colors.html).
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
dias = ['L', 'M', 'X', 'J', 'V', 'S', 'D']
temperaturas = {'Madrid':[28.5, 30.5, 31, 30, 28, 27.5, 30.5], 'Barcelona':[24.5, 25.5, 26.5, 25, 26.5, 24.5, 25]}
ax.plot(dias, temperaturas['Madrid'], color = 'tab:purple')
ax.plot(dias, temperaturas['Barcelona'], color = 'tab:green')
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/LineasColores.PNG)

#### Marcadores
Para cambiar la forma de los puntos marcadores se utiliza el parámetro *marker = nombre-marcador* donde *nombre-marcador* es una cadena con el nombre del marcador de entre los [marcadores disponibles](https://matplotlib.org/3.2.1/api/markers_api.html).
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
dias = ['L', 'M', 'X', 'J', 'V', 'S', 'D']
temperaturas = {'Madrid':[28.5, 30.5, 31, 30, 28, 27.5, 30.5], 'Barcelona':[24.5, 25.5, 26.5, 25, 26.5, 24.5, 25]}
ax.plot(dias, temperaturas['Madrid'], marker = '^')
ax.plot(dias, temperaturas['Barcelona'], marker = 'o')
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/LineasMarcadores.PNG)

#### Líneas
Para cambiar el estilo de las líneas se utiliza el parámetro *linestyle = nombre-estilo* donde *nombre-estilo* es una cadena con el nombre del estilo de entre los [estilos disponibles](https://matplotlib.org/3.2.1/gallery/lines_bars_and_markers/linestyles.html).
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
dias = ['L', 'M', 'X', 'J', 'V', 'S', 'D']
temperaturas = {'Madrid':[28.5, 30.5, 31, 30, 28, 27.5, 30.5], 'Barcelona':[24.5, 25.5, 26.5, 25, 26.5, 24.5, 25]}
ax.plot(dias, temperaturas['Madrid'], linestyle = 'dashed')
ax.plot(dias, temperaturas['Barcelona'], linestyle = 'dotted')
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/LineasEstilo.PNG)                        
                           
#### Títulos
Para añadir un título principal al gráfico se utiliza el siguiente método:
- *ax.set_title(titulo, loc=alineacion, fontdict=fuente)* : Añade un título con el contenido de la cadena *titulo* a los ejes *ax*. El parámetro *loc* indica la alineación del título, que puede ser *'left'* (izquierda), *'center'* (centro) o *'right'* (derecha), y el parámetro *fontdict* indica mediante un diccionario las características de la fuente (la el tamaño *fontisize*, el grosor *fontweight* o el color *color*).
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
dias = ['L', 'M', 'X', 'J', 'V', 'S', 'D']
temperaturas = {'Madrid':[28.5, 30.5, 31, 30, 28, 27.5, 30.5], 'Barcelona':[24.5, 25.5, 26.5, 25, 26.5, 24.5, 25]}
ax.plot(dias, temperaturas['Madrid'])
ax.plot(dias, temperaturas['Barcelona'])
ax.set_title('Evolución de la temperatura diaria', loc = "left", fontdict = {'fontsize':14, 'fontweight':'bold', 'color':'tab:blue'})
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/Titulo.PNG)

#### Ejes
Para cambiar el aspecto de los ejes se suelen utilizar los siguientes métodos:
- *ax.set_xlabel(titulo)* : Añade un título con el contenido de la cadena *titulo* al eje x de *ax*. Se puede personalizar la alineación y la fuente con los mismos parámetros que para el título principal.
- *ax.set_ylabel(titulo)* : Añade un título con el contenido de la cadena *titulo* al eje y de *ax*. Se puede personalizar la alineación y la fuente con los mismos parámetros que para el título principal.
- *ax.set_xlim([limite-inferior, limite-superior])* : Establece los límites que se muestran en el eje x de *ax*.
- *ax.set_ylim([limite-inferior, limite-superior])* : Establece los límites que se muestran en el eje y de *ax*.
- *ax.set_xticks(marcas)* : Dibuja marcas en el eje x de *ax* en las posiciones indicadas en la lista *marcas*.
- *ax.set_yticks(marcas)* : Dibuja marcas en el eje y de *ax* en las posiciones indicadas en la lista *marcas*.
- *ax.set_xscale(escala)* : Establece la escala del eje x de *ax*, donde el parámetro *escala* puede ser *'linear'* (lineal) o *'log'* (logarítmica).
- *ax.set_yscale(escala)* : Establece la escala del eje y de *ax*, donde el parámetro *escala* puede ser *'linear'* (lineal) o *'log'* (logarítmica).
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
dias = ['L', 'M', 'X', 'J', 'V', 'S', 'D']
temperaturas = {'Madrid':[28.5, 30.5, 31, 30, 28, 27.5, 30.5], 'Barcelona':[24.5, 25.5, 26.5, 25, 26.5, 24.5, 25]}
ax.plot(dias, temperaturas['Madrid'])
ax.plot(dias, temperaturas['Barcelona'])
ax.set_xlabel("Días", fontdict = {'fontsize':14, 'fontweight':'bold', 'color':'tab:blue'})
ax.set_ylabel("Temperatura ºC")
ax.set_ylim([20,35])
ax.set_yticks(range(20, 35))
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/Ejes.PNG)

#### Leyenda
Para añadir una leyenda a un gráfico se utiliza el siguiente método:

- *ax.legend(leyendas, loc = posición)* : Dibuja un leyenda en los ejes *ax* con los nombres indicados en la lista *leyendas*. El parámetro *loc* indica la posición en la que se dibuja la leyenda y puede ser: 
    + *'upper left'* (arriba izquierda)
    + *'upper center'* (arriba centro)
    + *'upper right'* (arriba derecha)
    + *'center left'* (centro izquierda)
    + *'center'* (centro)
    + *'center right'* (centro derecha)
    + *'lower left'* (abajo izquierda)
    + *'lower center'* (abajo centro)
    + *'lower right'* (abajo derecha). 
> ⚠️ Se puede omitir la lista *leyendas* si se indica la leyenda de cada serie en la función que la dibuja mediante el parámetro *label*.
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
dias = ['L', 'M', 'X', 'J', 'V', 'S', 'D']
temperaturas = {'Madrid':[28.5, 30.5, 31, 30, 28, 27.5, 30.5], 'Barcelona':[24.5, 25.5, 26.5, 25, 26.5, 24.5, 25]}
ax.plot(dias, temperaturas['Madrid'], label = 'Madrid')
ax.plot(dias, temperaturas['Barcelona'], label = 'Barcelona')
ax.legend(loc = 'upper right')
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/Leyenda.PNG)

#### Rejilla
- *ax.grid(axis=ejes, color=color, linestyle=estilo)* : Dibuja una rejilla en los ejes de *ax*. El parámetro *axis* indica los ejes sobre los que se dibuja la regilla y puede ser *'x'* (eje x), *'y'* (eje y) o *'both'* (ambos). Los parámetros *color* y *linestyle* establecen el color y el estilo de las líneas de la rejilla, y pueden tomar los mismos valores vistos en los apartados de colores y líneas.
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
dias = ['L', 'M', 'X', 'J', 'V', 'S', 'D']
temperaturas = {'Madrid':[28.5, 30.5, 31, 30, 28, 27.5, 30.5], 'Barcelona':[24.5, 25.5, 26.5, 25, 26.5, 24.5, 25]}
ax.plot(dias, temperaturas['Madrid'])
ax.plot(dias, temperaturas['Barcelona'])
ax.grid(axis = 'y', color = 'gray', linestyle = 'dashed')
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/Rejilla.PNG)

### Múltiples gráficos
Es posible dibujar varios gráficos en distintos ejes en una misma figura organizados en forma de tabla. Para ello, cuando se inicializa la figura y los ejes, hay que pasarle a la función *subplots* el número de filas y columnas de la tabla que contendrá los gráficos. Con esto los distintos ejes se organizan en un array y se puede acceder a cada uno de ellos a través de sus índices. Si se quiere que los distintos ejes compartan los mismos límites para los ejes se pueden pasar los parámetros *sharex = True* para el eje x o *sharey = True* para el eje y.
~~~~ python
import matplotlib.pyplot as plt
fig, ax = plt.subplots(2, 2, sharey = True)
dias = ['L', 'M', 'X', 'J', 'V', 'S', 'D']
temperaturas = {'Madrid':[28.5, 30.5, 31, 30, 28, 27.5, 30.5], 'Barcelona':[24.5, 25.5, 26.5, 25, 26.5, 24.5, 25]}
ax[0, 0].plot(dias, temperaturas['Madrid'])
ax[0, 1].plot(dias, temperaturas['Barcelona'], color = 'tab:orange')
ax[1, 0].bar(dias, temperaturas['Madrid'])
ax[1, 1].bar(dias, temperaturas['Barcelona'], color = 'tab:orange')
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/MultiplesGraficos.PNG)

### Integración con Pandas
Matplotlib se integra a la perfección con la librería Pandas, permitiendo dibujar gráficos a partir de los datos de las series y DataFrames de Pandas.
- *df.plot(kind=tipo, x=columnax, y=columnay, ax=ejes)* : Dibuja un diagrama del tipo indicado por el parámetro *kind* en los ejes indicados en el parámetro *ax*, representando en el eje x la columna del parámetro *x* y en el eje y la columna del parámetro *y*. El parámetro *kind* puede tomar como argumentos:
    + *'line'* (lineas)
    + *'scatter'* (puntos)
    + *'bar'* (barras verticales)
    + *'barh'* (barras horizontales)
    + *'hist'* (histograma)
    + *'box'* (cajas)
    + *'density'* (densidad)
    + *'area'* (area)
    + *'pie'* (sectores). 
> ⚠️ Es posible pasar otros parámetros para indicar el color, el marcador o el estilo de línea como se vió en los apartados anteriores.
~~~~ python
import pandas as pd 
import matplotlib.pyplot as plt
df = pd.DataFrame({'Días':['L', 'M', 'X', 'J', 'V', 'S', 'D'], 
                   'Madrid':[28.5, 30.5, 31, 30, 28, 27.5, 30.5], 
                   'Barcelona':[24.5, 25.5, 26.5, 25, 26.5, 24.5, 25]})
fig, ax = plt.subplots()
df.plot(x = 'Días', y = 'Madrid', ax = ax)
df.plot(x = 'Días', y = 'Barcelona', ax = ax)
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/MatplotlibPandas.PNG)

Si no se indican los parámetros *x* e *y* se representa el índice de las filas en el eje x y una serie por cada columna del Dataframe. Las columnas no numéricas se ignoran.
~~~~ python
import pandas as pd 
import matplotlib.pyplot as plt
df = pd.DataFrame({'Días':['L', 'M', 'X', 'J', 'V', 'S', 'D'], 
                   'Madrid':[28.5, 30.5, 31, 30, 28, 27.5, 30.5], 
                   'Barcelona':[24.5, 25.5, 26.5, 25, 26.5, 24.5, 25]})
df = df.set_index('Días')
fig, ax = plt.subplots()
df.plot(ax = ax)
plt.show()
~~~~

![](Fotos/Manual_Python/Libreria_Matplotlib/MatplotlibPandas_2.PNG)

## Librería itertools
---
Este módulo implementa un número de piezas básicas iterator inspiradas en constructs de *APL*, *Haskell* y *SML*.

~~~~ python
import itertools
~~~~

> ⚠️ Si queremos acceder a los valores de un iterador debemos hacerlo secuencialmente con el comando *next(iterador)*.

### Iteradores infinitos
- *count(i, s)* : Crea un iterador de una progresión aritmética con una diferencia *s* comenzando desde el valor *i*. Si no se especifica ninguno de los dos parámetros toma por valores predeterminados *count(i=0, s=1)*.
- *cycle(data)* : Crea un iterador de copias cíclicas de los elementos de *data* (listas, tuplas, diccionarios, textos).
- *repeat(elem, n)* : Crea un iterador del mismo objeto *elem* infinítamente si no se especifica un límite *n*.

~~~~ python
count(2)       #  2  3  4  5  6 ...
count(10, 5)   # 10 15 20 25 30 ...
count(1, 0.5)  # 1 1.5 2.0 2.5  ...

cycle('XYZ')   #  X  Y  Z  X  Y ...

repeat(9)      #  9  9  9  9  9 ...
repeat('1', 3) #  1  1  1
~~~~

### Iteradores con la entrada más corta
- *accumulate(data, func, i)* : Crea un iterador que devuelve sumas acumuladas. En caso de querer una acumulación con otra función (de 2 argumentos) se debe especificar *func*. También se puede especificar el valor inicial *i*.
- *batched(data, n)* : Crea un iterador que devuelve grupos de *n* elementos del iterable *data*. Si el valor *strict* se pone a *\<True>* el último grupo deberá ser del mismo tamaño que *n*, sino se devolverá un *ValueError*.
- *chain(*datas)* : Crea un iterador que retorna elementos del primer iterable hasta que es consumido, para luego proceder con el siguiente iterable hasta el último.
- *chain.from_iterable(data)* : Constructor alternativo para *chain()*. Crea un iterador que retorna elementos de cada elemento del iterable *data*.
- *compress(data, filter)* : Crea un iterador con los elementos de *data* correspondientes a *\<True>* en el filtro *filter*.
- *dropwhile(c, data)* : Crea un iterador que descarta los elementos del iterable *data* mientras la condición *c* sea verdadera. A partir del elemento que deje de cumplir la condición, devuelve el resto de la lista.
- *takewhile(c, data)* : Crea un iterador que retorna los elementos del iterable *data* mientras la condición *c* sea verdadera. A partir del elemento que deje de cumpliar la condición, para de devolver.
- *filterfalse(c, data)* : Crea un iterador que descarta los elementos del iterable *data* que devuelvan *\<False>* para la condición *c*.
- *groupby(data)* : Crea un iterador que retorna claves consecutivas y grupos del iterable *data*. Genera un salto o un nuevo grupo cada vez que el valor de la función clave cambia. 
- *islice(data, f)* / *islice(data, i, f, s)* : Crea un iterador que retorna los elementos seleccionados del iterable *data* (no admite valores negativos para *i*, *f* y *s*).
- *pairwise(data)* : Crea un iterador de pares superpuestos consecutivos del iterable *data*. Si el iterable tiene menos de 2 elementos, la salida estára vacía.
- *starmap(func, data)* : Crea un iterador que calcula la función *func* usando argumentos obtenidos del iterable *data*.
- *zip_longest(\*datas, fill)* : Crea un iterador agrupando elementos de los iterables *datas* con la misma posición. Para los elementos faltantes en un grupo al haberse terminado el correspondiente iterable, se rellena con el valor *fill* (valor predeterminado: *\<None>*).

~~~~ python
accumualte([1, 2, 3, 4, 5])                    # 1 3 6 10 15
accumulate([6, 5, 4, 3, 2], operator.mul)      # 6 30 120 360 720
accumulate(['o', 'l', 'a'], initial='H')       # H Ho Hol Hola

batched('ABCDEFG', 3)                          # ABC DEF G

chain('ABC', 'DEF')                            # A B C D E F
chain.from_iterable(['ABC', 'DEF'])            # A B C D E F

compress('ABCDEF', [1, 0, 1, 0, 1, 1])         # A C E F
compress([1, 2, 3], [False, True, True])       # 2 3

dropwhile(lambda x: x<5, [1, 4, 6, 4, 1])      # 6 4 1
takewhile(lambda x: x<5, [1, 4, 6, 4, 1])      # 1 4

filterfalse(lambda x: x%2, range(10))          # 0 2 4 6 8

[k for k, g in groupby('AAAABBBCCDAABBB')]     # A B C D A B      
[''.join(g) for k, g in groupby('AAAABBBCCD')] # AAAA BBB CC D

islice('ABCDEFG', 2)                           # A B
islice('ABCDEFG', 2, 4)                        # C D
islice('ABCDEFG', 2, None)                     # C D E F G
islice('ABCDEFG', 0, None, 2)                  # A C E G

pairwise('ABCDEFG')                            # AB BC CD DE EF FG

starmap(pow, [(2,5), (3,2), (10,3)])           # 32 9 1000

zip_longest('ABCD', 'xy', fillvalue='-')       # Ax By C- D-
~~~~

### Iteradores combinatorios
- *product(\*datas)* / *product(data, n)* : Crea un iterador a partir del producto cartesiano de los iterables *datas*. Para calcular el producto de un iterable consigo mismo, se especifica el número de repeticiones con el argumento opcional *n*.
- *permutations(data, d)* : Crea un iterador de permutaciones sucesivas de longitud *d* (valor predeterminado: longitud del iterable) de elementos del iterable *data*. 
- *combinations(data, d)* : Crea un iterador de subsecuencias de longitud *n* con elementos del iterable *data*.
- *combinations_with_replacement(data, d)* : Crea un iterador de subsecuencias de longitud *n* con elementos del iterable *data* permitiendo que haya elementos repetidos.

~~~~ python
product('ABCD', 'xy')                      # Ax Ay Bx By Cx Cy Dx Dy
product(range(2), repeat=3)                # 000 001 010 011 100 101 110 111

permutations('ABCD', 2)                    # AB AC AD BA BC BD CA CB CD DA DB DC
permutations(range(3))                     # 012 021 102 120 201 210

combinations('ABCD', 2)                    # AB AC AD BC BD CD
combinations(range(4), 3)                  # 012 013 023 123

combinations_with_replacement('ABCD', 2)   # AA AB AC AD BB BC BD CC CD DD
combinations_with_replacement(range(3), 3) # 000 001 002 011 012 022 111 112 122 222
~~~~
### 

## Librería Turtle
---
La "tortuga" es un cursor al que se le pueden dar órdenes de movimiento (avance, retroceso o giro) y que puede ir dejando un rastro sobre la pantalla. Moviendo adecuadamente la tortuga se pueden conseguir dibujar todo tipo de figuras.

Python incluye un módulo llamado "turtle" que permite crear gráficos de tortuga.
~~~~ python
import turtle
~~~~

### Ventana
- *setup(ancho, alto, posicionX, posicionY)* : Permite definir el tamaño y la posición inicial de la ventana. Todas las medidas en píxeles.
> ⚠️ Los valores positivos de la posición se miden desde la parte superior izquierda de la pantalla, los negativos desde la parte inferior derecha.
~~~~ python
turtle.setup(400,400,100,100)
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Setup.PNG)

> ⚠️ Si no se usa la función *setup()*, la ventana se crea en el centro de la pantalla (para que se cree la ventana tiene que aparecer alguna función del módulo turtle):

> ⚠️ El tamaño de la ventana de dibujo se puede modificar a lo largo de un programa, sin que se pierda el dibujo realizado anteriormente.
- *title()* : Permite definir el título de la ventana, que se muestra en el borde superior de la ventana.
~~~~ python
turtle.title("Titulo")
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Titulo.PNG)

- *screensize(ancho, alto)* : Permite definir el tamaño del área de dibujo, en píxeles. De forma predeterminada tiene un tamaño de *400x300* píxeles.
> ⚠️ El tamaño del área de dibujo se puede modificar a lo largo de un programa, sin que se pierda el dibujo realizado anteriormente.

### Dibujar
Dibujar gráficos de tortuga es similar a dibujar con un lápiz sobre papel. Las instrucciones de gráficos de tortuga permiten dibujar líneas y puntos, mover el lápiz de un sitio a otro, cambiar el color y grosor del trazo, colorear el interior de las figuras, etc.

Las posiciones en el área de dibujo se localizan mediante coordenadas XY en el que cada píxel es una unidad y con origen en el centro de la ventana.

![](Fotos/Manual_Python/Libreria_Turtle/Ejes.PNG)

- *showturle()* : Muestra el cursor en pantalla. Al crear la ventana, el cursor se sitúa en el centro de la ventana, de coordenadas (0, 0).
~~~~ python
turtle.showturle()
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Showturtle.PNG)

- *hideturtle()* : Oculta el cursor en pantalla.

- *goto(x, y)* : Permite desplazar el cursor a una posición determinada del área de dibujo.
~~~~ python
turtle.setup(450, 200, 0, 0)
turtle.screensize(300, 150)

turtle.goto(100,50)
turtle.goto(100,-50)
turtle.goto(50,-50)
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Goto_1.PNG)

- *setx(), sety()* : Permiten desplazar el cursor a una posición determinada del área de dibujo modificando la abcisa y la ordenada respectivamente.
~~~~ python
turtle.goto(100, 50)
turtle.sety(-50)
turtle.setx(50)
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Goto_1.PNG)

- *pendown(), penup()* : Son equivalentes a bajar y levantar el lápiz del papel. Una vez levantado el lápiz del papel, al desplazar el lápiz ya no se dibujan segmentos.
~~~~ python
turtle.goto(100, 50)
turtle.penup()
turtle.goto(100, -50)
turtle.pendown()
turtle.goto(50, -50)
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Goto_2.PNG)

- *pensize()* : Permite modificar el grosor del trazo.
~~~~ python
turtle.goto(100, 50)
turtle.pensize(4)
turtle.goto(100, -50)
turtle.pensize(8)
turtle.goto(50, -50)
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Pensize.PNG)

- *pencolor(rojo, azul verde)* : Permite modificar el color del trazo. El color se da como combinación de rojo, azul y verde. Los valores de color se pueden dar como valores enteros entre 0 y 255 o como valores decimales entre 0 y 1. Para elegir entre un modo y otro de indicar los colores hay que utilizar la función *colormode(1)* o *colormode(255)*.
~~~~ python
turtle.colormode(255)

turtle.pencolor(255, 0, 0)
turtle.goto(100, 50)
turtle.pencolor(0, 255, 0)
turtle.goto(100, -50)
turtle.pencolor(0, 0, 255)
turtle.goto(50, -50)
~~~~
~~~~ python
turtle.colormode(1)

turtle.pencolor(1, 0, 0)
turtle.goto(100, 50)
turtle.pencolor(0, 1, 0)
turtle.goto(100, -50)
turtle.pencolor(0, 0, 1)
turtle.goto(50, -50)
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Pencolor.PNG)

> ⚠️ También se pueden utilizar los [nombres de colores de Tk](https://www.mclibre.org/consultar/python/lecciones/python-tk-colores.html), que incluyen entre otros los nombres de colores *SVG*, en cuyo caso no hace falta utilizar la función *colormode()*.
> ~~~~ python
> pencolor("red")
> goto(100, 50)
> pencolor("green")
> goto(100, -50)
> pencolor("blue")
> goto(50, -50)
> ~~~~

- *dot(grosor, color)* : Permite dibujar un punto del grosor y color indicado en el punto en el que se encuentra el cursor. El grosor se indica en píxeles y el color se expresa como en la función *pencolor()*.
~~~~ python
turtle.colormode(255)

turtle.goto(100, 50)
turtle.dot(10, 255, 0, 0)
turtle.goto(100, -50)
turtle.dot(10, 0, 255, 0)
turtle.goto(50, -50)
turtle.dot(10, 0, 0, 255)
turtle.goto(0,0)
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Dot_1.PNG)

~~~~ python
turtle.colormode(255)

turtle.penup()
turtle.goto(100, 50)
turtle.dot(10, 255, 0, 0)
turtle.goto(100, -50)
turtle.dot(10, 0, 255, 0)
turtle.goto(50, -50)
turtle.dot(10, 0, 0, 255)
turtle.goto(0,0)
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Dot_2.PNG)

- *circle(radio, grados, pasos)* : Permite dibujar una curva, estando el centro de la curva a la izquierda perpendicularmente a donde esté apuntado el cursor. 
~~~~ python
turtle.circle(80)   # circulo de radio = 80
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Circulo_1.GIF)

~~~~ python
turtle.circle(80, 180)  # semi-circulo de radio = 80
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Circulo_2.GIF)

~~~~ python
turtle.circle(80, 360, 5)   # circulo de radio = 80 con solo 5 puntos uniformemente distribuidos (pentágono)
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Circulo_3.GIF)
> ⚠️ Si no se dibuja una "curva" completa (360º), el puntero permancerá en la posición y giro finales.

> ⚠️ Si se indica el número de pasos (polígono) y la curva es cerrada (360º), el puntero se encontrará en la misma posición y ángulo que al comienzo de dibujar la curva, aunque el tramo final sea una línea recta.


### Rellenar
- *begin_fill(), end_fill()* : Indican a Python que las figuras que se dibujen se deben rellenar o se deben parar de rellenar.
- *fillcolor(color)* : permite establecer el color de relleno, de la misma manera que la función *pencolor()*. El color de relleno predeterminado es el negro.
~~~~ python
turtle.hideturtle()

turtle.pensize(5)
turtle.fillcolor("red")
turtle.begin_fill()
turtle.goto(100, 0)
turtle.goto(100, 50)
turtle.goto(0, 50)
turtle.goto(0, 0)
turtle.end_fill()
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Fill_1.PNG)

~~~~ python
turtle.hideturtle()

turtle.pensize(5)
turtle.fillcolor("red")
turtle.begin_fill()
turtle.goto(50, 50)
turtle.goto(100, -50)
turtle.goto(150, 0)
turtle.goto(0, 0)
turtle.end_fill()
~~~~
![](Fotos/Manual_Python/Libreria_Turtle/Fill_2.PNG)

> ⚠️ Realmente no es necesario dibujar la figura completa ya que Python rellena la figura aunque no se cierre la figura (es como si Python uniera el último punto de la figura con el primero).
> ~~~~ python
> turtle.hideturtle()
> 
> turtle.pensize(5)
> turtle.fillcolor("red")
> turtle.begin_fill()
> turtle.goto(100, 0)
> turtle.goto(100, 50)
> turtle.goto(0, 50)
> turtle.end_fill()
> ~~~~
> ![](Fotos/Manual_Python/Libreria_Turtle/Fill_3.PNG)

## Librería Tkinter
---
Tkinter es un *binding* de la biblioteca gráfica Tcl/Tk para Python siendo un estandar para GUI *(Graphical User Interface)*.

~~~~ python
import tkinter as tk

raiz = tk.Tk()  # abre un ventana
raiz.mainloop() # mantiene la ventana abierta indefinidamente
~~~~
> ⚠️ *mainloop()* debe ir al final del código para que no se cierre la ventana.

![](Fotos/Manual_Python/Libreria_Tkinter/Ventana.PNG)

En caso de que se quiera lanzar un programa sin saber si se está instalado la librería Tkinter, lo mejor será anticiparnos a estos casos con una excepción.
~~~~ python
>>> try:
...     import tkinter
... except ImportError:
...     raise ImportError("Se requiere el módulo tkinter")
~~~~

Si quisieramos evitar que se abriese la consola de comandos a la vez que se abre la ventana creada, habría que cambiar la extensión del programa de *.py* a *.pyw*.

### Ventanas
- *r.title(texto)* : Añade el texto *texto* como título a la ventana *r* que hemos creado.
~~~~ python
raiz.title("Título de la ventana")
~~~~
- *r.geometry(anchoxlargo)* : Cambia el tamaño predeterminado de la ventana *r* al abrirla por tantos *ancho* píxeles x *largo* píxeles.
~~~~ python
raiz.geometry("500x300")
~~~~
- *r.resizable(booleano_ancho , booleano_alto)* : Permite redimensionar el ancho y largo de la ventana *r* si introducimos *\<True>* o 1. Con *\<False>* o 0 bloquea el tamaño de la ventana al predeterminado al crearla.
- *r.iconbitmap(imagen)* : Cambia el icono predefinido de la ventana *r* por una imagen con extensión *.ico*.
~~~~ python
raiz.iconbitmap("nuevo_icono.ico")
~~~~

### Frames
Contenedor donde se plasmarán los widgets. Pueden haber más de uno en una sola ventana.
~~~~ python
frame = tk.Frame(raiz , parámetros)         # Crear el frame y asignarlo a la ventana
frame.pack()                                # Se empaqueta el frame en la ventana creada
~~~~
> ⚠️ Si no definimos el tamaño de la ventana, ésta se adaptará al frame, pero solo al tamaño inicial. Si está activado la redimensión de la ventana, el frame permanecerá del mismo tamaño y centrado en la parte superior de la ventana.

### Widget
#### Entry
Widget que permite escribir texto en él y sacar el texto como variable.
~~~~ python
cuadroTexto = tk.Entry(frame, parámetros)
~~~~

#### Label
Widget empleado para mostrar texto o imágenes. No se puede interactuar con él.
~~~~ python
variableLabel = tk.Label(frame , parámetros)
~~~~

- *text* : Texto que se muestra en el Label.
- *anchor* : Permite controlar la posición del texto si hay espacio suficiente. *"Center"* por defecto.
- *bg* : Color de fondo (en inglés).
- *bitmap* : Mapa de bits que se mostrará como gráfico.
- *bd* : Grosor del borde. *2 px* por defecto.
- *font* : Tipo de fuente a mostrar.
- *fg* : Color de fuente.
- *width* : Ancho del Label.
- *height* : Altura del Label.
- *image* : Imagen que se muestra en el Label.
- *justify* : Orientación del texto del Label. *left* por defecto.

> **Ejemplo**
~~~~ python
import tkinter as tk

root = tk.Tk()
root.title('Pack Demo')
root.geometry("350x200")

# box 1
box1 = tk.Label(root, text="Box 1", bg="green", fg="white")
box1.pack()

# box 2
box2 = tk.Label(root, text="Box 2", bg="red", fg="white")
box2.pack()

root.mainloop()
~~~~
![](Fotos/Manual_Python/Libreria_Tkinter/Pack.PNG)
> ⚠️ El punto de origen de coordenadas (x,y) es la esquina superior izquierda.  
> ![](Fotos/Manual_Python/Libreria_Tkinter/PackCoordenadas.PNG)

#### Text
Widget que permite introducir un texto largo en pantalla.
~~~~ python
Texto = tk.Text(frame , parámetros)
~~~~

Mismos *parámetros* que *Label*.
> ⚠️ Si el texto supera el tamaño predeterminado del cuadro, el widget hace scroll vertical automaticamente pero no hay barra de scroll inicialmente.
> Para introducir una barra de movimiento al cuadro de texto tenemos que crearla.
> ~~~~ python
> barra_movimiento = ScrollBar(frame, command=Texto.yview)
> barra_movimiento.grid(fila, columna, sticky="nsew")
> Texto.config(yscrollcommand=scrollVert.set)
> ~~~~

#### Button
Widget que inserta un botón interactuable que ejecutará una acción asignada.
~~~~ python
def funcionBoton():
    return

Boton = tk.Button(frame, text="Texto", command=lambda:funcionBoton) 
Boton.pack()
~~~~
![](Fotos/Manual_Python/Libreria_Tkinter/Button.PNG)

#### Radiobutton
Widget que introduce una lista de opciones de selección de respuesta única.
~~~~ python
varOption = tk.IntVar()

tk.Radiobutton(frame, text="Option 1", variable=varOption, value=1).pack()
tk.Radiobutton(frame, text="Option 2", variable=varOption, value=2).pack()
tk.Radiobutton(frame, text="Option 3", variable=varOption, value=3).pack()
~~~~
![](Fotos/Manual_Python/Libreria_Tkinter/Radiobutton.PNG)

#### Checkbutton
Widget que introduce una lista de opciones de selección de respuesta multiple.
~~~~ python
varOption1 = tk.IntVar()
varOption2 = tk.IntVar()
varOption3 = tk.IntVar()

tk.Checkbutton(frame, text="Option 1", variable=varOption1, onvalue=1, offvalue=0).pack()
tk.Checkbutton(frame, text="Option 2", variable=varOption2, onvalue=1, offvalue=0).pack()
tk.Checkbutton(frame, text="Option 3", variable=varOption3, onvalue=1, offvalue=0).pack()
~~~~
![](Fotos/Manual_Python/Libreria_Tkinter/Checkbutton.PNG)

#### Menu
Widget que permite añadir una barra de menú con una lista de opciones (submenús) en cada elemento creado.
~~~~ python
menu = tk.Menu(raiz)
raiz.config(menu=menu)

menuArchivo = tk.Menu(menu)
menuEdicion = tk.Menu(menu)
menuAyuda = tk.Menu(menu)

menuArchivo = tk.Menu(menu, tearoff=0)
menuArchivo.add_command(label="Nuevo")
menuArchivo.add_command(label="Abrir")
menuArchivo.add_command(label="Guardar")

menu.add_cascade(label="Archivo", menu=menuArchivo)
menu.add_cascade(label="Edicion", menu=menuEdicion)
menu.add_cascade(label="Ayuda", menu=menuAyuda)
~~~~
![](Fotos/Manual_Python/Libreria_Tkinter/Menu_1.PNG)
![](Fotos/Manual_Python/Libreria_Tkinter/Menu_2.PNG)
> ⚠️ Si se quiere separar los distintos submenús dentro de un misco menú para crear y diferenciar grupos de opciones, tan solo hay que añadir entre los submenús a separar el código:
> ~~~~ python
> menu.add_command(label="Submenu1")
> menu.add_separator()
> menu.add_command(label="Submenu2")
> ~~~~

#### Ventanas emergentes
Ventanas modales para informar, avisar o permitir realizar tareas al usuario.

Estas ventanas no forman parte de la biblioteca estándar de Tkinter, por lo que hay que importarlas aparte.
~~~~ python
from tkinter import messagebox

messagebox.showinfo("Titulo", "Texto informativo")
messagebox.showwarning("Titulo", "Texto de aviso")
messagebox.askquestion("Titulo", "Pregunta")        # devuelve los valores "yes" ó "no"
messagebox.askokcancel("Titulo", "Pregunta")        # devuelve los valores <True> ó <False>
messagebox.askretrycancel("Titulo", "Pregunta")     # devuelve los valores <True> ó <False>
~~~~
![](Fotos/Manual_Python/Libreria_Tkinter/VentanaEmergente_1.PNG)
![](Fotos/Manual_Python/Libreria_Tkinter/VentanaEmergente_2.PNG)
![](Fotos/Manual_Python/Libreria_Tkinter/VentanaEmergente_3.PNG)
![](Fotos/Manual_Python/Libreria_Tkinter/VentanaEmergente_4.PNG)
![](Fotos/Manual_Python/Libreria_Tkinter/VentanaEmergente_5.PNG)

#### Abrir archivos
~~~~ python
from tkinter import filedialog

filedialog.askopenfilename(title="Titulo", initialdir="C:/", filetypes=(("Ficheros de Excel" , "*xlsx"), ("Ficheros de texto" , "*.txt")))  # devuelve la ruta del fichero seleccionado
~~~~
![](Fotos/Manual_Python/Libreria_Tkinter/FileDialog.PNG)
> ⚠️ Por defecto, se abre la ruta *📄 > Este equipo > Documentos*

#### Comandos de configuración
- *.place(x=posiciónx, y=posicioy)* : Permite indicar a los widgets dónde colocarse dentro del *frame* con coordenadas *(posicionx,posiciony)* respecto de la esquina superior izquierda en píxeles.
~~~~ python
variableLabel.place(x=50, y=50)
cuadroTexto.place(x=100, y=50)
~~~~
![](Fotos/Manual_Python/Libreria_Tkinter/place_1.PNG)
> ⚠️ Si x,y son iguales en dos elementos, la salida los colocará uno al lado del otro por orden de declaración. Pero si una posición de un elemento está dentro del espacio de otro, la salida los superpondrá según el orden en los que hayan sido declarados.  
> ~~~~ python
> cuadroTexto.place(x=100, y=50)
> variableLabel.place(x=110, y=50)
> ~~~~
> ![](Fotos/Manual_Python/Libreria_Tkinter/place_2.PNG)

- *.grid(row=fila, column=columna)* : Divide el frame en filas y columnas, pero a nivel conceptual para ordenar elementos. El orden de filas y columnas funciona igual que las listas, siendo la primera fila y columna la 0.
~~~~ python
variableLabel.grid(row=0, column=0)
cuadroTexto.grid(row=0, column=1)
~~~~
![](Fotos/Manual_Python/Libreria_Tkinter/grid.PNG)
> ⚠️ Si se quiere que los elementos se organicen en un dirección (texto pegado arriba, derecha, abajo-izquierda, etc) solo hay que añadir el parámetro *sticky=*. Funciona igual que *anchor*.

- *.pack()* : Empaqueta el widget dentro del frame *frame* asignado y permite modificar la posición, espacio y relleno de los widgets.
> + *ipadx* / *ipady* : Rellena internamente los widgets horizontalmente y verticalmente.
> ~~~~ python
> box1.pack(ipadx=999, ipady=999)
> ~~~~
>
> **Ejemplo**
> ~~~~ python
> box1.pack(ipadx=10, ipady=10)
> box2.pack(ipadx=10, ipady=10)
> ~~~~
> ![](Fotos/Manual_Python/Libreria_Tkinter/ipad.PNG)

> + *fill* : Rellena el espacio de un widget horizontalmente, verticalmente o ambos.
> ~~~~ python
> frame.pack(fill="x")
> frame.pack(fill="y")
> frame.pack(fill="both")
> frame.pack(fill="none")
> ~~~~
>
> **Ejemplo**
> ~~~~ python
> box1.pack(ipadx=20, ipady=20, fill='x')
> ~~~~
> ![](Fotos/Manual_Python/Libreria_Tkinter/fill_1.PNG)
> ![](Fotos/Manual_Python/Libreria_Tkinter/fill_2.PNG)

> + *expand* : Aumenta el espacio disponible de un frame/widget todo lo posible. El espacio estará delimitado por la posición y espacio de otros widgets.
> ~~~~ python
> frame.pack(expand=True)
> frame.pack(expand=1)
> frame.pack(expand=False)
> frame.pack(expand=0)
> ~~~~
>
> **Ejemplo**
> ~~~~ python
> box1.pack(ipadx=20,ipady=20,expand=True)
> ~~~~
> ![](Fotos/Manual_Python/Libreria_Tkinter/expand_1.PNG)
> ~~~~ python
> box1.pack(ipadx=20, ipady=20, fill="both", expand=True)
> ~~~~
> ![](Fotos/Manual_Python/Libreria_Tkinter/expand_2.PNG)
> ~~~~ python
> box1.pack(ipadx=20, ipady=20, fill="both", expand=True)
> box2.pack(ipadx=20, ipady=20, expand=True)
> ~~~~
> ![](Fotos/Manual_Python/Libreria_Tkinter/expand_3.PNG)

> + *anchor* : Ancla el widget en base a los puntos cardinales como puntos de referencia dentro de su propio espacio disponible.  
> ![](Fotos/Manual_Python/Libreria_Tkinter/anchorCoordenadas.JPG)  
>
> **Ejemplo**
> ~~~~ python
> box1.pack(ipadx=20, ipady=20, anchor="e",  expand=True)
> box2.pack(ipadx=20, ipady=20, anchor="w",  expand=True)
> ~~~~
> ![](Fotos/Manual_Python/Libreria_Tkinter/anchor.PNG)

> + *side* : Alinea el espacio del widget.
> ~~~~ python
> frame.pack(side="left")
> frame.pack(side="right")
> frame.pack(side="top")
> frame.pack(side="bottom")
> ~~~~
> **Ejemplo**
> ~~~~ python
> box1.pack(ipadx=20, ipady=20, fill="both", expand=True, side="left")
> box2.pack(ipadx=20, ipady=20, fill="both", expand=True) # side="top"
> ~~~~
> ![](Fotos/Manual_Python/Libreria_Tkinter/side.PNG)

> + *padx* / *pady* : Rellena externamente los widgets horizontalmente y verticalmente.
> ~~~~ python
> box1.pack(padx=999, pady=999)
> ~~~~
> **Ejemplo**
> ~~~~ python
> box1.pack(ipadx=20, ipady=20, padx=20, pady=20, fill="both", expand=True)
> box2.pack(ipadx=20, ipady=20, padx=20, pady=20, fill="both", expand=True)
> ~~~~
> ![](Fotos/Manual_Python/Libreria_Tkinter/pad.PNG)

## Librería Pygame
---
[Pygame](https://www.pygame.org/news) es un conjunto de módulos del lenguaje Python que permiten la creación de videojuegos en dos dimensiones de una manera sencilla. Está orientado al manejo de sprites.
![](Fotos/Manual_Python/Libreria_Pygame/PygameLogo.PNG)

- *init()* : Inicializa todos los módulos de pygame importados.
> Si algún módulo no se puede importar, no se mostrará ninguna excepción, pero se devolverá una tupla. El primer elemento es el número de módulos importados correctamente y el segundo elemento es el número de importaciones fallidas.

> ⚠️ Tal vez se desee inicializar diferentes módulos por separado para mejorar la velocidad de ejecución del programa, o no cargar módulos que no se utilizan temporalmente.

> Está bien llamar al método init () repetidamente, y no habrá efectos negativos. Incluso si ha llamado a pygame.quit (), es posible desinstalar todos los módulos.

-  *quit()* : Desinstala todos los módulos importados de pygame.
> Cuando se cierra el intérprete de Python, este método se llamará incondicionalmente, por lo que su programa no necesita llamar a este método a menos que desee terminar el recurso de pygame y continuar realizando otras funciones. 

> No es ningún problema ejecutar este método varias veces.

- *get_error()* : Módulo de excepción estándar de pygame.
> Obtiene un mensaje de error interno mantenido por SDL. Esta información se le proporcionará cuando se genere la excepción estándar de pygame.

- *set_error()* : Establece la información de error actual.
> Establece un mensaje de error interno mantenido por SDL. Esta información se le proporcionará cuando se genere la excepción estándar de pygame.

- *get_sdl_version()* : Obtiene el número de versión de SDL.
> Devuelve los 3 dígitos de la versión relevante de la biblioteca SDL. Esta versión se genera en tiempo de compilación. 

> ⚠️ Este método se puede utilizar para saber qué componente no funciona correctamente.

## Expresiones regulares
---
Mediante secuencias de [metacaracteres](./Manual_RegEx.md "Manual RegEx") se buscan patrones de caracteres.

### Coincidencia de caracteres
- *match(comparador, c)* : Determina si el comienzo de la cadena *c* coincide con la cadena *comparador*.
- *search(comparador, c)* : Escanea la cadena *c*, buscando la cadena *comparador* hasta encontrar una coincidencia.
- *findall(comparador, c)* : Encuentra todas las subcadenas de caracteres de la cadena *c* donde coincide la cadena *comparador* y las retorna como una lista.
- *finditer(comparador, c)* : Encuentra todas las subcadenas de caracteres de la cadena *c* donde coincide la cadena *comparador* y las retorna como un término iterado
> ⚠️ Si se cumplen las condiciones de las sentencias se devuelve un *\<match object>*. En caso contrario, devuelve *\<None>*.

~~~~ python
>>> import re
>>> texto = "Bienvenidos y bienvenidas a Python"
>>> re.match('Bienv', texto)
<re.Match object; span=(0, 5), match='Bienv'>
>>> re.search('Pithon', texto)
None
>>> re.findall('y', texto)
['y', 'y']
>>> re.finditer('y', texto)
<callable_iterator object at 0x7f00a4a35610>
~~~~

~~~~ python
>>> import re
>>> lista = ['A1', 'B7', 'D5', 'a2', 'f5', 'z9']
>>> for elemento in lista:
...     if re.findall('^B', elemento):  # los elementos que empiezan por "B"
...         print(elemento)
'B7'
...     if re.findall('5$', elemento):  # los elementos que terminen en "5"
...         print(elemento)
'D5' 
'f5'
...     if re.findall('[a-z]', elemento):   # los elementos que contegan un caracter entre "a" y "z" (ambos incluidos)
...         print(elemento)
'a2'
'f5'
'z9'
...     if re.findall('[A-D][1-4]', elemento):  # los elementos que sean una combinación entre los rangos A-D y 1-4 en dicho orden
...         print(elemento)
'A1'
...     if re.findall('[AD][1-8]', elemento): # los elementos que sean A ó D más un valor en el rango 1-8
...         print(elemento)
'A1'
'D5'
...     if re.findall('\w[^156]', elemento): # los elementos que contengan un caracter alfanumérico más un valor distinto de 1, 5 ó 6
...         print(elemento)
'B7'
'a2'
'z9'
~~~~
~~~~ python
>>> import re
>>> lista = ['Google', 'Yahoo', 'Amazon', 'Apple', 'Audi', 'Mercedes']
>>> for elemento in lista:
>>>     if re.findall('[oo{2}]', elemento): # los elementos que tengan 1 ó 2 "o"
>>>         print(elemento)
'Google'
'Yahoo'
'Amazon'
>>>     if re.findall('oo|pp', elemento): # los elementos que tengan "oo" ó "pp" 
>>>         print(elemento)
'Google'
'Yahoo'
'Apple'
>>>     if re.findall('a.o', elemento): # los elementos que tengan "a" +...+ "o"
>>>         print(elemento)
'Yahoo'
'Amazon'
~~~~

## Depuración de código
---
### Depuración de programas
La depuración es una técnica que permite *trazar* un programa, es decir, seguir el flujo de ejecución de un programa paso a paso, ejecutando una instrucción en cada paso, y observar el estado de sus variables.

Cuando un programa tiene cierta complejidad, la depuración es imprescindible pare detectar posibles errores.

Python dispone del módulo *pyd* para depurar programas, pero es mucho más cómodo utilizar algún entorno de desarrollo que incorpore la depuración, como por ejemplo Visual Studio Code.

#### Comandos de depuración
- **Establecer punto de parada**: Detiene la ejecución del programa en una línea concreta de código.
- **Continuar la ejecución**: Continúa la ejecución del programa hasta el siguiente punto de parada o hasta que finalice.
- **Próximo paso**: Ejecuta la siguiente línea de código y para la ejecución.
- **Próximo paso con entrada en función**: Ejecuta la siguiente línea de código. Si se trata de una llamada a una función entonces ejecuta la primera instrucción de la función y para la ejecución.
- **Próximo paso con salida de función**: Ejecuta lo que queda de la función actual y para la ejecución.
- **Terminar la depuración**: Termina la depuración.

#### Depuración en Visual Studio Code
Antes de iniciar la depuración de un programa en VSCode hay que establecer algún punto de parada. Para ello basta con hacer click en le margen izquierdo de la ventana con del código a la altura de la línea donde se quiere parar la ejecución del programa.

![](Fotos/Manual_Python/Depuracion_Codigo/BreakPoint.PNG)

Para iniciar la depuración de un programa en VSCode hay que hacer clic sobre el botón ![](https://aprendeconalf.es/docencia/python/manual/img/debug-button.png) o pulsar la combinación de teclas (Ctr+Shift+D).

La primera vez que depuremos un programa tendremos que crear un fichero de configuración del depurador (*launch.json*). Para ello hay que hacer clic en el botón *Run and Debug*. VSCode mostrará los distintos ficheros de configuración disponibles y debe seleccionarse el más adecuado para el tipo de programa a depurar. Para programas simples se debe seleccionar *Python file*.

La depuración comenzará iniciando la ejecución del programa desde el inicio hasta el primer punto de parada que encuentre.

Una vez iniciado el proceso de depuración, se puede avanzar en la ejecución del programa haciendo uso de la barra de depuración que contiene botones con los principales comandos de depuración.

![](Fotos/Manual_Python/Depuracion_Codigo/DebbugerBar.PNG)

Durante la ejecución del programa, se puede ver el contenido de las variables del programa en la ventana del estado de las variables.

El usuario también puede introducir expresiones y ver cómo se evalúan durante la ejecución del programa en la ventana de vista de expresiones.

![](Fotos/Manual_Python/Depuracion_Codigo/DebbugerEstadoVariables.PNG)

## Trucos y consejos
---
### Operador ternario / Expresión condicional
A la hora de expresar condiciones *if...else...* se suele hacer por enseñanza básica en mínimo 4 líneas de código.
~~~~ python
>>> if condition:
...     option_1
... else:
...     option_2
~~~~

Pero todo ese párrafo se puede expresar en una misma línea de código con la estructura: 
~~~~ python
>>> option_1 if condition else option_2
~~~~

### Expresar numeros grandes en grupos de miles
Si queremos escribir un número grande en papel y saber por cuantos grupos de miles está formado solo tendríamos que separar por <.> en grupos de 3 por la derecha: *1.234; 1.642.146; 15.425.564.456*.  
Pero Python no lo permite de la misma manera ya que el punto se emplea para los valores de *coma flotante* (números decimales). 

Así que podemos o expresar todo el número seguido (*123456789*) o separlo de la misma manera con <_> (*123_456_789*).
~~~~ python
>>> num1 = 10_000_000_000
>>> num2 = 100_000_000
>>> total = num1 + num2
10100000000
>>> print(f'{total:,}')
10,100,000,000
~~~~

### Enumerar listas
En vez leer elemento a elemento una lista y declarar un índice externamente para enumerar la lista y aumentar este con cada lectura
~~~~ python
>>> lista = ['A', 'B', 'C', 'D']
>>> i = 0
>>> for elemento in lista:
...     print(i, elemento)
...     i += 1
...
0 A
1 B
2 C
3 D
~~~~
podemos usar la función *enumerate(list, start=)* que crea un objeto que contiene tuplas con el índice y el elemento de la lista.
~~~~ python
>>> lista = ['A', 'B', 'C', 'D']
>>> for i, elemento in enumerate(lista, start=1):
...     print(i, elemento)
...
1 A
2 B
3 C
4 D
~~~~

### Juntar listas
Si queremos recorrer dos (o más) listas a la vez, la función *zip(lista1, lista2, ...)* une en tuplas cada elemento correspondiente al mismo índice hasta el elemento de la lista más corta, el resto los ignora.

~~~~ python
>>> identidades = ['Peter Parker', 'Clark Kent', 'Wade Wilson', 'Bruce Wayne']
>>> superheroes = ['Spiderman', 'Superman', 'Deadpool', 'Batman']
>>> villanos = ['Venom', 'Lex Luthor', 'Taskmaster', 'Joker']
>>> for nombre, superheroe, villano in zip(identidades, superheroes, villanos):
...     print(f'{nombre} en realidad es {superheroe}, y su enemigo es {villano}')
...
Peter Parker en realidad es Spiderman, y su enemigo es Venom
Clark Kent en realidad es Superman, y su enemigo es Lex Luthor
Wade Wilson en realidad es Deadpool, y su enemigo es Taskmaster
Bruce Wayne en realidad es Batman, y su enemigo es Joker
~~~~
> ⚠️ Si se quiere forzar la necesidad de que todas las listas tengan el mismo tamaño, solo es necesario incluir el comando *strict=True* al final.
> ~~~~ python
> >>> listas = [['A','B','C'],[1,2,3,4],['X','Y','Z']]
> >>> for val1, val2, val3 in zip(*listas, strict=True):
> ...   print(f'{val1}, {val2}, {val3}')
> ...
> A, 1, X
> B, 2, Y
> C, 3, Z
> Traceback (most recent call last):
>   File "<stdin>", line 1, in <module>
> ValueError: zip() argument 2 is longer than argument 1
> ~~~~

### Ignorar valores de un conjunto
Al asignar un valor a una variable, si solo quisieramos unos valores concretos y quiesieramos ahorrarnos el declarar cada varaible por la llamada al conjunto por su correspondeinte índice, podemos usar <_> para cada valor del que queramos pasar.
~~~~ python
>>> a, _, b = (1,7,10)
>>> a
1
>>> b
10
~~~~

### Asignar valores demás
Parecido al caso anterior, si queremos asignar más de un valor (una lista) al declarar una varias variables donde a algunas solo se les pasará un único valor, podemos escribir <*> detrás de una variable para expresar que es un conjunto de valores.
~~~~ python
>>> a, b, *c, d = (1,2,3,4,5,6)
>>> a
1
>>> b
2
>>> c
[3,4,5]
>>> d
6
~~~~
> ⚠️ Si se emplease <*_> en la declaración de variables esto haría que se ignorasen los conjuntos sobrantes.
> ~~~~ python
> >>> a, *_, b = (1,2,3,4)
> >>> a
> 1
> >>> b
> 4
> ~~~~

### Intercambiar valores entre variables
Generalmente, cuando se quiere intercambiar los valores de dos o más varias variables se crea una variable auxiliar para almacenar el valor de una de las variables, sobrescribirla y asignar a la última de ellas este valor.  
Python permite un método más simple.

Tan solo hay que igualar el conjunto de variables al conjunto de variables correspondiente según el valor que se quiera asignar.
~~~~ python
>>> a = 7
>>> b = -3
>>> c = 0
>>> d = 1
>>> a, b, c, d = d, c, a , b
>>> a
1
>>> b
0
>>> c
7
>>> d
-3
~~~~

### Contar valores/caracteres de un objeto
Si quisieramos contar cuantos valores únicos y cuantas veces se repiten en un objeto, la función *Counter()* se encarga de crear un diccionario siendo cada las *keys* los valores únicos y los *values* la cantidad de veces que se repiten, todo ordenado en orden descendente por *value*.
~~~~ python
from collections import Counter
~~~~

~~~~ python
>>> palabra = 'COBOL'
>>> contador = Counter(palabra)
>>> contador
{'O': 2, 'C': 1, 'B': 1, 'L': 1}
>>> contador['X']
0
>>> lista = [10,10,10,5,5,2,9,9,9,9,9,9]
>>> contador = Counter(lista)
>>> contador
{9: 6, 10: 3, 5: 2, 2: 1}
>>> contador[10]
3
~~~~
Podemos separar también las *keys* más repetidas.
~~~~ python
>>> contador.most_common(2)
[(9, 6), (10, 3)]
~~~~

### Fusionar diccionarios
Si tenemos varios diccionarios que queremos juntar tan solo hay que declar un nuevo diccionario poniendo <**> detrás de cada uno de ellos.
~~~~ python
>>> d1 = {'nombre': 'Javier', 'edad': 26}
>>> d2 = {'nombre': 'Javier', 'oficio': 'programador'}
>>> d3 = {'nombre': 'Nacho', 'edad': 33}
>>>
>>> d4 = {**d1, **d2}
>>> d4
{'nombre': 'Javier', 'edad': 26, 'oficio': 'programador'}
~~~~

Pero si incluimos otro diccionario con una misma *key* en común pero diferente *value* se sobrescribirá el *value* previo.
~~~~ python
>>> d1 = {'nombre': 'Javier', 'edad': 26}
>>> d2 = {'nombre': 'Javier', 'oficio': 'programador'}
>>> d3 = {'nombre': 'Nacho', 'edad': 33}
>>>
>>> d4 = {**d1, **d2, **d3}
>>> d4
{'nombre': 'Nacho', 'edad': 33, 'oficio': 'programador'}
~~~~

### Rellenar con ceros
Si quisieramos rellenar con ceros un texto hasta alcanzar una longitud *n* podemos usar el comando *.zfill(n)*.
~~~~ python
>>> txt = '123'
>>> txt.zfill(10)
0000000123
~~~~
> ⚠️ Si la longitud del texto original es superior a la lingitud *n* especificada, no pasará nada.
> ~~~~ python
> >>> txt = '12345'
> >>> txt.zfill(3)
> 12345
> ~~~~
