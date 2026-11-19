# Product Backlog por sprint

**Responsable:** Ebrahim Ali (Product Owner)  
**Última actualización:** 19 de noviembre de 2026

Las historias técnicas y las de usuario están mezcladas y ordenadas por sprint. Dentro de cada sprint, la de prioridad más alta va arriba. La estimación está en **puntos de historia** con la escala 1, 2, 3, 5, 8: es una medida del esfuerzo relativo y no son horas. El sprint asignado es tentativo y se confirma en cada Sprint Planning.

## Backlog priorizado

| ID | Historia | Prioridad | Estimación | Asignación |
|---|---|---|---|---|
| HT-01 | Investigar metalenguajes existentes | Alta (1) | 3 SP | Sprint 1 |
| HT-02 | Especificación del lenguaje (gramática y notación) | Alta (2) | 5 SP | Sprint 1 |
| HT-03 | Definir los contratos entre las partes del programa | Alta (3) | 3 SP | Sprint 1 |
| HU-01 | Crear un cuestionario con título y comentarios | Alta (4) | 5 SP | Sprint 2 |
| HU-02 | Preguntas de opción múltiple y de verdadero/falso | Alta (5) | 5 SP | Sprint 2 |
| HU-05 | Mensajes de error con número de línea | Alta (6) | 5 SP | Sprint 2 |
| HU-03 | Preguntas de respuesta abierta | Alta (7) | 3 SP | Sprint 3 |
| HU-06 | Aplicar el cuestionario en consola | Alta (8) | 8 SP | Sprint 3 |
| HU-04 | Puntos por pregunta y secciones | Media (9) | 5 SP | Sprint 3 |
| HU-09 | Manual de usuario con ejemplos | Alta (10) | 3 SP | Sprint 4 |
| HU-08 | Exportar el cuestionario a JSON y HTML | Media (11) | 8 SP | Sprint 4 |
| HU-07 | Retroalimentación y orden aleatorio | Baja (12) | 5 SP | Sprint 4 |

**Historias de usuario:** 47 puntos. **Historias técnicas:** 11 puntos. **Total del backlog:** 58 puntos.

## Historias por sprint

### Sprint 1: Fundamentos y especificación v0.1

16 al 22 de noviembre de 2026. Puntos comprometidos: 11.

#### HT-01: Investigar metalenguajes existentes

Historia técnica | Prioridad Alta | 3 puntos | Sprint 1

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Equipo de desarrollo | revisar cómo están hechos otros metalenguajes (JSON Schema, XML, Regex, ANTLR y SQL) | tomar ideas y no copiar uno que ya existe |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Metalenguajes revisados | La investigación está terminada | Se revisa el documento | Tiene al menos 4 metalenguajes revisados |
| 2. Detalle de cada uno | Un metalenguaje ya revisado | Se lee su sección | Anota qué describe, cómo es su notación y qué idea nos sirve |
| 3. Fuentes | El documento de investigación | Se revisan las referencias | Las fuentes están citadas |
| 4. Conclusión | El documento llegó al final | Se lee el último apartado | Termina con una conclusión de qué ideas se van a usar en Cuestiona |

#### HT-02: Especificación del lenguaje (gramática y notación)

Historia técnica | Prioridad Alta | 5 puntos | Sprint 1

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Equipo de desarrollo | escribir la especificación del lenguaje (gramática y notación) | que el equipo y la profesora sepan qué se puede escribir y qué no |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Gramática | La especificación está escrita | Se revisa la gramática | Está en EBNF (una forma estándar de escribir las reglas de un lenguaje) |
| 2. Notación con ejemplos | La especificación está escrita | Se revisa la notación | Se explica con al menos un ejemplo por tipo de pregunta |
| 3. Palabras clave | La especificación está escrita | Se compara con el backlog | Cubre cuestionario, seccion, pregunta, puntos, respuesta, acepta, explicacion, aleatorio y los comentarios con # |
| 4. Versión | La especificación está terminada | Se guarda en el repositorio | El documento está marcado como versión 0.1 |

#### HT-03: Definir los contratos entre las partes del programa

Historia técnica | Prioridad Alta | 3 puntos | Sprint 1

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Equipo de desarrollo | definir qué recibe y qué devuelve cada parte del programa (analizador, validador, intérprete y exportadores) | que cada integrante pueda trabajar su parte sin esperar a que otra esté terminada |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Estructura del cuestionario | El documento de contratos | Se revisa la estructura del cuestionario ya leído | Están definidos cuestionario, sección, pregunta y opción con sus campos |
| 2. Formato de error | El documento de contratos | Se revisa cómo se reporta un error | Está definido con archivo, línea, columna y mensaje |
| 3. Entradas y salidas | Una parte del programa (analizador, validador, intérprete o exportadores) | Se consulta el documento | Indica qué datos recibe y cuáles devuelve |
| 4. Revisión del equipo | El documento está terminado | Antes de empezar a programar | Está en el repositorio, en Markdown, y todo el equipo lo revisó |

### Sprint 2: Núcleo, analizador y validador

23 al 29 de noviembre de 2026. Puntos comprometidos: 15.

#### HU-01: Crear un cuestionario con título y comentarios

Historia de usuario | Prioridad Alta | 5 puntos | Sprint 2

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Docente | crear un archivo .cst con el nombre del cuestionario y poder dejar notas dentro | empezar a armarlo y recordar de dónde saqué cada pregunta |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Título válido | Un archivo con cuestionario "Título" | Se procesa el archivo | Se procesa sin errores |
| 2. Sin título | Un archivo sin título o con el título vacío | Se procesa el archivo | Muestra un error que indica que falta el título |
| 3. Conteo de preguntas | Un archivo válido con preguntas | Se procesa el archivo | Muestra cuántas preguntas encontró |
| 4. Comentarios | Una línea con # | Se procesa la línea | Todo lo que va después del # se ignora |
| 5. # dentro de comillas | Un # dentro de un texto entre comillas | Se procesa la línea | No cuenta como comentario |
| 6. Archivo sin contenido | Un archivo vacío o que solo tiene comentarios | Se procesa el archivo | Se marca como error, porque no tiene título |

#### HU-02: Preguntas de opción múltiple y de verdadero/falso

Historia de usuario | Prioridad Alta | 5 puntos | Sprint 2

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Docente | escribir preguntas con varias opciones (marcando la correcta) y preguntas de verdadero o falso | hacer preguntas de selección y preguntas rápidas |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Opción correcta | Una pregunta de opción múltiple | Se marca una opción con * y las demás con - | La opción con * es la correcta y las marcadas con - son incorrectas |
| 2. Pocas opciones | Una pregunta con menos de 2 opciones | Se procesa el archivo | Muestra un error, porque necesita al menos 2 opciones |
| 3. Sin opción correcta | Una pregunta donde ninguna opción tiene * | Se procesa el archivo | Muestra un error |
| 4. Varias correctas | Una pregunta con más de una opción marcada con * | Se procesa el archivo | Muestra un error |
| 5. Verdadero/falso válida | Una pregunta de verdadero/falso | Se escribe respuesta verdadero o respuesta falso | La respuesta se acepta |
| 6. Valor inválido | Una pregunta de verdadero/falso | En respuesta se escribe otro valor | Se marca como error |
| 7. Sin respuesta | Una pregunta de verdadero/falso sin respuesta | Se procesa el archivo | Muestra un error |

#### HU-05: Mensajes de error con número de línea

Historia de usuario | Prioridad Alta | 5 puntos | Sprint 2

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Docente | que cuando me equivoque el programa me diga la línea y el problema | corregirlo rápido |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Datos del error | Un archivo con un error | Se procesa el archivo | El error indica el archivo, la línea y la columna |
| 2. Mensaje claro | Un error encontrado | Se muestra el mensaje | Está en español y sin términos internos del analizador |
| 3. Varios errores | Un archivo con varios errores | Se procesa el archivo | Se muestran todos y no solo el primero |
| 4. Conteo final | Un archivo con errores | Termina de procesarse | Al final se muestra cuántos errores se encontraron |

### Sprint 3: Ampliación y validación con la profesora

30 de noviembre al 6 de diciembre de 2026. Puntos comprometidos: 16.

#### HU-03: Preguntas de respuesta abierta

Historia de usuario | Prioridad Alta | 3 puntos | Sprint 3

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Docente | escribir una pregunta donde el alumno escribe la respuesta | evaluar definiciones cortas |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Varias respuestas aceptadas | Una pregunta abierta | Se escribe acepta "a", "b" | Todas esas respuestas se aceptan como correctas |
| 2. Sin respuestas aceptadas | Una pregunta abierta sin acepta | Se procesa el archivo | Muestra un error, porque necesita al menos una respuesta aceptada |
| 3. Comparación flexible | Una respuesta aceptada y una respuesta del alumno | Se comparan | Se ignoran mayúsculas, acentos y espacios de más |

#### HU-06: Aplicar el cuestionario en consola

Historia de usuario | Prioridad Alta | 8 puntos | Sprint 3

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Estudiante | contestar el cuestionario en la terminal | practicar y ver mi calificación |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Preguntas una por una | Un cuestionario válido | El estudiante lo inicia | Se muestran las preguntas una por una, con su sección y sus puntos |
| 2. Respuesta inválida | Una pregunta en pantalla | El estudiante escribe algo inválido (por ejemplo, una letra que no existe) | La pregunta se vuelve a hacer |
| 3. Calificación | El estudiante contestó todo | Termina el cuestionario | Se ve la calificación total y por sección |
| 4. Revisión de errores | El cuestionario terminó | Se muestra el resultado | Se ven las preguntas que estuvieron mal y cuál era la respuesta correcta |
| 5. Archivo con errores | Un archivo .cst con errores | Se intenta aplicar | No se aplica y se muestran los errores |

#### HU-04: Puntos por pregunta y secciones

Historia de usuario | Prioridad Media | 5 puntos | Sprint 3

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Docente | asignar puntos a cada pregunta y dividir el cuestionario en secciones | que la calificación sea justa y los temas estén organizados |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Puntos de una pregunta | Una pregunta con puntos N | Se procesa el archivo | La pregunta vale N puntos |
| 2. Sin puntos | Una pregunta sin puntos | Se procesa el archivo | Vale 1 punto |
| 3. Valor inválido | Un valor negativo, cero o que no es número | Se procesa el archivo | Se marca como error |
| 4. Total | Un cuestionario con puntos | Se procesa el archivo | El programa calcula el total |
| 5. Sección | Una línea seccion "Nombre" | Se procesa el archivo | Agrupa las preguntas que siguen hasta la siguiente sección |
| 6. Sin sección | Preguntas antes de la primera sección | Se procesa el archivo | Quedan en una sección general |
| 7. Resultado por sección | Un cuestionario con secciones | Se muestra el resultado | Aparece el puntaje por sección y el total |

### Sprint 4: Cierre, documentación y demostración

7 al 13 de diciembre de 2026. Puntos comprometidos: 16.

#### HU-09: Manual de usuario con ejemplos

Historia de usuario | Prioridad Alta | 3 puntos | Sprint 4

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Docente | un manual corto con ejemplos | aprender a usar el lenguaje sin ayuda |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Instalación | El manual terminado | El docente lo lee | Incluye cómo instalar y ejecutar la herramienta |
| 2. Palabras clave | El manual terminado | El docente busca una pregunta o palabra clave | Explica cada tipo de pregunta y cada palabra clave del lenguaje |
| 3. Ejemplos | El manual terminado | Se revisan los ejemplos | Hay al menos 5 válidos y 5 inválidos con el resultado esperado |

#### HU-08: Exportar el cuestionario a JSON y HTML

Historia de usuario | Prioridad Media | 8 puntos | Sprint 4

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Docente o desarrollador | obtener el cuestionario en JSON y en una página HTML | usarlo en otra aplicación o compartirlo con los alumnos |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Exportar a JSON | Un cuestionario válido | Se usa el comando de exportación a JSON | Se genera un archivo .json válido |
| 2. Contenido del JSON | Un archivo .json generado | Se revisa su contenido | Conserva todas las preguntas, opciones, respuestas, puntos y secciones |
| 3. Exportar a HTML | Un cuestionario válido | Se usa el comando de exportación a HTML | Se genera un archivo .html con el cuestionario |
| 4. Abrir la página | Un archivo .html generado | Se abre en el navegador | Funciona sin instalar nada |
| 5. Respuestas ocultas | La página generada | El alumno revisa el código visible | Las respuestas correctas no aparecen |
| 6. Archivo con errores | Un archivo .cst con errores | Se intenta exportar | No se genera ningún archivo y se muestran los errores |

#### HU-07: Retroalimentación y orden aleatorio

Historia de usuario | Prioridad Baja | 5 puntos | Sprint 4

| Rol (Como) | Acción (Quiero) | Beneficio (Para) |
|---|---|---|
| Docente | escribir una explicación para cada pregunta y hacer que las preguntas y opciones salgan en desorden | que el alumno entienda en qué se equivocó y no se copien entre ellos |

**Criterios de aceptación**

| Escenario | Dado que (Contexto) | Cuando (Acción) | Entonces (Resultado) |
|---|---|---|---|
| 1. Explicación tras un error | Una pregunta con explicacion "texto" | El alumno responde mal | Se muestra la explicación |
| 2. Respuesta correcta | Una pregunta con explicación | El alumno responde bien | La explicación no se muestra |
| 3. Pregunta sin explicación | Una pregunta sin explicacion | Se aplica el cuestionario | Funciona igual que antes |
| 4. Orden aleatorio | aleatorio en el encabezado del cuestionario | Se aplica el cuestionario | Las preguntas y las opciones salen en desorden |
| 5. Calificación con desorden | Una opción correcta que cambió de lugar | El alumno la elige | Se califica bien |
| 6. Sin aleatorio | Un cuestionario sin aleatorio | Se aplica el cuestionario | El orden es el mismo que en el archivo |
