# MANUAL JAVA

![Java](Fotos/Manual_Java/Java_logo.png)

1. [INTRODUCCIÓN A JAVA](#introducción-a-java)
2. [CONCEPTOS BÁSICOS](#conceptos-básicos)
   - [Comentatios](#comentarios)
   - [Identificadores](#identificadores)
3. [TIPOS PRIMITIVOS Y VARIABLES](#tipos-primitivos-y-variables)
4. [OPERADORES](#operadores)
   - [Operadores aritméticos](#operadores-aritméticos)
   - [Operadores de asignación](#operadores-de-asignación)
   - [Operadores unarios](#operadores-unarios)
   - [Operadores InstanceOf](#operador-instanceof)
   - [Operadores incrementales](#operadores-incrementales)
   - [Operadores relacionales](#operadores-relacionales)
   - [Operadores lógicos](#operadores-lógicos)
   - [Operador de concatenación con cadena de caracteres '+'](#operador-de-concatenación-con-cadena-de-caracteres-)
   - [Operadores que actúan a nivel de bits](#operadores-que-actúan-a-nivel-de-bits)
5. [ESTRUCTURAS DE CONTROL](#estructuras-de-control)
   - [Bifurcaciones](#bifurcaciones)
   - [Bucles](#bucles)
   - [Ramificaciones](#ramificaciones)
   - [Excepciones](#excepciones)
6. [CLASES](#clases)
7. [ORGANIZAR CLASES](#organizar-clases)

## INTRODUCCIÓN A JAVA
---
[Java](https://www.java.com/es/) nace y da sus primeros pasos en 1991 formando parte de un proyecto de desarrollo de soporte software para electrónica de consumo (frigoríficos, lavadoras...), llevado a cabo por un equipo de *SUN* llamado *Green Team*. Este primer enfoque le da a Java una de sus más interesantes características: la portabilidad, dado que Java tenía que funcionar en numerosos tipos de CPUs, y por tanto se pensó para ser independiente de la plataforma sobre la que funcione. Esta característica es muy posiblemente la que ha permitido a Java convertirse actualmente en el lenguaje por excelencia para la creación de aplicaciones en Internet.

Este salto de Java para convertirse en un lenguaje de programación para computadores se da definitivamente en 1995 cuando en la versión 2 del navegador web [netscape](https://isp.netscape.com/) se incluye un interprete para este lenguaje, produciendo de este modo una auténtica revolución en Internet.

Con este nuevo enfoque Java sigue creciendo y saca su versión 1.1 en 1997 con muchas mejoras y adaptaciones, fruto de una revisión sustancial del lenguaje. Java 1.2 aparece a finales de 1998 y más tarde se rebautizará como Java 2.  
Java 2 es la tercera versión importante del lenguaje de programación Java. Parte de la versión 1.1 sin introducirle cambios sustanciales, simplemente ampliándolo.

*SUN* describe a Java como:
- simple
- orientado a objetos
- distribuido
- interpretado
- robusto
- seguro
- de arquitectura neutra
- portable
- de altas prestaciones
- multitarea
- dinámico

Java presenta muchas características que lo diferencian de lenguajes similares como C++, empezando por las posibilidades de ejecución:
- ***Stand Alone*** : Aplicación independiente.
- ***Applet*** : Aplicación especial que se ejecuta en el navegador del cliente.
- ***Servlet*** : Aplicación especial sin interfaz que se ejecuta en servidor.


## CONCEPTOS BÁSICOS
---
### Comentarios
~~~~ java
// Comentario de una sola línea
/* Comentario de una o más líneas */
/** Comentario de documentación */
~~~~

### Identificadores
Un identificador es un "nombre" que nos permite dirigirnos específicamente a una de las entidades propias del lenguaje, es decir, son los nombres que podemos ponerles a nuestras variables, métodos, clases, interfaces y objetos.

La única restricción en la formación de identificadores es que tienen que comenzar por letra, guion bajo *_* o por el signo *$*, pudiéndoles seguir después letras o números. Hay que tener en cuenta que en Java como en otros muchos lenguajes de programación se distinguen las mayúsculas y las minúsculas.

Hay una serie de normas muy recomendables para crear identificadores en Java: En Java es habitual escribir todos los identificadores en minúscula teniendo en cuenta las siguientes excepciones:
   - Si en un identificador queremos incluir un nombre compuesto se pone el primer nombre entero en minúscula y el resto con la primera letra en mayúscula y el resto en minúscula.
~~~~ java
miNuevaVariable = 3;
~~~~
   - Los identificadores de clases e interfaces siempre empiezan en mayúscula siguiendo la anterior norma en caso de tratarse de un nombre compuesto.
~~~~ java
MiNuevaClase();
~~~~
   - Las constantes se escriben íntegramente en mayúscula.
~~~~ java
PI = 3.141592653589793238462
~~~~
   - No coincidir con ciertas palabras restringidas del propio lenguaje:
~~~~ java
abstract   continue    for         new         switch      boolean     default     goto        null        synchronized
break      do          if          package     this        byte        double      implements  private     threadsafe
byvalue    else        import      protected   throw       case        extends     instanceof  public      transient
catch      false       int         return      true        char        final       interface   short       try
class      finally     long        static      void        const       float       native      super       while
~~~~

## TIPOS PRIMITIVOS Y VARIABLES
---
Como tipos primitivos entendemos aquellos tipos de información más usuales y básicos. Son los habituales de otros lenguajes de programación.
- **boolean** : *\<True>* / *\<False>*.
- **char** : Usa el código *UNICODE* y ocupa cada carácter 16 bits.
- **Enteros** : Difieren en las precisiones y pueden ser positivos o negativos.
   - *byte* : 1 byte.
   - *short* : 2 bytes.
   - *int* : 4 bytes.
   - *long* : 8 bytes.
- **Reales en punto flotante**: igual que los enteros también difieren en las precisiones y pueden ser positivos o negativos.
   - *float* : 4 bytes.
   - *double* : 8 bytes.

Una variable referenciará siempre a un tipo primitivo de Java o a cualquier otro objeto creado en nuestro programa.
~~~~ java
int a;      // declaración de una variable 'a'
            // inicializada a 0 (valor por defecto)
int b = 8;  // declaración de una variable 'b'
            // inicializada a 8

NombreClase referencia;        // declaración de una variable 'referencia' preparada para llevar un objeto de la clase 'NombreClase'
referencia = new NombreClase;  // se crea un nuevo objeto de la clase 'NombreClase'
                               // asignado a la variable 'referencia'
referencia2 = referencia;      // 'referencia2' tiene el mismo objeto que 'referencia'
~~~~

Para poder acceder a las variables (ámbito de las variable) está la norma de que tiene validez dentro del bloque encerrado entre llaves donde ha sido declarada.
~~~~ java
public class AmbitoVariables {
    public static void main(String[] args) {
       if (true) {
          int y=5;
       }
       System.out.println(y);
    }
}
~~~~
> Si intentamos ejecutar este código el compilador nos dará un error diciéndonos que la variable *\<y>* no está definida puesto que la hemos declarado en un bloque distinto de donde la pretendemos utilizar.

Hay mas normas de ámbito respecto a las variables miembro de una clase. Para acceder a ellas depende si en la clase está declarada como *public* o como *private*. Las variables declaradas en una clase como *public* se acceden directamente a través de *\<NombreClase.nombreVariable*. En caso de una variable *private* solo podemos utilizarla mediante los métodos de esa clase.

Por otro lado desde la declaración de cualquier función propia de una clase podemos acceder a las variables internas de esa clase directamente.


## OPERADORES
---
### Operadores aritméticos
~~~~ java
>>> int a = 14;
>>> int b = 3;
>>> int c = a + b;  // Suma
17
>>> int c = a - b;  // Resta
11
>>> int c = a * b;  // Multiplicación
42
>>> int c = a / b;  // División
4
>>> int c = a % b;  // Resto de la División
2
~~~~

### Operadores de asignación
~~~~
a += b --> a = a + b
a -= b --> a = a - b
a *= b --> a = a * b
a /= b --> a = a / b
a %= b --> a = a % b
~~~~

### Operadores unarios
El signo *-* delante de un valor para cambiarle el signo del operando
~~~~ java
>>> int a = 1;
>>> -a
-1
>>> -a
1
~~~~

### Operador Instanceof
Nos permite saber si un objeto pertenece a una clase o no.

### Operadores incrementales
Son operadores que nos permiten incrementar (*++*) o decrementar(*--*) las variables en una unidad.
~~~~ java
>>> int i
>>> i++
1
>>> ++i
2
~~~~
> Cuando el operador se utiliza en su forma de sufijo (*i++*) el valor de *i* se incrementará sólamente después de que el valor actual de *i* haya sido utilizado en la expresión. En formato prefijo (*++i*) incrementará directamente el valor.

### Operadores relacionales
~~~~
>   // Mayor que
<   // Menor que
==  // Iguales
!=  // Distintos
>=  // Mayor o igual que
<=  // Menor o igual que
~~~~
> Devuelven siempre un valor boolean

### Operadores lógicos
~~~~
&&  // Devuelve <True> si ambos operandos son <True>
||  // Devuelve <True> si al menos uno de los operandos es <True<
!   // Niega el operando
~~~~

### Operador de concatenación con cadena de caracteres '+'
~~~~ java
>>> int result = 10
>>> "El total es"+ result + "unidades"
El total es 10 unidades
~~~~

### Operadores que actúan a nivel de bits
~~~~ java
>>  // Desplazamiento a la derecha de los bits del operando
<<  // Desplazamiento a la izquierda de los bits del operando
&   // Operador AND a nivel de bit
|   // Operador OR a nivel de bit
~~~~


## ESTRUCTURAS DE CONTROL
---
### Bifurcaciones
Permiten ejecutar código en función de una expresión evaluada

#### if
~~~~ java
if (expresionBooleana) {
   sentencias
}

if (expresionBooleana) {
   sentencias
} else {
   conjuntoAlternativo
}

if (expresionBooleana) {
   sentencias
} else if {
   conjuntoAlternativo
} else if {
   conjuntoAlternativo2
}
~~~~

#### switch
~~~~ java
switch (expresion) {
   Case valor1:
      sentencias;
      break;
   Case valor2:
      sentenciasAlternativas;
      break;
   Case valor3:
      sentenciasAlternativas2;
      break;
   Case valor4:
      sentenciasAlternativas3;
      break;
}
~~~~
> La sentencia *break* al final de cada opción sirve para que no evalue el resto de opciones sino que se salga directamente del *switch*.

### Bucles
#### for
~~~~ java
for (inicializacion, expresionBooleana, incremento) {
   sentencias;
}
~~~~

#### while
~~~~ java
while (expresionBooleana) {
   sentencias;
}
~~~~

#### do while
~~~~ java
do {
   sentencias;
} while (expresionBooleana)
~~~~

### Ramificaciones
#### break
Permite salirnos del bloque de sentencias (encerrado entre llaves) o el bucle que estamos ejecutando, sin ejecutar las sentencias que resten para el final o las restantes iteraciones del bucle.

#### continue
Solo es válida para bucles. Impide ejecutar las sentencias que restan para la finalización de una iteración de ese bucle, continuando después con las siguientes iteraciones del bucle.

#### return
Permite finalizar también un conjunto de sentencias, con la peculiaridad esta vez de que también finaliza el método o función en el que se encuentre. En el caso de que queramos devolver un valor desde esa función o método lo debemos poner a continuación de *return*.

### Excepciones
El tratamiento de excepciones se utiliza para detectar errores cuando se ejecutan nuestros programas y tratarlos del modo que nosotros queramos. Los errores cazados por un sistema de tratamiento de excepciones no bloquean el programa y el manejo de excepciones nos permite hacer cosas cuando esos errores ocurren.

#### try
#### catch
#### finally

## CLASES
---
Una clase es el producto de enfocar la programación a los datos más que a las funciones. Por tanto, una clase es una colección de datos con los que operar una serie de funciones propias de la clase. 

~~~~ java
permiso class NombreClase {
   estructuraClase;
}
~~~~

La primera palabra nos proporciona la posibilidad de dar permisos de accesos a nuestra clase.
- **Package** : Usar este identificador en la cabecera de la clase es opcional, pues es la opción por defecto en Java.
- **Public** : Accesible desde cualquier otra clase. No obstante, para que esto suceda debe ser primero accesible el *package* de esa clase *public*. Para que un *package* sea accesible debe de estar en el directorio que señala la variable *CLASSPATH* que definimos al instalar nuestro entorno Java y tener permiso de lectura en ese directorio.

En cuanto al nombre de la clase debe de obedecer al convenio de nombres de Java y coincidir con el nombre del fichero *.java* en el que se guardará la clase.  
Lo normal es que cada clase vaya incluida en un único fichero pero claro está, nos puede interesar por algún motivo meter varias clases en un único fichero. En este caso solo puede haber una clase public que es la que dará el nombre a dicho fichero. En caso de que no hubiese una clase public el compilador entenderá que la clase "principal" de ese fichero es la que concuerda con el nombre del mismo, por lo que evidentemente dos clases con un mismo nombre no son permitidas en un mismo fichero.

Para explicar la estructura de la clase, primero se suelen declarar, al menos, las variables internas de esa clase y posteriormente se definen los constructores y los métodos que dispondrá la clase.  
En la definición de constructores y métodos tenemos que tener en cuenta un nuevo concepto de la programación orientada a objetos. La sobrecarga. La sobrecarga consiste en poder tener varios métodos o constructores con el mismo nombre dentro de una misma clase y que no hagan las mismas cosas. Esto se consigue diferenciando entre ellos el número y tipo de parámetros que reciben.

~~~~ java
float obtenerAreaCirculo(Circulo ci) {
   /* ... */
}

float obtenerAreaCuadrado(Cuadrado cu) {
   /* ... */
}

/* en Java esto se puede abreviar teniendo dos métodos sobrecargados */

float obtenerArea(Circulo ci) {
   /* ... */
}

float obtenerArea(Cuadrado cu) {
   /* ... */
}

/* A la hora de ejecutar el método obtenerArea se utilizará el que corresponda al parámetro que se le pase por cabecera */
~~~~

## ORGANIZAR CLASES
