Las expresiones regulares, también llamadas RegEx, son secuencias de caracteres que forman un patrón de búsqueda.

# Metacaracteres
Sirven para poder especificar secuencias especiales y sets.

## Clases de caracteres
|Caracter|Descripción|Ejemplo|
|:-:|:-|:-|
|[ _ ]|Un único caracter de un conjunto tanto numéricos como alfabéticos.|[abc] --> a or b or c|
|[ \_-_ ]|Un rango de caracteres.|[a-z] / [B-W] / [3-7] / [a-zA-Z0-9]|
|[ ^_ ]|Un conjunto de caracteres descartado.|[^d-h] --> [a-ci-z]|
|.|Caracter comodin, reemplaza cualquier caracter.||
|\\w|Caracteres alfanuméricos|Equivalente a [a-zA-z0-9_].|
|\\W|Caracteres no-alfanuméricos.|Equivalente a [^a-zA-z0-9_].|
|\\d|Caracteres numéricos.|Equivalente a [0-9].|
|\\D|Caracteres no-numéricos.|Equivalente a [^0-9].|
|\\s|Espacios, tabulaciones y saltos de línea.|Equivalente a [ \t\n\r\f\v].|
|\\S|No-espacios.|Equivalente a [^ \t\n\r\f\v].|

|Caracter|Descripción|Ejemplo|
|:-:|:-|:-|
|\{ _ }|Un número determinado de resultados.|a{3} --> aaa|
|\{ _, }|Un número mínimo de resultados.|a{2,} --> aa or aaa or aaaa...|
|\{ _, _ }|Un rango de resultados.|a{1,3} --> a or aa or aaa|
|( _ )|Agrupación de patrones.|
|(?:_)|Agrupación de patrones que se ignora.| (ab)(?:c)(d) --> Match_1: abcd ; Group_1: ab - Group_2: d|
|(( _ ))|Subagrupación de patrones.|((ab)c)d --> Match_1: abcd ; Group_1: abc - Group_2: ab|
|\\n|Siendo \<n> un número entero, se repite el caracter del n-ésimo grupo.|(a(b))\1\2 --> ababb ; Group_1: ab - Group_2: b|
|\\_|Secuencia especial, permite que un metacaracter funcione como caracter literal.|\\(\\) --> Match_1: ()|
|_ \| _|Para especificar que encuentre un resultado u otro.| abc|xyz --> abc or xyz|
|^_|Comienza con lo que le escribas.||
|_$|Termina con lo que le escribas.||
|_\*|Ninguno o más resultados.|Equivalente a _{0,}.|
|_+|Uno o más resultados.|Equivalente a _{1,}.|
|_?|Resultado opcional.|Equivalente a _{0,1}.|
|_\*?|Captura los menos caracteres posibles.|\d\*?0 --> Hará capturas de dígitos hasta que encuentre un 0.|
|(?(n)\_\|_)|Si el grupo n hace match se recogerá el primer patrón, sino, el segundo.||
|\\A_|El resultado está al comienzo del texto.||
|_\\Z|El resultado está al final del texto.||
|\\b_ or _\\b|El resultado está al comienzo o final de una palabra.||
|\\B_ or _\\B|El resultado no está al comienzo o final de una palabra.||
|...(?=_)|Solo se tienen en cuenta los resultados que van antes de _.|
|...(?!_)|Solo se tienen en cuenta los resultados que no van antes de _.|
|(?<=_)...|Solo se tienen en cuenta los resultados que van después de _.|
|(?<!_)...|Solo se tienen en cuenta los resultados que no van después de _.|
|(?#_)|Se ignora todo lo agrupado.|abc(?# esto es un comentario) --> Match_1: abc|
