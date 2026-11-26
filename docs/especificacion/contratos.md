# Contratos entre las partes del programa (HT-03)

**Sprint:** 1 (24 al 26 de noviembre de 2026)
**Responsable:** Rey David Ayala Noriega
**Revisó:** todo el equipo, en la Sprint Review del 26/11/2026

Un contrato es el acuerdo de qué datos recibe cada parte del programa y qué datos devuelve. Con esto cada integrante puede programar su parte en el Sprint 2 sin esperar a que la otra esté lista, porque ya sabe qué le va a llegar. Los nombres están pensados para Python.

## 1. Cómo se conectan las partes

```text
archivo .cst ──► Analizador léxico ──► tokens ──► Analizador sintáctico ──► Cuestionario
                                                                              │
                                                       Validador ◄────────────┘
                                                          │
                              (sin errores) ──► Intérprete (consola) / Exportadores (JSON, HTML)
```

Si alguna parte encuentra errores, se juntan todos y se muestran al final. El intérprete y los exportadores solo se ejecutan si no hubo ningún error (HU-06 CA5 y HU-08 CA6).

## 2. Estructura del cuestionario ya leído

Es la sintaxis abstracta de la [especificación v0.1](especificacion-v0.1.md) escrita como clases.

| Clase | Campo | Tipo | Notas |
|---|---|---|---|
| `Cuestionario` | `titulo` | `str` | |
| | `aleatorio` | `bool` | `False` si no se escribe |
| | `secciones` | `list[Seccion]` | Al menos una ("General") |
| | `archivo` | `str` | Nombre del archivo de donde se leyó |
| `Seccion` | `nombre` | `str` | |
| | `preguntas` | `list[Pregunta]` | |
| | `linea` | `int` | 0 para la sección "General" |
| `Pregunta` | `tipo` | `str` | `"opcion"`, `"vf"` o `"abierta"` |
| | `enunciado` | `str` | |
| | `puntos` | `int` | 1 si no se escribe |
| | `opciones` | `list[Opcion]` | Solo tipo `opcion`; vacía en los demás |
| | `respuesta_vf` | `bool \| None` | Solo tipo `vf` |
| | `aceptadas` | `list[str]` | Solo tipo `abierta` |
| | `explicacion` | `str \| None` | |
| | `linea` | `int` | Línea donde empieza la pregunta |
| `Opcion` | `texto` | `str` | |
| | `correcta` | `bool` | `True` si se marcó con `*` |
| | `linea` | `int` | |

Ejemplo en JSON de cómo queda una pregunta (también es la base del exportador a JSON de la HU-08):

```json
{
  "tipo": "opcion",
  "enunciado": "¿Qué es un metalenguaje?",
  "puntos": 2,
  "opciones": [
    { "texto": "Un formato de imagen", "correcta": false },
    { "texto": "Un lenguaje que sirve para describir otros lenguajes", "correcta": true }
  ],
  "explicacion": null,
  "linea": 4
}
```

## 3. Formato de un error

| Campo | Tipo | Ejemplo |
|---|---|---|
| `archivo` | `str` | `"repaso.cst"` |
| `linea` | `int` | `2` (empieza en 1) |
| `columna` | `int` | `1` (empieza en 1) |
| `mensaje` | `str` | `"la pregunta no tiene ninguna opción correcta. Marca la correcta con * en vez de -."` |
| `etapa` | `str` | `"lexico"`, `"sintactico"` o `"semantico"` (solo para el equipo, no se le muestra al docente) |

Así se muestra en la consola:

```text
repaso.cst:2:1: la pregunta no tiene ninguna opción correcta. Marca la correcta con * en vez de -.
Se encontró 1 error.
```

El mensaje va en español, sin palabras internas como "token" o "EOF" (HU-05 CA2).

## 4. Qué recibe y qué devuelve cada parte

| Parte | Función | Recibe | Devuelve |
|---|---|---|---|
| Analizador léxico | `tokenizar(texto, archivo)` | El texto del `.cst` y el nombre del archivo | `(list[Token], list[Error])`. Cada `Token` tiene `tipo`, `valor`, `linea` y `columna`. |
| Analizador sintáctico | `analizar(tokens, archivo)` | La lista de tokens | `(Cuestionario \| None, list[Error])`. Si hay errores sigue leyendo para encontrar los demás. |
| Validador | `validar(cuestionario)` | El `Cuestionario` | `list[Error]` con las reglas de la sección 2.4 de la especificación. Vacía si todo está bien. |
| Intérprete | `aplicar(cuestionario, entrada, salida)` | El `Cuestionario` sin errores y por dónde leer y escribir (la consola) | `Resultado` con `obtenido`, `total`, `por_seccion` y `falladas`. |
| Exportador JSON | `a_json(cuestionario)` | El `Cuestionario` sin errores | Texto JSON (`str`). |
| Exportador HTML | `a_html(cuestionario)` | El `Cuestionario` sin errores | Texto HTML (`str`) sin las respuestas correctas visibles. |

## 5. Comandos de la consola

```text
cuestiona revisar repaso.cst
cuestiona aplicar repaso.cst
cuestiona exportar repaso.cst --json
cuestiona exportar repaso.cst --html
```

El programa termina con código 0 si no hubo errores y con código 1 si hubo alguno, para que se pueda usar en pruebas automáticas.
