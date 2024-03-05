# **MANUAL SQL**

1. **[INTRODUCCIÓN](#introducción)**
    1. **[Tipos de campo](#tipos-de-campo)**
    2. **[Tipos de datos](#tipos-de-datos)**
    3. **[Tipos de sentencias y sus componentes sintácticos](#tipos-de-sentencias-y-sus-componentes-sintácticos)**
2. **[INSERCCIÓN Y MODIFICACIÓN DE DATOS](#insercción-y-modificación-de-datos)**
    1. **[Creación de tablas](#creación-de-tablas)**
    2. **[Estructuras de las tablas](#estructuras-de-las-tablas)**
    3. **[Añadir un nuevo registro](#añadir-un-nuevo-registro)**
    4. **[Borrar un registro](#borrar-un-registro)**
    5. **[Actualizar un registro](#actualizar-un-registro)**
3. **[BÚSQUEDA Y SELECCIÓN DE DATOS](#búsqueda-y-selección-de-datos)**
    1. **[Selección de tablas](#selección-de-tablas)**
    2. **[Consultas de selección](#consultas-de-selección)**
    3. **[Criterios de selección](#criterios-de-selección)**
    4. **[Subconsultas](#subconsultas)**
    5. **[Consultas de Unión Internas](#consultas-de-unión-internas)**
    6. **[Consultas de Unión Externas](#consultas-de-unión-externas)**
    7. **[Consultas de acción](#consultas-de-acción)**
    8. **[Optimizar prestaciones](#optimizar-prestaciones)**
    9. **[Trucos-prácticos](#trucos-prácticos)**
4. **[FUNCIONES](#funciones)**
    1. **[Funciones para búsquedas con fechas en Access](#funciones-para-búsquedas-con-fechas-en-access)**
    2. **[La función datepart() en Access](#la-función-datepart()-en-access)**
5. **[SQL SERVER O PL/SQL](#sql-server-o-pl/sql)**
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


## **[^](#manual-sql)**
## INTRODUCCIÓN
---
### **[^](#manual-sql)**
### Tipos de campo
Como sabemos una base de datos esta compuesta de tablas donde almacenamos registros catalogados en función de distintos campos (características).  
Un aspecto previo a considerar es la naturaleza de los valores que introducimos en esos campos. Dado que una base de datos trabaja con todo tipo de informaciones, es importante especificarle qué tipo de valor le estamos introduciendo de manera a, por un lado, facilitar la búsqueda posteriormente y por otro, optimizar los recursos de memoria.

Cada base de datos introduce tipos de valores de campo que no necesariamente están presentes en otras. Sin embargo, existe un conjunto de tipos que están representados en la totalidad de estas bases. Estos tipos comunes son los siguientes:

|Tipo de dato|Comentario|
|:-:|:-|
|**Alfanuméricos**|Cifras y letras. Presentan una longitud limitada: 255 caracteres.|
|**Numéricos**|Varios tipos, principalmente, enteros (sin decimales) y reales (con decimales).|
|**Booleanos**|Verdadero ó Falso.|
|**Fechas**|Almacenan fechas facilitando posteriormente su explotación. Almacenar fechas de esta forma posibilita ordenar los registros por fechas o calcular los días entre una fecha y otra.|
|**Memos**|Campos alfanuméricos de longitud ilimitada. Presentan el inconveniente de no poder ser indexados.|
|**Autoincrementables**|Campos numéricos enteros que incrementan en una unidad su valor para cada registro incorporado para servir de identificador, ya que resultan exclusivos de un registro.|

### **[^](#manual-sql)**
### Tipos de datos
Los tipos de datos SQL se clasifican en 13 tipos de datos primarios y de varios sinónimos válidos reconocidos por dichos tipos de datos. Los tipos de datos primarios son:

|Tipo de dato|Longitud|Valores|
|:-:|:-|:-|
|**BINARY**|1 byte|Para consultas sobre tabla adjunta de productos de bases de datos que definen un tipo de datos Binario.|
|**BIT**|1 byte|Si/No ó True/False.|
|**BYTE**|1 byte|Entero: 0 a 255.|
|**COUNTER**|4 bytes|Un número incrementado automáticamente (de tipo Long).|
|**CURRENCY**|8 bytes|Entero escalable: 922.337.203.685.477,5808 a 922.337.203.685.477,5807.|
|**DATETIME**|8 bytes|Fecha u hora entre los años 100 y 9999.|
|**SINGLE**|4 bytes|Punto flotante de precisión simple: -3.402823E38 a -1.401298E-45 (valores negativos), 1.401298E-45 a 3.402823E38 (valores positivos), y 0.|
|**DOUBLE**|8 bytes|Punto flotante de doble precisión: -1.79769313486232E+308 a -4.94065645841247E-324 (valores negativos), 4.94065645841247E-324 a 1.79769313486232E+308 (valores positivos), y 0.|
|**SHORT**|2 bytes|Entero corto: -32,768 a 32,767.|
|**LONG**|4 bytes|Entero largo: -2,147,483,648 a 2,147,483,647.|
|**LONGTEXT**|1 byte por carácter|0 a 1.2 GB.|
|**LONGBINARY**|Según se necesite|0 a 1 GB. Utilizado para objetos OLE.|
|**TEXT**|1 byte por carácter|0 a 255 caracteres.|

La siguiente tabla recoge los sinónimos de los tipos de datos definidos:

|Tipo de dato|Sinónimo|
|:-|:-|
|BINARY|VARBINARY|
|BIT|BOOLEAN - LOGICAL - LOGICAL1 - YESNO|
|BYTE|INTEGER1|
|COUNTER|AUTOINCREMENT|
|CURRENCY|MONEY|
|DATETIME|DATE - TIME - TIMESTAMP|
|SINGLE|FLOAT4 - IEEESINGLE - REAL|
|DOUBLE|FLOAT - FLOAT8 - IEEEDOUBLE - NUMBER - NUMERIC|
|SHORT|INTEGER2 - SMALLINT|
|LONG|INT - INTEGER - INTEGER4|
|LONGBINARY|GENERAL - OLEOBJECT|
|LONGTEXT|LONGCHAR - MEMO - NOTE|
|TEXT|ALPHANUMERIC - CHAR - CHARACTER - STRING - VARCHAR|
|VARIANT(No admitido)|VALUE|

### **[^](#manual-sql)**
### Tipos de sentencias y sus componentes sintácticos
En SQL tenemos bastantes sentencias que se pueden utilizar para realizar diversas tareas.
Dependiendo de las tareas, estas sentencias se pueden clasificar en tres grupos principales (DML, DDL,DCL), aunque nos quedaría otro grupo que a mi entender no está dentro del lenguaje SQL sino del PLSQL.

||Sentencia|Descripción|
|:-:|:-|:-|
|**DML**|**Manipulación de datos**||
||SELECT|Recupera datos de la base de datos.|
||INSERT|Añade nuevas filas de datos a la base de datos.|
||DELETE|Suprime filas de datos de la base de datos.|
||UPDATE|Modifica datos existentes en la base de datos.|
|**DDL**|**Definición de datos**||
||CREATE TABLE|Añade una nueva tabla a la base de datos.|
||DROP TABLE|Suprime una tabla de la base de datos.|
||ALTER TABLE|Modifica la estructura de una tabla existente.|
||CREATE VIEW|Añade una nueva vista a la base de datos.|
||DROP VIEW|Suprime una vista de la base de datos.|
||CREATE INDEX|Construye un índice para una columna.|
||DROP INDEX|Suprime el índice para una columna.|
||CREATE SYNOYM|Define un alias para un nombre de tabla.|
||DROP SYNONYM|Suprime un alias para un nombre de tabla.|
|**DCL**|**Control de acceso**||
||GRANT|Concede privilegios de acceso a usuarios.|
||REVOKE|Suprime privilegios de acceso a usuarios.|
||**Control de transacciones**||
||COMMIT|Finaliza la transacción actual.|
||ROLLBACK|Aborata la transacción actual.|
|**PLSQL**|**SQL Programático**||
||DECLARE|Define un cursor para una consulta.|
||OPEN|Abre un cursor para recuperar resultados de consulta.|
||FETCH|Recupera una fila de resultados de consulta.|
||CLOSE|Cierra un cursor.|

#### Componentes sintácticos
La mayoría de sentencias SQL tienen la misma estructura.  
Todas comienzan por un verbo (select, insert, update, create), a continuación le sigue una o más clausulas que nos dicen los datos con los que vamos a operar (from, where), algunas de estas son opcionales y otras obligatorias como es el caso del from.

![](https://desarrolloweb.com/articulos/images/componentes-sentencia-sql.gif)


## **[^](#manual-sql)**
## INSERCCIÓN Y MODIFICACIÓN DE DATOS
---
### **[^](#manual-sql)**
### Creación de tablas
En general, la mayoría de las bases de datos poseen potentes editores de bases que permiten la creación rápida y sencilla de cualquier tipo de tabla con cualquier tipo de formato.

Sin embargo, una vez la base de datos está alojada en el servidor, puede darse el caso de que queramos introducir una nueva tabla ya sea con carácter temporal (para gestionar un carrito de compra por ejemplo) o bien permanente por necesidades concretas de nuestra aplicación.

En estos casos, podemos, a partir de una sentencia SQL, crear la tabla con el formato que deseemos lo cual nos puede ahorrar más de un quebradero de cabeza.

Este tipo de sentencias son especialmente útiles para bases de datos como Mysql, las cuales trabajan directamente con comandos SQL y no por medio de editores.

Para crear una tabla debemos especificar diversos datos: El nombre que le queremos asignar, los nombres de los campos y sus características. Además, puede ser necesario especificar cuáles de estos campos van a ser índices y de qué tipo van a serlo.

La sintaxis de creación puede variar ligeramente de una base de datos a otra ya que los tipos de campo aceptados no están completamente estandarizados.

A continuación os explicamos someramente la sintaxis de esta sentencia y os proponemos una serie de ejemplos prácticos:

#### Sintaxis
~~~~ sql
CREATE TABLE nombre_tabla
(
    nombre_campo_1 tipo_dato_1,
    nombre_campo_2 tipo_dato_2,
    nombre_campo_n tipo_dato_n,
    KEY(campo_x,...)
)
~~~~

##### Ejemplo
~~~~ sql
CREATE TABLE articulos
(
    id_articulo INT(4) NOT NULL AUTO_INCREMENT,
    titulo      VARCHAR(50),
    autor       VARCHAR(25),
    editorial   VARCHAR(25),
    precio      REAL,
    KEY(id_articulo)
)
~~~~

En este caso puede verse que los campos alfanuméricos son introducidos de la misma forma que los numéricos.

Muchas son las opciones que se ofrecen al generar tablas. Algunos de los tipos de campos que pueden ser empleados en la creación de tablas con sus características:

#### Tipos de campos
|Tipo|Bytes|Descripción|
|:-:|:-:|:-|
|INT / INTEGER|4|Números enteros. Existen otros tipos de mayor o menor longitud específicos de cada base de datos.|
|DOUBLE / REAL|8|Números reales (grandes y con decimales). Permiten almacenar todo tipo de número no entero.|
|CHAR|1/carácter|Alfanuméricos de longitud fija predefinida.|
|VARCHAR|1/carácter + 1|Alfanuméricos de longitud variable.|
|DATE|3|Fechas, existen multiples formatos específicos de cada base de datos.|
|BLOB|1/carácter + 2|Grandes textos no indexables.|
|BIT / BOOLEAN|1|Almacenan un bit de información (verdadero o falso).|

### **[^](#manual-sql)**
### Estructuras de las tablas
En la terminología usada en SQL no se alude a las relaciones, del mismo modo que no se usa el término atributo, pero sí la palabra columna, y no se habla de tupla, sino de línea.

#### Creación de tablas nuevas
~~~~ sql
CREATE TABLE tabla 
(
    columna tipo (tamaño) índice,
    ...,
    índice multicampo,
    ...
)
~~~~

|Campo|Descripción|
|:-|:-|
|tabla|Nombre de la tabla que se va a crear.|
|columna|Nombres de las columnas que se van a crear en la nueva tabla. La nueva tabla debe contener al menos una columna.|
|tipo|Tipo de dato de columna en la nueva tabla.|
|tamaño|Tamaño del campo (sólo se aplica para campos de tipo texto).|
|índice|Cláusula CONSTRAINT que define el tipo de índice a crear (opcional).|
|índice multicampo|Cláusula CONSTRAINT que define el tipo de índice multicampo a crear. Un índice multicampo es aquel que está indexado por el contenido de varios campos (opcional).|

##### Ejemplo 1
~~~~ sql
CREATE TABLE Empleados
(
   Nombre          TEXT (10),
   Apellidos       TEXT,
   FechaNacimiento DATETIME
) CONSTRAINT IndiceGeneral UNIQUE
    (
        Nombre, Apellidos, FechaNacimiento
    )
~~~~
> Nueva tabla llamada Empleados con un campo Nombre de tipo texto y longitud 10, otro con llamado Apellidos de tipo texto y longitud predeterminada (50) y otro llamado FechaNacimiento de tipo Fecha/Hora.  

> Se crea un índice único - no permite valores repetidos - formado por los tres campos.

##### Ejemplo 2
~~~~ sql
CREATE TABLE Empleados
(
    IdEmpleado      INTEGER CONSTRAINT IndicePrimario PRIMARY,
    Nombre          TEXT,
    Apellidos       TEXT,
    FechaNacimiento DATETIME
)
~~~~
> Nueva tabla llamada Empleados con un campo Nombre de tipo texto de longitud predeterminada (50) y otro igual llamado Apellidos, crea otro campo llamado FechaNacimiento de tipo Fecha/Hora y el campo IdEmpleado de tipo entero el que establece como clave principal.

#### La cláusula CONSTRAINT
Se utiliza la cláusula CONSTRAINT en las instrucciones ALTER TABLE y CREATE TABLE para crear o eliminar índices.  

Existen dos sintaxis para esta cláusula dependiendo si desea Crear ó Eliminar un índice de un único campo o si se trata de un campo multiíndice. Si se utiliza el motor de datos de Microsoft, sólo podrá utilizar esta cláusula con las bases de datos propias de dicho motor. 

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
|UNIQUE|Genera un índice de clave única. Lo que implica que los registros de la tabla no pueden contener el mismo valor en los campos indexados.|
|PRIMARY KEY|Genera un índice primario el campo o los campos especificados. Todos los campos de la clave principal deben ser únicos y no nulos, cada tabla sólo puede contener una única clave principal.|
|FOREIGN KEY|Genera un índice externo (toma como valor del índice campos contenidos en otras tablas). Si la clave principal de la tabla externa consta de más de un campo, se debe utilizar una definición de índice de múltiples campos, listando todos los campos de referencia, el nombre de la tabla externa, y los nombres de los campos referenciados en la tabla externa en el mismo orden que los campos de referencia listados. Si los campos referenciados son la clave principal de la tabla externa, no tiene que especificar los campos referenciados, predeterminado por valor, el motor Jet se comporta como si la clave principal de la tabla externa estuviera formada por los campos referenciados.|

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

##### Ejemplo 1
~~~~ sql
CREATE INDEX MiIndice ON Empleados
(
    Prefijo, 
    Telefono
)
~~~~
> Crea un índice llamado MiIndice en la tabla empleados con los campos Prefijo y Teléfono.

##### Ejemplo 2
~~~~ sql
CREATE UNIQUE INDEX MiIndice ON Empleados
(
    IdEmpleado
) WITH DISALLOW NULL
~~~~
> Crea un índice en la tabla Empleados utilizando el campo IdEmpleado, obligando que el campo IdEmpleado no contenga valores nulos ni repetidos.

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


### **[^](#manual-sql)**
### Añadir un nuevo registro
Los registros pueden ser introducidos a partir de sentencias que emplean la instrucción INSERT.
La sintaxis utilizada es la siguiente:
~~~~ sql
INSERT INTO nombre_tabla (nombre_columna1, nombre_columna2, ...) 
     VALUES (valor_campo1, valor_campo2, ...)
~~~~

No es imprescindible rellenar todos los campos del registro. Pero puede ser que determinados campos sean necesarios. Estos campos necesarios pueden ser definidos cuando construimos nuestra tabla mediante la base de datos.
> ⚠️ Si no insertamos uno de los campos en la base de datos se inicializará con el valor por defecto que hayamos definido a la hora de crear la tabla. Si no hay valor por defecto, probablemente se inicialice como NULL (vacío), en caso de que este campo permita valores nulos. Si ese campo no permite valores nulos (eso se define también al crear la tabla) lo más seguro es que la ejecución de la sentenca SQL nos de un error.


### **[^](#manual-sql)**
### Borrar un registro
Para borrar un registro nos servimos de la instrucción DELETE. En este caso debemos especificar cual o cuales son los registros que queremos borrar. Es por ello necesario establecer una selección que se llevara a cabo mediante la cláusula WHERE.  
La forma de seleccionar se verá detalladamente en capítulos posteriores. Por ahora nos contentaremos de mostrar cuál es el tipo de sintaxis utilizado para efectuar estas supresiones:
~~~~ sql
DELETE FROM nombre_tabla 
      WHERE condiciones_de_selección
~~~~

> ⚠️ Hay que tener cuidado con esta instrucción ya que si no se especifica una condición con WHERE, se borrará todo la tabla.


### **[^](#manual-sql)**
### Actualizar un registro
UPDATE es la instrucción del lenguaje SQL que nos sirve para modificar los registros de una tabla. Como para el caso de DELETE, necesitamos especificar por medio de WHERE cuáles son los registros en los que queremos hacer efectivas nuestras modificaciones. Además, obviamente, tendremos que especificar cuáles son los nuevos valores de los campos que deseamos actualizar.

La sintaxis es de este tipo:
~~~~ sql
UPDATE nombre_tabla 
   SET nombre_columna1 = valor_campo1, nombre_columna2 = valor_campo2,... 
 WHERE condiciones_de_selección
~~~~


## **[^](#manual-sql)**
## BÚSQUEDA Y SELECCIÓN DE DATOS
---
### **[^](#manual-sql)**
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

### **[^](#manual-sql)**
### Consultas de selección
### **[^](#manual-sql)**
### Criterios de selección
### **[^](#manual-sql)**
### Subconsultas
### **[^](#manual-sql)**
### Consultas de Unión Internas
### **[^](#manual-sql)**
### Consultas de Unión Externas
### **[^](#manual-sql)**
### Consultas de acción
### **[^](#manual-sql)**
### Optimizar prestaciones
### **[^](#manual-sql)**
### Trucos prácticos


## **[^](#manual-sql)**
## FUNCIONES
---
### **[^](#manual-sql)**
### Funciones para búsquedas con fechas en Access
### **[^](#manual-sql)**
### La función datepart() en Access


## **[^](#manual-sql)**
## SQL SERVER O PL/SQL
---
### **[^](#manual-sql)**
### Cursores
### **[^](#manual-sql)**
### Emular un Cursor con un Bucle
### **[^](#manual-sql)**
### Procedures y búsqueda de registros duplicados
### **[^](#manual-sql)**
### Referencias Cruzadas
### **[^](#manual-sql)**
### Introducción a freetext y contains en SQL-Server
### **[^](#manual-sql)**
### Introducción a los Índices en MySQL
### **[^](#manual-sql)**
### Consultas e índices de texto
### **[^](#manual-sql)**
### Consultas con parámetros y omisión de permisos
### **[^](#manual-sql)**
### Acceso a base de datos externas
### **[^](#manual-sql)**
### Crear una cadena de conexión para SQL Server
