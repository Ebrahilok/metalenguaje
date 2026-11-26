# Especificación del lenguaje Cuestiona, versión 0.1 (HT-02)

**Versión:** 0.1
**Fecha:** 26 de noviembre de 2026
**Responsables:** Ebrahim Ali y Xavier Estavillo Servin
**Revisó:** Rey David Ayala Noriega

Este documento dice qué se puede escribir en un archivo `.cst` y qué no. Tiene dos partes: la **sintaxis abstracta**, que son las piezas que forman un cuestionario y cómo se relacionan (sin importar cómo se escriben), y la **sintaxis concreta**, que es la forma exacta en que el docente las escribe en el archivo. La versión 0.1 puede cambiar en el Sprint 2 si al programar el analizador encontramos algo que no funciona.

## 1. Sintaxis abstracta (metamodelo)

Un cuestionario está formado por estas piezas:

```text
Cuestionario
 ├─ titulo: texto
 ├─ aleatorio: sí / no                    (por defecto: no)
 └─ secciones: 1 o más Seccion
     Seccion
      ├─ nombre: texto                    ("General" si no se escribe)
      └─ preguntas: 0 o más Pregunta
          Pregunta
           ├─ tipo: opcion | vf | abierta
           ├─ enunciado: texto
           ├─ puntos: entero mayor a 0    (por defecto: 1)
           ├─ explicacion: texto          (opcional)
           ├─ opciones: 2 o más Opcion    (solo tipo opcion)
           │   Opcion
           │    ├─ texto: texto
           │    └─ correcta: sí / no
           ├─ respuesta: verdadero | falso   (solo tipo vf)
           └─ aceptadas: 1 o más textos      (solo tipo abierta)
```

| Pieza | Qué es | Reglas |
|---|---|---|
| Cuestionario | El archivo completo | Tiene un título que no puede estar vacío y al menos una pregunta. |
| Seccion | Un grupo de preguntas del mismo tema | Las preguntas que van antes de la primera sección quedan en la sección "General". |
| Pregunta | Una pregunta del examen | Siempre tiene tipo, enunciado y puntos. Lo demás depende del tipo. |
| Opcion | Una respuesta posible de una pregunta de opción múltiple | Exactamente una opción por pregunta es la correcta. |

## 2. Sintaxis concreta

### 2.1 Reglas generales

- El archivo es de texto en UTF-8 y tiene extensión `.cst`.
- Cada instrucción va en su propia línea. La sangría (los espacios al inicio) es opcional y solo sirve para que se lea mejor.
- Los textos van entre comillas dobles: `"¿Qué es un token?"`.
- Todo lo que va después de `#` es un comentario y se ignora, menos si el `#` está dentro de comillas.
- Las palabras clave se escriben en minúsculas y sin acento (`seccion`, `explicacion`), para que no haya problemas con el teclado.

### 2.2 Palabras clave

| Palabra clave | Dónde va | Para qué sirve |
|---|---|---|
| `cuestionario` | Primera línea | Da el título del cuestionario. |
| `aleatorio` | Después del título, en la misma línea | Hace que las preguntas y opciones salgan en desorden. |
| `seccion` | En su propia línea | Empieza un grupo de preguntas. |
| `pregunta` | En su propia línea | Empieza una pregunta. Le sigue el tipo: `opcion`, `vf` o `abierta`. |
| `puntos` | Al final de la línea de la pregunta | Dice cuánto vale la pregunta. |
| `*` y `-` | Debajo de una pregunta `opcion` | `*` marca la opción correcta y `-` las incorrectas. |
| `respuesta` | Debajo de una pregunta `vf` | Lleva `verdadero` o `falso`. |
| `acepta` | Debajo de una pregunta `abierta` | Lista de respuestas que se dan por buenas, separadas por coma. |
| `explicacion` | Al final de cualquier pregunta | Texto que se le muestra al alumno si se equivoca. |
| `#` | En cualquier lugar | Comentario. |

### 2.3 Gramática en EBNF

Los comentarios y las líneas vacías pueden ir en cualquier parte, así que el analizador léxico los quita antes y no aparecen en la gramática. `FIN` es el final de una línea.

```ebnf
archivo       = encabezado , { bloque } ;
encabezado    = "cuestionario" , TEXTO , [ "aleatorio" ] , FIN ;
bloque        = seccion | pregunta ;
seccion       = "seccion" , TEXTO , FIN ;

pregunta      = preg_opcion | preg_vf | preg_abierta ;
preg_opcion   = "pregunta" , "opcion" , TEXTO , [ puntos ] , FIN ,
                { opcion } , [ explicacion ] ;
preg_vf       = "pregunta" , "vf" , TEXTO , [ puntos ] , FIN ,
                "respuesta" , ( "verdadero" | "falso" ) , FIN , [ explicacion ] ;
preg_abierta  = "pregunta" , "abierta" , TEXTO , [ puntos ] , FIN ,
                "acepta" , TEXTO , { "," , TEXTO } , FIN , [ explicacion ] ;

opcion        = ( "*" | "-" ) , TEXTO , FIN ;
puntos        = "puntos" , ENTERO ;
explicacion   = "explicacion" , TEXTO , FIN ;
```

Tokens (lo que reconoce el analizador léxico):

| Token | Expresión regular | Ejemplo |
|---|---|---|
| `TEXTO` | `"[^"\n]*"` | `"Conceptos básicos"` |
| `ENTERO` | `[0-9]+` | `2` |
| Palabra clave | `[a-z]+` (si está en la tabla 2.2) | `pregunta` |
| Marca de opción | `\*` o `-` | `*` |
| Coma | `,` | `,` |
| Comentario | `#[^\n]*` (fuera de comillas) | `# tema 3` |
| `FIN` | `\n` | |

### 2.4 Reglas que revisa el validador

La gramática no puede revisar todo. Estas reglas las revisa el validador después de leer el archivo, y si alguna falla se muestra un error con la línea:

1. El título no puede estar vacío (HU-01).
2. Tiene que haber al menos una pregunta (HU-01).
3. Una pregunta `opcion` tiene al menos 2 opciones y exactamente una con `*` (HU-02).
4. Una pregunta `vf` tiene `respuesta verdadero` o `respuesta falso` (HU-02).
5. Una pregunta `abierta` tiene al menos un texto en `acepta` (HU-03).
6. `puntos` es un número entero mayor a 0. Si no se escribe, vale 1 (HU-04).

Las opciones de una pregunta `opcion` se dejan en `{ opcion }` (cero o más) en la gramática a propósito: así el analizador no se detiene y el validador puede decir con palabras sencillas que faltan opciones, en vez de un error de sintaxis.

## 3. Ejemplos por tipo de pregunta

### Opción múltiple

```text
pregunta opcion "¿Qué es un metalenguaje?" puntos 2
  - "Un formato de imagen"
  * "Un lenguaje que sirve para describir otros lenguajes"
  - "Un sistema operativo"
  explicacion "Un metalenguaje describe o define otros lenguajes."
```

### Verdadero o falso

```text
pregunta vf "Un analizador léxico separa el texto en tokens."
  respuesta verdadero
```

Como no tiene `puntos`, vale 1 punto.

### Respuesta abierta

```text
pregunta abierta "¿Qué significan las siglas DSL?" puntos 1
  acepta "lenguaje de dominio especifico", "domain specific language"
```

### Archivo completo

```text
# Repaso del primer parcial
cuestionario "Repaso de Procesadores de Lenguajes" aleatorio

pregunta vf "EBNF sirve para escribir reglas de un lenguaje."   # queda en "General"
  respuesta verdadero

seccion "Análisis léxico"

pregunta opcion "¿Qué hace el analizador léxico?" puntos 2
  * "Separa el texto en tokens"
  - "Ejecuta el programa"
  - "Dibuja la interfaz"

pregunta abierta "¿Con qué se reconocen los tokens?"
  acepta "expresiones regulares", "regex"
  explicacion "Cada token se puede describir con un patrón."
```

### Ejemplo inválido

```text
cuestionario ""
pregunta opcion "¿Cuál es la correcta?"
  - "Esta no"
  - "Esta tampoco"
```

Errores esperados:

```text
repaso.cst:1:14: el cuestionario no tiene título. Escribe el nombre entre las comillas.
repaso.cst:2:1: la pregunta no tiene ninguna opción correcta. Marca la correcta con * en vez de -.
Se encontraron 2 errores.
```

## 4. Cambios respecto al boceto de la Semana 0

- Se agrega `aleatorio` después del título y `explicacion` al final de cada pregunta (vienen de la HU-07).
- `puntos` ahora es opcional y vale 1 si no se escribe.
- La sintaxis de las preguntas no cambió, para que el boceto del README siga siendo válido.
