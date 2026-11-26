# Investigación de metalenguajes existentes (HT-01)

**Sprint:** 1 (24 al 26 de noviembre de 2026)
**Responsables:** Jesus Armando Molina Garcia y Juan Anyelo Valberde Lopez
**Revisó:** Ebrahim Ali

Antes de escribir la gramática de Cuestiona revisamos cómo están hechos otros metalenguajes, o sea lenguajes que sirven para describir o revisar otros datos o lenguajes. Para cada uno anotamos qué describe, cómo se escribe y qué idea nos sirve. También revisamos el formato GIFT de Moodle, porque es lo más parecido a lo que queremos hacer y no queremos copiarlo.

## 1. EBNF (forma de Backus-Naur extendida)

- **Qué describe:** las reglas de cualquier lenguaje, es decir qué secuencias de palabras y símbolos están permitidas. Está estandarizada en ISO/IEC 14977.
- **Notación:** cada regla tiene un nombre, un `=` y lo que puede ir ahí. Las llaves `{ }` significan "se repite cero o más veces", los corchetes `[ ]` "es opcional" y la barra `|` "una cosa u otra".

```ebnf
numero = digito , { digito } ;
digito = "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" ;
```

- **Qué nos sirve:** es la notación que nos pide la HT-02 para escribir la gramática. Es corta y se puede leer sin instalar nada.

## 2. XML con DTD / XSD

- **Qué describe:** XML sirve para guardar datos en etiquetas, y una DTD o un XSD dicen qué etiquetas se permiten, en qué orden y cuántas veces.
- **Notación:** etiquetas que abren y cierran, y en la DTD reglas para cada elemento.

```xml
<!ELEMENT pregunta (enunciado, opcion+)>
<!ATTLIST pregunta puntos CDATA "1">
```

- **Qué nos sirve:** la idea de que un documento puede estar *bien formado* (las etiquetas cierran bien) pero no ser *válido* (no cumple las reglas). Nosotros vamos a separar igual los errores de escritura de los errores de reglas, como una pregunta sin respuesta correcta. Lo que no vamos a copiar es lo largo que se hace escribir tantas etiquetas.

## 3. JSON Schema

- **Qué describe:** la forma que debe tener un documento JSON: qué campos lleva, de qué tipo son y cuáles son obligatorios.
- **Notación:** el propio esquema también es un JSON.

```json
{
  "type": "object",
  "required": ["titulo", "preguntas"],
  "properties": {
    "puntos": { "type": "integer", "minimum": 1 }
  }
}
```

- **Qué nos sirve:** los valores por defecto y los mínimos (por ejemplo, que los puntos valgan 1 si no se escriben y que no puedan ser cero). Además, como vamos a exportar a JSON en la HU-08, más adelante podemos publicar un esquema para que otros sistemas sepan cómo leer nuestro archivo.

## 4. ANTLR

- **Qué describe:** es una herramienta que lee una gramática y genera solo el analizador léxico (el que separa el texto en palabras o *tokens*) y el sintáctico (el que revisa que esas palabras vayan en orden).
- **Notación:** parecida a EBNF, con las reglas del analizador en minúscula y los tokens en mayúscula.

```antlr
pregunta : 'pregunta' TIPO TEXTO puntos? ;
TEXTO    : '"' (~["\r\n])* '"' ;
```

- **Qué nos sirve:** separar en dos niveles lo que son palabras sueltas (tokens) y lo que son reglas que juntan esas palabras. No vamos a usar ANTLR porque queremos programar nosotros el analizador en Python para entenderlo y explicarlo en la demo, pero sí vamos a seguir esa separación.

## 5. Expresiones regulares (Regex)

- **Qué describe:** patrones de texto, por ejemplo "uno o más dígitos" o "un texto entre comillas".
- **Notación:** símbolos cortos como `\d+`, `[a-z]*` o `"[^"]*"`.
- **Qué nos sirve:** para el analizador léxico. Cada token de Cuestiona (un número, un texto entre comillas, una palabra clave) se puede reconocer con una expresión regular sencilla. Lo que no sirven es para revisar la estructura completa, porque no pueden contar cosas anidadas, como saber si cada pregunta tiene sus opciones.

## 6. SQL

- **Qué describe:** SQL tiene una parte para describir datos (DDL, como `CREATE TABLE`) y otra para consultarlos.
- **Notación:** palabras clave en inglés que se leen casi como una frase.

```sql
CREATE TABLE pregunta (
  id INT PRIMARY KEY,
  puntos INT DEFAULT 1 CHECK (puntos > 0)
);
```

- **Qué nos sirve:** que las palabras clave se lean como una frase normal. Por eso en Cuestiona se escribe `pregunta opcion "..." puntos 2`, que se entiende sin saber programar. También la idea de las restricciones (`CHECK`) que después revisa el validador.

## 7. GIFT de Moodle (lo más parecido a Cuestiona)

- **Qué describe:** preguntas de examen para importarlas a Moodle.
- **Notación:** usa símbolos: `=` para la respuesta correcta, `~` para las incorrectas y llaves para las opciones.

```text
::P1:: ¿Qué es un metalenguaje? {=Un lenguaje que describe otros lenguajes ~Un formato de imagen}
```

- **Qué nos sirve:** confirma que la idea de escribir exámenes en texto plano sí se usa. Pero todo depende de símbolos que hay que memorizar y no tiene mensajes de error claros, que es justo lo que queremos mejorar con palabras clave en español.

## Comparación

| Metalenguaje | Qué describe | Tipo de notación | Idea que tomamos |
|---|---|---|---|
| EBNF | Reglas de un lenguaje | Reglas con `=`, `{ }`, `[ ]`, `\|` | Escribir la gramática de Cuestiona |
| XML + DTD/XSD | Estructura de documentos | Etiquetas | Separar "bien escrito" de "válido" |
| JSON Schema | Forma de un JSON | JSON | Valores por defecto y mínimos |
| ANTLR | Gramáticas para generar analizadores | Parecida a EBNF | Dividir tokens y reglas |
| Regex | Patrones de texto | Símbolos cortos | Reconocer los tokens |
| SQL | Tablas y consultas | Palabras clave en frase | Palabras clave legibles y restricciones |
| GIFT | Preguntas de Moodle | Símbolos `= ~ { }` | Saber qué no queremos copiar |

## Conclusión

Después de revisar todo decidimos que Cuestiona va a tener palabras clave en español que se lean como frase (idea de SQL), la gramática se va a escribir en EBNF y el analizador se va a dividir en una parte léxica con expresiones regulares y una parte sintáctica, como lo hace ANTLR. Los errores se separan en errores de escritura y errores de reglas (idea de XML), y los puntos van a tener valor por defecto y mínimo (idea de JSON Schema). Del formato GIFT aprendimos que usar puros símbolos hace que el archivo sea difícil de leer para un docente, así que solo dejamos `*` y `-` para marcar las opciones, que es como se hace una lista en un cuaderno.

## Referencias

- Aho, A. V., Lam, M. S., Sethi, R. y Ullman, J. D. (2006). *Compilers: Principles, techniques, and tools* (2.ª ed.). Addison-Wesley.
- Friedl, J. E. F. (2006). *Mastering regular expressions* (3.ª ed.). O'Reilly Media.
- International Organization for Standardization. (1996). *ISO/IEC 14977:1996 Information technology — Syntactic metalanguage — Extended BNF*. ISO.
- International Organization for Standardization. (2023). *ISO/IEC 9075-1:2023 Information technology — Database languages SQL — Part 1: Framework (SQL/Framework)*. ISO.
- JSON Schema. (2022). *JSON Schema draft 2020-12*. https://json-schema.org/draft/2020-12
- Moodle. (s. f.). *GIFT format*. Moodle Docs. https://docs.moodle.org/en/GIFT_format
- Parr, T. (2013). *The definitive ANTLR 4 reference*. Pragmatic Bookshelf.
- World Wide Web Consortium. (2008). *Extensible Markup Language (XML) 1.0* (5.ª ed.). https://www.w3.org/TR/xml/
