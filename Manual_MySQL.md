# **MANUAL MySQL**

 ![MySQL](Fotos/Manual_MySQL/MySQL_logo.png)

1. **[INTRODUCCIÓN](#introducción)**
2. **[ESTRUCTURA DE TABLAS](#estructura-de-tablas)**
    1. **[Tipos de campo](#tipos-de-campo)**
    2. **[Tipos de datos](#tipos-de-datos)**
    3. **[Tipos de sentencias y sus componentes sintácticos](#tipos-de-sentencias-y-sus-componentes-sintácticos)**
3. **[INSERCCIÓN Y MODIFICACIÓN DE DATOS](#insercción-y-modificación-de-datos)**
    1. **[Creación de tablas](#creación-de-tablas)**
    2. **[Estructuras de las tablas](#estructuras-de-las-tablas)**
    3. **[Añadir un nuevo registro](#añadir-un-nuevo-registro)**
    4. **[Borrar un registro](#borrar-un-registro)**
    5. **[Actualizar un registro](#actualizar-un-registro)**
4. **[BÚSQUEDA Y SELECCIÓN DE DATOS](#búsqueda-y-selección-de-datos)**
    1. **[Selección de tablas](#selección-de-tablas)**
    2. **[Consultas de selección](#consultas-de-selección)**
    3. **[Criterios de selección](#criterios-de-selección)**
    4. **[Subconsultas](#subconsultas)**
    5. **[Consultas de Unión Internas](#consultas-de-unión-internas)**
    6. **[Consultas de Unión Externas](#consultas-de-unión-externas)**
    7. **[Consultas de acción](#consultas-de-acción)**
    8. **[Optimizar prestaciones](#optimizar-prestaciones)**
    9. **[Trucos-prácticos](#trucos-prácticos)**
5. **[FUNCIONES](#funciones)**
    1. **[Funciones para búsquedas con fechas en Access](#funciones-para-búsquedas-con-fechas-en-access)**
    2. **[La función datepart() en Access](#la-función-datepart()-en-access)**
6. **[SQL SERVER O PL/SQL](#sql-server-o-pl/sql)**
    1. **[Cursores](#cursores)**
    2. **[Emular un Cursor con un Bucle](#emular-un-cursor-con-un-bucle)**
    3. **[Procedures y búsqueda de registros duplicados](#procedures-y-búsqueda-de-registros-duplicados)**
    4. **[Referencias Cruzadas](#referencias-cruzadas)**
    5. **[Introducción a freetext y contains en SQL-Server](#introducción-a-freetext-y-contains-en-sql-server)**
    6. **[Introducción a los Índices en MySQL](#introducción-a-los-índices-en-mysql)**
    7. **[Consultas e índices de texto](#consultas-e-índices-de-texto)**
    8. **[Consultas con parámetros y omisión de permisos](#consultas-con-parámetros-y-omisión-de-permisos)**
    9. **[Acceso a base de datos externas](#acceso-a-base-de-datos-externas)**
    10. **[Crear una cadena de conexión para SQL Server](#crear-una-cadena-de-conexión-para-sql-server)**


## INTRODUCCIÓN
---
MySQL es un sistema de administración de bases de datos (Database Management System, DBMS) para bases de datos relacionales *open source* que permite gestionar archivos llamados de bases de datos.

Existen muchos tipos de bases de datos, desde un simple archivo hasta sistemas relacionales orientados a objetos.
MySQL, como base de datos relacional, utiliza múltiples tablas para almacenar y organizar la información.

MySQL fue escrito en C y C++ y destaca por su gran adaptación a diferentes entornos de desarrollo, permitiendo su
interacción con los lenguajes de programación más utilizados como PHP, Perl y Java y su integración en distintos
sistemas operativos.

Éste permite crear base de datos y tablas, insertar datos, modificarlos, eliminarlos, ordenarlos, hacer consultas y realizar
muchas operaciones. Ingresando instrucciones en la línea de comandos o embebidas en un lenguaje como PHP nos
comunicamos con el servidor. 


## ESTRUCTURA DE TABLAS
---
### Tipos de campo
Como sabemos, una base de datos esta compuesta de tablas donde almacenamos registros catalogados en función de distintos campos (características).  
Un aspecto previo a considerar es la naturaleza de los valores que introducimos en esos campos. Dado que una base de datos trabaja con todo tipo de informaciones, es importante especificarle qué tipo de valor le estamos introduciendo de manera a, por un lado, facilitar la búsqueda posteriormente y por otro, optimizar los recursos de memoria.

Cada base de datos introduce tipos de valores de campo que no necesariamente están presentes en otras. Sin embargo, existe un conjunto de tipos que están representados en la totalidad de estas bases. Estos tipos comunes son los siguientes:

|Tipo de dato|Comentario|
|:-:|:-|
|**Alfanuméricos**|Cifras y letras. Presentan una longitud limitada: 255 caracteres.|
|**Numéricos**|Varios tipos, principalmente enteros (sin decimales) y reales (con decimales).|
|**Booleanos**|Verdadero o Falso.|
|**Fechas**|Almacenan fechas facilitando posteriormente su explotación. Almacenar fechas de esta forma posibilita ordenar los registros por fechas o calcular los días entre una fecha y otra.|
|**Memos**|Campos alfanuméricos de longitud ilimitada. Presentan el inconveniente de no poder ser indexados.|
|**Autoincrementables**|Campos numéricos enteros que incrementan en una unidad su valor para cada registro incorporado para servir de identificador, ya que resultan exclusivos de un registro.|

### Tipos de datos
#### Numéricos

|Tipo de dato|Almacenamiento (bytes)|Min. valor (sin signo)|Max. valor (sin signo)|Min. valor (con signo)|Max. valor (con signo)|
| :- | :-: | :- | :- | :- | :- |
|TINYINT|1|0|255|-128 |127|
|SMALLINT|2|0|65.535|-32.768|32.767|
|MEDIUMINT|3|0|16.777.215|-8.388.608|8.388.607|
|INT / INTEGER|4|0|4294927295|-2.147.483.648|2.147.483.647|
|BIGINT|8|0|2^64^ - 1|-2^63^|2^63^ - 1|

> :memo: Los atributos UNSIGNED / sin signo:
>> ✅ Rango de valores ampliado.
>
>> ✅ Rendimiento mejorado: Las columnas numéricas requieren menos bits para su representación en comparación con sus contrapartes con signo.
>
>> ❌ Posible desbordamiento: Intentar insertar un valor mayor que el rango permitido provocará un desbordamiento, lo que provocará el truncamiento del valor, reduciendo el valor a 0. 
>
>> ❌ Compatibilidad: Es fundamental tener en cuenta que no todos los sistemas de bases de datos admiten el atributo UNSIGNED. Si requiere compatibilidad con múltiples sistemas de bases de datos, es recomendable evitar el uso del atributo UNSIGNED.

|Tipo de dato|Almacenamiento (bytes)|Rango de valores|
| :- | :-: | :- |
|BOOL / BIT|1|0|1|
|FLOAT / FLOAT (0-24)|4|-3.402823466E+38 - -1.175494351E-38; 0; 1.175494351E-38 - 3.402823466E+38|
|DOUBLE / FLOAT(25-53)|8|-1.7976931348623157E+308 - -2.2250738585072014E-308; 0; 2.2250738585072014E-308 - 1.7976931348623157E+308|

#### Cadenas / Textos
|Tipo de dato|Almacenamiento (bytes)|Descripción|Rango (caracteres)|
| :- | :-: | :- | :- |
|CHAR(n)|n|Almacena una cadena de longitud fija.|255|
|VARVHAR(n)|n + 1|Almacena una cadena de longitud variable.|255|
|TINYTEXT / TINYBLOB|longitud + 1|-|255|
|TEXT / BLOB|longitud + 2|-|65.535|
|MEDIUMTEXT / MEDIUMBLOB|longitud + 3|-|16.777.215|
|LONGTEXT / LONGBLOB|longitud + 4|-|4.294.967.295|
|ENUM(val1, val2, ...)|1 ó 2 dependiendo del número de valores|Lista|65.535 valores distintos|
|SET(val1, val2, ...)|1, 2, 3, 4 ó 8, dependiendo del número de valores|Lista|64 valores distintos|

> :bulb: La diferencia entre TEXT y BLOB (*Binary large Object*) es el tratamiento que reciben a la hora de realizar ordenamientos y comparaciones. 
> - TEXT se ordena sin tener en cuenta las mayúsculas y las minúsculas.
> - Los tipos BLOB se utilizan para almacenar datos binarios como pueden ser ficheros.

#### Fechas
|Tipo de dato|Almacenamiento (bytes)|Rango|
| :-: | :-: | :-: |
|DATE|3|01/01/1001 - 31/12/9999|
|DATETIME|8|01/01/1001 00:00:00 - 31/12/9999 23:59:59|
|TIMESTAMP|4|01/01/1970 00:00:00 - 31/12/2037 23:59:59|
|TIME|3|-838:59:59 - 838:59:59|
|YEAR|1|1901 - 2155|

> :warning: Mysql no comprueba de una manera estricta si una fecha es válida o no. Simplemente comprueba que el mes esta comprendido entre 0 y 12 y que el día esta comprendido entre 0 y 31.

### Tipos de sentencias y sus componentes sintácticos
En SQL tenemos bastantes sentencias que se pueden utilizar para realizar diversas tareas.
Dependiendo de las tareas, estas sentencias se pueden clasificar en tres grupos principales (DML, DDL,DCL), aunque nos quedaría otro grupo que a mi entender no está dentro del lenguaje SQL sino del PLSQL.

#### DML (Data Manipulation Language)
Es el subconjunto de comandos utilizado para gestionar, consultar y modificar los datos almacenados en una base de datos relacional sin cambiar su estructura.

|Sentencia|Descripción|
|:-|:-|
|**SELECT**|Recupera datos de la base de datos.|
|**INSERT**|Añade nuevas filas de datos a la base de datos.|
|**DELETE**|Suprime filas de datos de la base de datos.|
|**UPDATE**|Modifica datos existentes en la base de datos.|

#### DDL (Data Definition Language)
Es el subconjunto utilizado para definir, modificar y eliminar la estructura (esquema) de los objetos de una base de datos, como tablas, índices y vistas. 

|Sentencia|Descripción|
|:-|:-|
|**CREATE TABLE**|Añade una nueva tabla a la base de datos.|
|**DROP TABLE**|Suprime una tabla de la base de datos.|
|**ALTER TABLE**|Modifica la estructura de una tabla existente.|
|**CREATE VIEW**|Añade una nueva vista a la base de datos.|
|**DROP VIEW**|Suprime una vista de la base de datos.|
|**CREATE INDEX**|Construye un índice para una columna.|
|**DROP INDEX**|Suprime el índice para una columna.|
|**CREATE SYNOYM**|Define un alias para un nombre de tabla.|
|**DROP SYNONYM**|Suprime un alias para un nombre de tabla.|

#### DCL (Data Control Language)
Es el subconjunto de comandos utilizado para controlar el acceso a los datos y la gestión de transacciones en una base de datos relacional.

|Sentencia|Descripción|
|:-|:-|
|**GRANT**|Concede privilegios de acceso a usuarios.|
|**REVOKE**|Suprime privilegios de acceso a usuarios.|
|**COMMIT**|Finaliza la transacción actual.|
|**ROLLBACK**|Aborata la transacción actual.|

#### PL/SQL (Procedural Language/SQL)
Es un lenguaje de programación procedural que se utiliza para escribir procedimientos almacenados, funciones y triggers en bases de datos Oracle. PL/SQL es una extensión de SQL que permite la programación estructurada y el control de flujo, lo que facilita la creación de aplicaciones más complejas y eficientes.

|Sentencia|Descripción|
|:-|:-|
|**DECLARE**|Define un cursor para una consulta.|
|**OPEN**|Abre un cursor para recuperar resultados de consulta.|
|**FETCH**|Recupera una fila de resultados de consulta.|
|**CLOSE**|Cierra un cursor.|

#### Componentes sintácticos
La mayoría de sentencias SQL tienen la misma estructura.  
Todas comienzan por un verbo (select, insert, update, create), a continuación le sigue una o más clausulas que nos dicen los datos con los que vamos a operar (from, where), algunas de estas son opcionales y otras obligatorias como es el caso del from.

~~~~ SQL
SELECT   nombre_columna1
       , nombre_columna2
       , ...
  FROM nombre_tabla
 WHERE condición1
       AND condición2
       OR ...
 ORDER BY   nombre_columnaX ASC
          , nombre_columnaY DESC
          , ...
~~~~


## INSERCCIÓN Y MODIFICACIÓN DE DATOS
---
### Creación de tablas
Para crear una tabla debemos especificar diversos datos: 
1. El nombre que le queremos asignar.
2. Los nombres de los campos y sus características. 
3. Puede ser necesario especificar cuáles de estos campos van a ser índices y de qué tipo van a serlo.

La sintaxis de creación puede variar ligeramente de una base de datos a otra ya que los tipos de campo aceptados no están completamente estandarizados.

~~~~ SQL
CREATE TABLE nombre_tabla
(
      nombre_campo1 tipo_campo1 NOT NULL PRIMARY KEY [CONSTRAINT índice1]
    , nombre_campo2 tipo_campo2 FOREIGN KEY [CONSTRAINT índice2]
    , nombre_campo3 tipo_campo3 UNIQUE [CONSTRAINT índice3]
    , nombre_campo4 tipo_campo4 [CONSTRAINT índice4]
    , ...
)
~~~~
- **nombre_tabla**: Es el nombre que se le asigna a la tabla. Debe ser único dentro de la base de datos.
- **nombre_campo**: Es el nombre que se le asigna a cada campo o columna de la tabla. Debe ser único dentro de la tabla.
- **tipo_campo**: Es el tipo de dato que se asigna a cada campo, como por ejemplo INT, VARCHAR, DATE, etc.
- **NOT NULL**: Es una restricción que indica que el campo no puede contener valores nulos (vacíos).
- **PRIMARY KEY**: Es una restricción que indica que el campo es la clave primaria de la tabla.
- **FOREIGN KEY**: Es una restricción que indica que el campo es una clave foránea que hace referencia a otra tabla.
- **UNIQUE**: Es una restricción que indica que los valores del campo deben ser únicos.
- **AUTO_INCREMENT**: Es una restricción que indica que el valor del campo se incrementará automáticamente con cada nueva fila insertada.
- **CONSTRAINT índice**: Es una cláusula opcional que se utiliza para nombrar un índice o restricción específica en la tabla.


~~~~ SQL
CREATE TABLE articulos
(
      id_articulo INT          NOT NULL  AUTO_INCREMENT PRIMARY KEY
    , titulo      VARCHAR(50)
    , autor       VARCHAR(25)
    , editorial   VARCHAR(25)
    , precio      SMALLINT(5)            UNSIGNED
    , CONSTRAINT titulo_autor  UNIQUE (titulo, autor)
)
~~~~

### Valores por defecto
En el caso de que no se introduzca un valor para un campo, éste se inicializará con un valor por defecto. Este valor por defecto puede ser especificado a la hora de crear la tabla o posteriormente mediante la instrucción ALTER TABLE.  
Si no se especifica un valor por defecto, el campo se inicializará con el valor predeterminado del tipo de dato del campo, que puede ser NULL (vacío) si el campo permite valores nulos.

~~~~ SQL
CREATE TABLE empleados
(
      id_empleado   INT          NOT NULL  AUTO_INCREMENT PRIMARY KEY
    , nombre        VARCHAR(50)  NOT NULL
    , departamento  VARCHAR(25)  NOT NULL  DEFAULT 'General'
    , salario       SMALLINT(5)  UNSIGNED  DEFAULT 1000
)
~~~~

### Valores nulos
Un valor nulo 


#### La cláusula CONSTRAINT
Se utiliza la cláusula CONSTRAINT en las instrucciones ALTER TABLE y CREATE TABLE para crear o eliminar índices.  

Para los índices de campos únicos:
~~~~ sql
CONSTRAINT nombre
{
    PRIMARY KEY | UNIQUE | REFERENCES tabla externa
    [
        columna externa1, 
        columna externa2
    ]
}
~~~~

Para los índices de campos múltiples:
~~~~ sql
CONSTRAINT nombre 
{
    PRIMARY KEY 
    (
        primario1,
        primario2,
        ...
    ) |
    UNIQUE 
    (
        único1,
        único2,
        ...
    ) |
    FOREIGN KEY
    (
        ref1, 
        ref2,
        ...
    ) REFERENCES tabla externa
    [
        campo externo1,
        campo externo2,
        ...
    ]
}
~~~~

|Campo|Descripción|
|:-|:-|
|**nombre**|Nombre del índice que se va a crear.|
|**primarioN**|Nombre del campo o de los campos que forman el índice primario.|
|**únicoN**|Nombre del campo o de los campos que forman el índice de clave única.|
|**refN**|Nombre del campo o de los campos que forman el índice externo (hacen referencia a campos de otra tabla).|
|**tabla externa**|Nombre de la tabla que contiene el campo o los campos referenciados en refN.|
|**campos externos**|Nombre del campo o de los campos de la tabla externa especificados por ref1, ref2,... , refN.|

Si se desea crear un índice para un campo cuando se esta utilizando las instrucciones ALTER TABLE o CREATE TABLE la cláusula CONTRAINT debe aparecer inmediatamente después de la especificación del campo indexado.

Si se desea crear un índice con múltiples campos cuando se está utilizando las instrucciones ALTER TABLE o CREATE TABLE la cláusula CONSTRAINT debe aparecer fuera de la cláusula de creación de tabla.

|Índice|Descripción|
|:-|:-|
|**UNIQUE**|Genera un índice de clave única. Lo que implica que los registros de la tabla no pueden contener el mismo valor en los campos indexados.|
|**PRIMARY KEY**|Genera un índice primario el campo o los campos especificados. Todos los campos de la clave principal deben ser únicos y no nulos, cada tabla sólo puede contener una única clave principal.|
|**FOREIGN KEY**|Genera un índice externo (toma como valor del índice campos contenidos en otras tablas). Si la clave principal de la tabla externa consta de más de un campo, se debe utilizar una definición de índice de múltiples campos, listando todos los campos de referencia, el nombre de la tabla externa, y los nombres de los campos referenciados en la tabla externa en el mismo orden que los campos de referencia listados. Si los campos referenciados son la clave principal de la tabla externa, no tiene que especificar los campos referenciados, predeterminado por valor, el motor Jet se comporta como si la clave principal de la tabla externa estuviera formada por los campos referenciados.|

#### Creación de Índices
Si se utiliza el motor de datos Jet de Microsoft sólo se pueden crear índices en bases de datos del mismo motor. La sintaxis para crear un índice en ua tabla ya definida en la siguiente:
~~~~ sql
CREATE [UNIQUE] INDEX índice ON Tabla 
(
    columna1 [ASC|DESC], 
    columna2 [ASC|DESC], 
    ...
) WITH 
    {
        PRIMARY | DISALLOW NULL | IGNORE NULL
    }
~~~~

|Campo|Descripción|
|:-|:-|
|índice|Nombre del índice a crear.|
|tabla|Nombre de una tabla existente en la que se creará el índice.|
|columna|Nombre del campo o lista de campos que constituyen el índice.|
|ASC\|DESC|Indica el orden de los valores de los campos ASC indica un orden ascendente (valor predeterminado) y DESC un orden descendente.|
|UNIQUE|Indica que el índice no puede contener valores duplicados.|
|DISALLOW NULL|Prohibe valores nulos en el índice.|
|IGNORE NULL|Excluye del índice los valores nulos incluidos en los campos que lo componen.|
|PRIMARY|Asigna al índice la categoría de clave principal, en cada tabla sólo puede existir un único índice que sea "Clave Principal". Si un índice es clave principal implica que no puede contener valores nulos ni duplicados.|

En el caso de ACCESS, se puede utilizar CREATE INDEX para crear un pseudo índice sobre una tabla adjunta en una fuente de datos ODBC tal como SQL Server que no tenga todavía un índice. No necesita permiso o tener acceso a un servidor remoto para crear un pseudo índice, además la base de datos remota no es consciente y no es afectada por el pseudo índice. Se utiliza la misma sintaxis para las tablas adjuntas que para las originales. Esto es especialmente útil para crear un índice en una tabla que sería de sólo lectura debido a la falta de un índice.

#### Modificar el Diseño de una Tabla
Modifica el diseño de una tabla ya existente, se pueden modificar los campos o los índices existentes. Su sintaxis es:
~~~~ sql
ALTER TABLE tabla
{
    ADD
    {
        COLUMN tipo(tamaño) [CONSTRAINT indice]
    } CONSTRAINT índice multicampo|
    DROP
    {
        COLUMN columna | CONSTRAINT nombre del índice
    }
}
~~~~

|Campo|Descripción|
|:-|:-|
|tabla|Es el nombre de la tabla que se desea modificar.|
|columna|Es el nombre de la columna que se va a añadir o eliminar.|
|tipo|Es el tipo de campo que se va a añadir.|
|tamaño|Es el tamaño del campo que se va a añadir (sólo para campos de texto).|
|índice|Es el nombre del índice del campo (cuando se crean campos) o el nombre del índice de la tabla que se desea eliminar.|
|índice multicampo|Es el nombre del índice del campo multicampo (cuando se crean campos) o el nombre del índice de la tabla que se desea eliminar.|

|Operación|Descripción|
|:-|:-|
|ADD COLUMN|Añadir un nuevo campo a la tabla, indicando el nombre, el tipo de campo y opcionalmente el tamaño (para campos de tipo texto).|
|ADD|Agregar un índice de multicampos o de un único campo.|
|DROP COLUMN|Borrar un campo. Se especifica únicamente el nombre del campo.|
|DROP|Eliminar un índice. Se especifica únicamente el nombre del índice a continuación de la palabra reservada CONSTRAINT.|

##### Ejemplo 1
~~~~ sql
ALTER TABLE Empleados 
 ADD COLUMN Salario CURRENCY
~~~~
> Agrega un campo Salario de tipo Moneda a la tabla Empleados.

##### Ejemplo 2
~~~~ sql
ALTER TABLE Empleados 
DROP COLUMN Salario
~~~~
> Elimina el campo Salario de la tabla Empleados.

##### Ejemplo 3
~~~~ sql
   ALTER TABLE Pedidos 
ADD CONSTRAINT RelacionPedidos 
   FOREIGN KEY
   (
    IdEmpleado
    ) REFERENCES Empleados
      (
        IdEmpleado
      )
~~~~
> Agrega un índice externo a la tabla Pedidos. El índice externo se basa en el campo IdEmpleado y se refiere al campo IdEmpleado de la tabla Empleados. En este ejemplo no es necesario indicar el campo junto al nombre de la tabla en la cláusula REFERENCES, pues ID_Empleado es la clave principal de la tabla Empleados.

##### Ejemplo 4
~~~~ sql
ALTER TABLE Pedidos DROP CONSTRAINT RelacionPedidos
~~~~
> Elimina el índice de la tabla Pedidos.


### Añadir un nuevo registro
Los registros pueden ser introducidos a partir de sentencias que emplean la instrucción INSERT.
La sintaxis utilizada es la siguiente:
~~~~ sql
INSERT INTO nombre_tabla (nombre_columna1, nombre_columna2, ...) 
     VALUES (valor_campo1, valor_campo2, ...)
~~~~

No es imprescindible rellenar todos los campos del registro. Pero puede ser que determinados campos sean necesarios. Estos campos necesarios pueden ser definidos cuando construimos nuestra tabla mediante la base de datos.
> ⚠️ Si no insertamos uno de los campos en la base de datos se inicializará con el valor por defecto que hayamos definido a la hora de crear la tabla. Si no hay valor por defecto, probablemente se inicialice como NULL (vacío), en caso de que este campo permita valores nulos. Si ese campo no permite valores nulos (eso se define también al crear la tabla) lo más seguro es que la ejecución de la sentenca SQL nos de un error.

### Borrar un registro
Para borrar un registro nos servimos de la instrucción DELETE. En este caso debemos especificar cual o cuales son los registros que queremos borrar. Es por ello necesario establecer una selección que se llevara a cabo mediante la cláusula WHERE.  
La forma de seleccionar se verá detalladamente en capítulos posteriores. Por ahora nos contentaremos de mostrar cuál es el tipo de sintaxis utilizado para efectuar estas supresiones:
~~~~ sql
DELETE FROM nombre_tabla 
      WHERE condiciones_de_selección
~~~~

> ⚠️ Hay que tener cuidado con esta instrucción ya que si no se especifica una condición con WHERE, se borrará todo la tabla.

### Actualizar un registro
UPDATE es la instrucción del lenguaje SQL que nos sirve para modificar los registros de una tabla. Como para el caso de DELETE, necesitamos especificar por medio de WHERE cuáles son los registros en los que queremos hacer efectivas nuestras modificaciones. Además, obviamente, tendremos que especificar cuáles son los nuevos valores de los campos que deseamos actualizar.

La sintaxis es de este tipo:
~~~~ sql
UPDATE nombre_tabla 
   SET nombre_columna1 = valor_campo1, nombre_columna2 = valor_campo2,... 
 WHERE condiciones_de_selección
~~~~


## BÚSQUEDA Y SELECCIÓN DE DATOS
---
### Selección de tablas
La selección total o parcial de una tabla se lleva a cabo mediante la instrucción SELECT. En dicha selección hay que especificar (como mínimo):
- Los campos que queremos seleccionar.
- La tabla en la que hacemos la selección.

Aparte, también se pueden añadir las claúsulas: 
- WHERE (para las condiciones de búsqueda)
- ORDER BY (para especificar el orden en el que se ordenan los campos por cada columna introducida) [de forma ascendente de forma predeterminada]

~~~~ sql
SELECT nombre_columna1, nombre_columna2, ...
  FROM nombre_tabla
 WHERE condiciones_de_selección
 ORDER BY nombre_columnaX [DESC], nombre_columnaY [DESC], ...
~~~~

Si quisiésemos seleccionar todos los campos de la tabla:
~~~~ sql
SELECT * FROM nomnbre_tabla
~~~~

También se puede efectuar selecciones sin coincidencia, es decir, que no se repitan líneas totalmente iguales.
~~~~ sql
SELECT DISTINCT *
  FROM nombre_tabla
~~~~

### Consultas de selección

### Criterios de selección

### Subconsultas

### Consultas de Unión Internas

### Consultas de Unión Externas

### Consultas de acción

### Optimizar prestaciones

### Trucos prácticos


## FUNCIONES
---
### Funciones para búsquedas con fechas en Access

### La función datepart() en Access


## SQL SERVER O PL/SQL
---
### Cursores

### Emular un Cursor con un Bucle

### Procedures y búsqueda de registros duplicados

### Referencias Cruzadas

### Introducción a freetext y contains en SQL-Server

### Introducción a los Índices en MySQL

### Consultas e índices de texto

### Consultas con parámetros y omisión de permisos

### Acceso a base de datos externas

### Crear una cadena de conexión para SQL Server
