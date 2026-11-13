# Product Backlog inicial

**Responsable:** Ebrahim Ali (Product Owner)
**Última actualización:** 12 de noviembre de 2026

Las historias están ordenadas por prioridad (la de arriba es la más importante). La estimación está en **puntos de historia** con la escala 1, 2, 3, 5, 8. Es una medida del esfuerzo relativo y no son horas. El sprint sugerido es tentativo y se confirma en cada Sprint Planning.

## Resumen

| ID | Historia | Prioridad | Puntos | Sprint sugerido |
|---|---|---|---|---|
| HU-01 | Investigar metalenguajes existentes | Alta | 3 | 1 |
| HU-02 | Especificación del lenguaje (gramática y notación) | Alta | 5 | 1 |
| HU-03 | Escribir un cuestionario con título | Alta | 3 | 2 |
| HU-04 | Preguntas de opción múltiple | Alta | 3 | 2 |
| HU-05 | Preguntas de verdadero/falso | Alta | 2 | 2 |
| HU-06 | Mensajes de error con número de línea | Alta | 5 | 2 |
| HU-07 | Comentarios dentro del archivo | Media | 1 | 2 |
| HU-08 | Preguntas de respuesta abierta | Alta | 3 | 3 |
| HU-09 | Puntos por pregunta y total | Media | 2 | 3 |
| HU-10 | Secciones | Media | 3 | 3 |
| HU-11 | Aplicar el cuestionario en consola | Alta | 8 | 3 |
| HU-12 | Exportar a JSON | Media | 3 | 4 |
| HU-13 | Exportar a HTML | Media | 5 | 4 |
| HU-14 | Retroalimentación por pregunta | Baja | 2 | 4 |
| HU-15 | Orden aleatorio de preguntas y opciones | Baja | 2 | 4 |
| HU-16 | Manual de usuario con ejemplos | Alta | 3 | 4 |

**Total:** 53 puntos.

## Historias de usuario y criterios de aceptación

### HU-01: Investigar metalenguajes existentes
**Como** equipo de desarrollo, **quiero** revisar cómo están hechos otros metalenguajes (JSON Schema, XML, Regex, ANTLR, SQL) **para** tomar ideas y no copiar uno que ya existe.

Criterios de aceptación:
- Existe un documento con al menos 4 metalenguajes revisados.
- Por cada uno se anota qué describe, cómo es su notación y qué idea nos sirve.
- Las fuentes están citadas.

### HU-02: Especificación del lenguaje
**Como** docente, **quiero** un documento que explique las reglas del lenguaje **para** saber qué puedo escribir y qué no.

Criterios de aceptación:
- La gramática está escrita en EBNF (una forma estándar de escribir las reglas de un lenguaje).
- Se explica la notación concreta con al menos un ejemplo por tipo de pregunta.
- El documento está marcado como versión 0.1.

### HU-03: Escribir un cuestionario con título
**Como** docente, **quiero** crear un archivo `.cst` con el nombre del cuestionario **para** empezar a agregarle preguntas.

Criterios de aceptación:
- Un archivo con `cuestionario "Título"` se procesa sin errores.
- Si falta el título, se muestra un error que lo indica.
- El programa muestra cuántas preguntas encontró.

### HU-04: Preguntas de opción múltiple
**Como** docente, **quiero** escribir una pregunta con varias opciones y marcar la correcta **para** hacer preguntas de selección.

Criterios de aceptación:
- La opción correcta se marca con `*` y las incorrectas con `-`.
- Si ninguna opción está marcada como correcta, se muestra un error.
- Una pregunta necesita al menos 2 opciones.

### HU-05: Preguntas de verdadero/falso
**Como** docente, **quiero** escribir preguntas de verdadero o falso **para** hacer preguntas rápidas.

Criterios de aceptación:
- La respuesta se indica con `respuesta verdadero` o `respuesta falso`.
- Cualquier otro valor se marca como error.

### HU-06: Mensajes de error con número de línea
**Como** docente, **quiero** que cuando me equivoque el programa me diga la línea y el problema **para** corregirlo rápido.

Criterios de aceptación:
- Cada error indica el archivo, la línea y la columna.
- El mensaje está en español y sin términos internos del analizador.
- Si hay varios errores, se muestran todos y no solo el primero.

### HU-07: Comentarios dentro del archivo
**Como** docente, **quiero** dejar notas dentro del archivo **para** recordar de dónde saqué una pregunta.

Criterios de aceptación:
- Todo lo que va después de `#` en una línea se ignora.
- Un `#` dentro de un texto entre comillas no cuenta como comentario.

### HU-08: Preguntas de respuesta abierta
**Como** docente, **quiero** escribir una pregunta donde el alumno escribe la respuesta **para** evaluar definiciones cortas.

Criterios de aceptación:
- Se pueden indicar varias respuestas aceptadas con `acepta "a", "b"`.
- La comparación ignora mayúsculas, acentos y espacios de más.

### HU-09: Puntos por pregunta y total
**Como** docente, **quiero** asignar puntos a cada pregunta **para** que la calificación sea justa.

Criterios de aceptación:
- Se escribe `puntos N` en la pregunta. Si no se pone, vale 1 punto.
- El programa calcula el total del cuestionario.
- Un valor negativo o que no es número se marca como error.

### HU-10: Secciones
**Como** docente, **quiero** dividir el cuestionario en secciones **para** organizar los temas.

Criterios de aceptación:
- `seccion "Nombre"` agrupa las preguntas que siguen.
- El resultado muestra el puntaje por sección.

### HU-11: Aplicar el cuestionario en consola
**Como** estudiante, **quiero** contestar el cuestionario en la terminal **para** practicar y ver mi calificación.

Criterios de aceptación:
- Se muestran las preguntas una por una.
- Al final se ve la calificación y qué preguntas estuvieron mal.
- Una respuesta inválida (por ejemplo, una letra que no existe) se vuelve a preguntar.

### HU-12: Exportar a JSON
**Como** desarrollador, **quiero** obtener el cuestionario en JSON **para** usarlo en otra aplicación.

Criterios de aceptación:
- El comando de exportación genera un archivo `.json` válido.
- El JSON conserva todas las preguntas, opciones, respuestas y puntos.

### HU-13: Exportar a HTML
**Como** docente, **quiero** generar una página HTML del cuestionario **para** compartirla con los alumnos.

Criterios de aceptación:
- La página se abre en el navegador sin instalar nada.
- Las respuestas correctas no aparecen en el código visible de la página para el alumno.

### HU-14: Retroalimentación por pregunta
**Como** docente, **quiero** escribir una explicación para cada pregunta **para** que el alumno entienda en qué se equivocó.

Criterios de aceptación:
- Se escribe con `explicacion "texto"`.
- Se muestra solo si la respuesta fue incorrecta.

### HU-15: Orden aleatorio
**Como** docente, **quiero** que las preguntas y opciones salgan en desorden **para** que no se copien entre alumnos.

Criterios de aceptación:
- Se activa con `aleatorio` en el encabezado del cuestionario.
- La opción correcta se sigue calificando bien aunque cambie de lugar.

### HU-16: Manual de usuario con ejemplos
**Como** docente, **quiero** un manual corto con ejemplos **para** aprender a usar el lenguaje sin ayuda.

Criterios de aceptación:
- Incluye cómo instalar y ejecutar la herramienta.
- Tiene al menos 5 ejemplos válidos y 5 inválidos con el resultado esperado.
