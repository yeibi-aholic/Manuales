Las expresiones regulares, también llamadas RegEx, son secuencias de caracteres que forman un patrón de búsqueda.

# Metacaracteres
Sirven para poder especificar secuencias especiales y sets.

## Clases de caracteres
|Caracter|Descripción|Ejemplo|
|:-:|:-|:-|
|[ _ ]|Un único caracter de un conjunto tanto numéricos como alfabéticos.|[abc] --> a or b or c|
|[ \_-_ ]|Un rango de caracteres.|[a-z] / [B-W] / [3-7] / [a-zA-Z0-9]|
|[ ^_ ]|Un conjunto de caracteres descartado.|[^d-h] --> [a-ci-z]|
|.|Caracter comodin. Reemplaza cualquier caracter.||
|\\w|Caracteres alfanuméricos|Equivalente a [a-zA-z0-9_].|
|\\W|Caracteres no-alfanuméricos.|Equivalente a [^a-zA-z0-9_].|
|\\d|Caracteres numéricos.|Equivalente a [0-9].|
|\\D|Caracteres no-numéricos.|Equivalente a [^0-9].|
|\\s|Espacios, tabulaciones y saltos de línea.|Equivalente a [ \t\n\r\f\v].|
|\\S|No-espacios.|Equivalente a [^ \t\n\r\f\v].|

## Anclajes
|Caracter|Descripción|
|:-:|:-|
|^_|El texto comienza con lo especificado. Si se añade el *[flag](#flags)* /m se tendrá en cuenta en cada salto de línea.|
|_$|El texto termina con lo especificado. Si se añade el *[flag](#flags)* /m se tendrá en cuenta en cada salto de línea.|
|\\b_ or _\\b|El resultado está al comienzo o final de una palabra.|
|\\B_ or _\\B|El resultado no está al comienzo o final de una palabra.|
|\\A_|El resultado está al comienzo del texto.|
|_\\Z|El resultado está al final del texto.|

## Caracteres de escape
|Caracter|Descripción|Ejemplo|
|:-:|:-|:-|
|\\_|Secuencia especial, permite que un metacaracter funcione como caracter literal.|+*?^$\\.[]{}()\|/|
|\\000|Caracteres en formato octal. El valor debe de ser menor o igual a 255 (\\377)|\\251 --> ©; \\275 --> ½|
|\\xFF|Caracteres en formato hexadecimal.|\\xAE --> ®, \\xD8 --> Ø|
|\\uFFFF|Caracteres en formato *unicode*.|\\u00A5 --> ¥, \\u00B2 --> ²|
|\\u{FFFF}|Caracteres en formato extendido de *unicode*. Es necesario el *[flag](#flags)* /u.||
|\\t|Tabulador.||
|\\n|Salto de línea.||
|\\v|Tabulador vertical.||
|\\f|Salto de página.||
|\\r|Retorno de carro.||
|\\0|Valor *NULL*.||

## Grupos y Referencias
|Caracter|Descripción|Ejemplo|
|:-:|:-|:-|
|( _ )|Agrupación de patrones.|(ab)+ --> ab or abab or abab ab|
|(( _ ))|Subagrupación de patrones.|((ab)c)d --> Match_1: abcd ; Group_1: abc - Group_2: ab|
|\\n|Siendo *\<n>* un número entero, se repite el caracter del n-ésimo grupo.|(a(b))\1\2 --> ababb ; Group_1: ab - Group_2: b|
|(?:_)|Agrupación de patrones que se ignora.| (ab)(?:c)(d) --> Match_1: abcd ; Group_1: ab - Group_2: d|
|(?(n)\_\|_)|Si el grupo *n* hace match se recogerá el primer patrón, sino, el segundo.||
|(?<*nombre*> _ )|El grupo capturado es referenciado con el nombre *\<nombre>* especificado.|(?<A>ab) --> abc ; Group_A: ab|
|...(?=_)|Solo se tienen en cuenta los resultados que van antes de _.||
|...(?!_)|Solo se tienen en cuenta los resultados que no van antes de _.||
|(?<=_)...|Solo se tienen en cuenta los resultados que van después de _.||
|(?<!_)...|Solo se tienen en cuenta los resultados que no van después de _.||
|(?#_)|Se ignora todo lo agrupado.|abc(?# esto es un comentario) --> Match_1: abc|

## Cuantificadores y Alternación
|Caracter|Descripción|Ejemplo|
|:-:|:-|:-|
|_+|Uno o más resultados.|Equivalente a _{1,}.|
|_\*|Ninguno o más resultados.|Equivalente a _{0,}.|
|\{ _ }|Un número determinado de resultados.|a{3} --> aaa|
|\{ _, }|Un número mínimo de resultados.|a{2,} --> aa or aaa or aaaa...|
|\{ _, _ }|Un rango de resultados.|a{1,3} --> a or aa or aaa|
|_?|Resultado opcional.|Equivalente a _{0,1}.|
|_+?|Captura los menos caracteres posibles.|\d+?0 --> Hará capturas de dígitos hasta que encuentre un 0.|
|_ \| _|Para especificar que encuentre un resultado u otro.| abc\|xyz --> abc or xyz|

## Sustituciones
|Caracter|Descripción|
|:-:|:-|
|$&|Inserta el texto coincidente.|
|$n|Inserta el n-ésimo grupo capturado.|
|$`|Inserta la porción del texto coincidente antes de la captura.|
|$'|Inserta la porción del texto coincidente después de la captura.|
|$$|Inserta el símbolo *$*.|

## Flags
|Caracter|Descripción|Ejemplo|
|:-:|:-|:-|
|i|**Insensible a mayúsculas**: No se hace distinción entre mayúsculas y minúsculas, tratándolas como iguales.|/aBc/i --> aBc or abc or AbC or ...|
|g|**Búsqueda global**: Permite devolver todos las coincidencias en una misma búsqueda. Sin ella devolvería tan solo la primera coincidencia.|/a[bc]/ --> Match_1: ab - /a[bc]/g --> Match_1: ab; Match_2: ac|
|m|**Multilínea**: Permite interpretar línea por línea en vez todo el texto a la vez.||
|u|**Unicode**: Permite usar valores *unicode* extendidos.||
|s|**Valor cualquiera**: Permite que el \<.> también sirva para salto de línea.||
