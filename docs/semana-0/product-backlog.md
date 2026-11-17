# Product Backlog inicial

**Responsable:** Ebrahim Ali (Product Owner)
**Última actualización:** 17 de noviembre de 2026

Las historias están ordenadas por prioridad (la de arriba es la más importante). La estimación está en **puntos de historia** con la escala 1, 2, 3, 5, 8. Es una medida del esfuerzo relativo y no son horas. El sprint sugerido es tentativo y se confirma en cada Sprint Planning.

El backlog se divide en dos partes: las **historias de usuario** (lo que necesita una persona que usa la herramienta) y las **historias técnicas** (trabajo interno del equipo que no tiene un usuario final, pero que hace falta para poder construir el resto). Las historias técnicas no se escriben con el formato "Como… quiero… para…" y por eso están en su propio apartado.

## Resumen

### Historias de usuario

| ID | Historia | Prioridad | Puntos | Sprint sugerido |
|---|---|---|---|---|
| HU-01 | Crear un cuestionario con título y comentarios | Alta | 5 | 2 |
| HU-02 | Preguntas de opción múltiple y de verdadero/falso | Alta | 5 | 2 |
| HU-03 | Preguntas de respuesta abierta | Alta | 3 | 3 |
| HU-04 | Puntos por pregunta y secciones | Media | 5 | 3 |
| HU-05 | Mensajes de error con número de línea | Alta | 5 | 2 |
| HU-06 | Aplicar el cuestionario en consola | Alta | 8 | 3 |
| HU-07 | Retroalimentación y orden aleatorio | Baja | 5 | 4 |
| HU-08 | Exportar el cuestionario a JSON y HTML | Media | 8 | 4 |
| HU-09 | Manual de usuario con ejemplos | Alta | 3 | 4 |

**Total de historias de usuario:** 47 puntos.

### Historias técnicas

| ID | Historia técnica | Prioridad | Puntos | Sprint sugerido |
|---|---|---|---|---|
| HT-01 | Investigar metalenguajes existentes | Alta | 3 | 1 |
| HT-02 | Especificación del lenguaje (gramática y notación) | Alta | 5 | 1 |
| HT-03 | Definir los contratos entre las partes del programa | Alta | 3 | 1 |

**Total de historias técnicas:** 11 puntos.

**Total del backlog:** 58 puntos.

## Vista de historias (solo el enunciado)

Aquí se ven únicamente las historias, sin criterios de aceptación, para tener una lista rapida de todo lo que se va a construir.

### Historias de usuario

- **HU-01:** Como docente, quiero crear un archivo `.cst` con el nombre del cuestionario y poder dejar notas dentro, para empezar a armarlo y recordar de dónde saqué cada pregunta.
- **HU-02:** Como docente, quiero escribir preguntas de opción múltiple y de verdadero/falso, para hacer preguntas de selección y preguntas rápidas.
- **HU-03:** Como docente, quiero escribir una pregunta donde el alumno escribe la respuesta, para evaluar definiciones cortas.
- **HU-04:** Como docente, quiero asignar puntos a cada pregunta y dividir el cuestionario en secciones, para que la calificación sea justa y los temas estén organizados.
- **HU-05:** Como docente, quiero que cuando me equivoque el programa me diga la línea y el problema, para corregirlo rápido.
- **HU-06:** Como estudiante, quiero contestar el cuestionario en la terminal, para practicar y ver mi calificación.
- **HU-07:** Como docente, quiero explicar cada respuesta y hacer que las preguntas salgan en desorden, para que el alumno entienda en qué se equivocó y no se copien entre ellos.
- **HU-08:** Como docente o desarrollador, quiero obtener el cuestionario en JSON y en una página HTML, para usarlo en otra aplicación o compartirlo con los alumnos.
- **HU-09:** Como docente, quiero un manual corto con ejemplos, para aprender a usar el lenguaje sin ayuda.

### Historias técnicas

- **HT-01:** Revisar cómo están hechos otros metalenguajes (JSON Schema, XML, Regex, ANTLR y SQL), para tomar ideas y no copiar uno que ya existe.
- **HT-02:** Escribir la especificación del lenguaje (gramática y notación), para que el equipo y la docente sepan qué se puede escribir y qué no.
- **HT-03:** Definir los contratos entre las partes del programa, para que cada integrante pueda trabajar su parte sin esperar a que otra esté terminada.

---

## Historias de usuario y criterios de aceptación

### HU-01: Crear un cuestionario con título y comentarios
**Como** docente, **quiero** crear un archivo `.cst` con el nombre del cuestionario y poder dejar notas dentro **para** empezar a armarlo y recordar de dónde saqué cada pregunta.

Criterios de aceptación:
- Un archivo con `cuestionario "Título"` se procesa sin errores.
- Si falta el título o está vacío, se muestra un error que lo indica.
- El programa muestra cuántas preguntas encontró.
- Todo lo que va después de `#` en una línea se ignora.
- Un `#` dentro de un texto entre comillas no cuenta como comentario.
- Un archivo vacío o que solo tiene comentarios se marca como error, porque no tiene título.

### HU-02: Preguntas de opción múltiple y de verdadero/falso
**Como** docente, **quiero** escribir preguntas con varias opciones (marcando la correcta) y preguntas de verdadero o falso **para** hacer preguntas de selección y preguntas rápidas.

Criterios de aceptación:
- En opción múltiple, la opción correcta se marca con `*` y las incorrectas con `-`.
- Una pregunta de opción múltiple necesita al menos 2 opciones.
- Si ninguna opción está marcada como correcta, se muestra un error.
- Si hay más de una opción marcada como correcta, se muestra un error.
- En verdadero/falso, la respuesta se indica con `respuesta verdadero` o `respuesta falso`.
- Cualquier otro valor en `respuesta` se marca como error.
- Si una pregunta de verdadero/falso no tiene `respuesta`, se muestra un error.

### HU-03: Preguntas de respuesta abierta
**Como** docente, **quiero** escribir una pregunta donde el alumno escribe la respuesta **para** evaluar definiciones cortas.

Criterios de aceptación:
- Se pueden indicar varias respuestas aceptadas con `acepta "a", "b"`.
- Una pregunta abierta necesita al menos una respuesta aceptada, si no se muestra un error.
- La comparación ignora mayúsculas, acentos y espacios de más.

### HU-04: Puntos por pregunta y secciones
**Como** docente, **quiero** asignar puntos a cada pregunta y dividir el cuestionario en secciones **para** que la calificación sea justa y los temas estén organizados.

Criterios de aceptación:
- Se escribe `puntos N` en la pregunta. Si no se pone, vale 1 punto.
- Un valor negativo, cero o que no es número se marca como error.
- El programa calcula el total del cuestionario.
- `seccion "Nombre"` agrupa las preguntas que siguen hasta la siguiente sección.
- Las preguntas que están antes de la primera sección quedan en una sección general.
- El resultado muestra el puntaje por sección y el total.

### HU-05: Mensajes de error con número de línea
**Como** docente, **quiero** que cuando me equivoque el programa me diga la línea y el problema **para** corregirlo rápido.

Criterios de aceptación:
- Cada error indica el archivo, la línea y la columna.
- El mensaje está en español y sin términos internos del analizador.
- Si hay varios errores, se muestran todos y no solo el primero.
- Al final se muestra cuántos errores se encontraron.

### HU-06: Aplicar el cuestionario en consola
**Como** estudiante, **quiero** contestar el cuestionario en la terminal **para** practicar y ver mi calificación.

Criterios de aceptación:
- Se muestran las preguntas una por una, con su sección y sus puntos.
- Una respuesta inválida (por ejemplo, una letra que no existe) se vuelve a preguntar.
- Al final se ve la calificación total y por sección.
- Al final se muestran qué preguntas estuvieron mal y cuál era la respuesta correcta.
- Si el archivo tiene errores, el cuestionario no se aplica y se muestran los errores.

### HU-07: Retroalimentación y orden aleatorio
**Como** docente, **quiero** escribir una explicación para cada pregunta y hacer que las preguntas y opciones salgan en desorden **para** que el alumno entienda en qué se equivocó y no se copien entre ellos.

Criterios de aceptación:
- La explicación se escribe con `explicacion "texto"` dentro de la pregunta.
- La explicación se muestra solo si la respuesta fue incorrecta.
- Una pregunta sin `explicacion` funciona igual que antes.
- El orden aleatorio se activa con `aleatorio` en el encabezado del cuestionario.
- La opción correcta se sigue calificando bien aunque cambie de lugar.
- Sin `aleatorio`, el orden es el mismo que en el archivo.

### HU-08: Exportar el cuestionario a JSON y HTML
**Como** docente o desarrollador, **quiero** obtener el cuestionario en JSON y en una página HTML **para** usarlo en otra aplicación o compartirlo con los alumnos.

Criterios de aceptación:
- El comando de exportación genera un archivo `.json` válido.
- El JSON conserva todas las preguntas, opciones, respuestas, puntos y secciones.
- El comando de exportación genera un archivo `.html` con el cuestionario.
- La página se abre en el navegador sin instalar nada.
- Las respuestas correctas no aparecen en el código visible de la página para el alumno.
- Si el archivo `.cst` tiene errores, no se genera ningún archivo y se muestran los errores.

### HU-09: Manual de usuario con ejemplos
**Como** docente, **quiero** un manual corto con ejemplos **para** aprender a usar el lenguaje sin ayuda.

Criterios de aceptación:
- Incluye cómo instalar y ejecutar la herramienta.
- Explica cada tipo de pregunta y cada palabra clave del lenguaje.
- Tiene al menos 5 ejemplos válidos y 5 inválidos con el resultado esperado.

---

## Historias técnicas y criterios de aceptación

### HT-01: Investigar metalenguajes existentes
Revisar cómo están hechos otros metalenguajes (JSON Schema, XML, Regex, ANTLR y SQL) para tomar ideas y no copiar uno que ya existe.

Criterios de aceptación:
- Existe un documento con al menos 4 metalenguajes revisados.
- Por cada uno se anota qué describe, cómo es su notación y qué idea nos sirve.
- Las fuentes están citadas.
- El documento termina con una conclusión de qué ideas se van a usar en Cuestiona.

### HT-02: Especificación del lenguaje (gramática y notación)
Escribir un documento que explique las reglas del lenguaje, para saber qué se puede escribir y qué no.

Criterios de aceptación:
- La gramática está escrita en EBNF (una forma estándar de escribir las reglas de un lenguaje).
- Se explica la notación concreta con al menos un ejemplo por tipo de pregunta.
- La especificación cubre todas las palabras clave del backlog (`cuestionario`, `seccion`, `pregunta`, `puntos`, `respuesta`, `acepta`, `explicacion`, `aleatorio` y los comentarios con `#`).
- El documento está marcado como versión 0.1.

### HT-03: Definir los contratos entre las partes del programa
Dejar por escrito qué recibe y qué devuelve cada parte del programa (analizador, validador, intérprete y exportadores), para que se pueda trabajar cada una por separado.

Criterios de aceptación:
- Está definida la estructura del cuestionario ya leído (cuestionario, sección, pregunta y opción) con sus campos.
- Está definido el formato de un error (archivo, línea, columna y mensaje).
- Por cada parte del programa se indica qué datos recibe y cuáles devuelve.
- El documento está en el repositorio, en formato Markdown, y todo el equipo lo revisó antes de empezar a programar.
