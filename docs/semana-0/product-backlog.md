# Product Backlog

**Responsable:** Ebrahim Ali (Product Owner)  
**Última actualización:** 26 de noviembre de 2026 (cierre del Sprint 1)

Las historias técnicas (HT) y las de usuario (HU) están mezcladas y ordenadas por sprint; dentro de cada sprint la de prioridad más alta va arriba. La estimación está en **puntos de historia (SP)** con la escala 1, 2, 3, 5, 8: es esfuerzo relativo, no horas. El sprint asignado se confirma en cada Sprint Planning.

## Backlog priorizado

| ID | Item / Historia | Prioridad | Estimación | Asignación / Estado |
|---|---|---|---|---|
| HT-01 | Investigar metalenguajes existentes | Alta (1) | 3 SP | Sprint 1 (Terminado) |
| HT-02 | Especificación del lenguaje (gramática y notación) | Alta (2) | 5 SP | Sprint 1 (Terminado) |
| HT-03 | Definir los contratos entre las partes del programa | Alta (3) | 3 SP | Sprint 1 (Terminado) |
| HU-01 | Crear un cuestionario con título y comentarios | Alta (4) | 5 SP | Sprint 2 (Pendiente) |
| HU-02 | Preguntas de opción múltiple y de verdadero/falso | Alta (5) | 5 SP | Sprint 2 (Pendiente) |
| HU-05 | Mensajes de error con número de línea | Alta (6) | 5 SP | Sprint 2 (Pendiente) |
| HU-03 | Preguntas de respuesta abierta | Alta (7) | 3 SP | Sprint 3 (Pendiente) |
| HU-06 | Aplicar el cuestionario en consola | Alta (8) | 8 SP | Sprint 3 (Pendiente) |
| HU-04 | Puntos por pregunta y secciones | Media (9) | 5 SP | Sprint 3 (Pendiente) |
| HU-10 | Validar el lenguaje con la docente | Media (10) | 3 SP | Sprint 3 (Pendiente) |
| HU-09 | Manual de usuario con ejemplos | Alta (11) | 3 SP | Sprint 4 (Pendiente) |
| HU-08 | Exportar el cuestionario a JSON y HTML | Media (12) | 8 SP | Sprint 4 (Pendiente) |
| HU-07 | Retroalimentación y orden aleatorio | Baja (13) | 5 SP | Sprint 4 (Pendiente) |

**Historias de usuario:** 50 SP. **Historias técnicas:** 11 SP. **Total:** 61 SP.

## Historias por sprint

### Sprint 1: Fundamentos y especificación v0.1

Del 24 al 26 de noviembre de 2026. Puntos comprometidos: 11. Puntos terminados: 11.

Historia técnica | Prioridad Alta | 3 SP | Sprint 1

| CUESTIONA | |
|---|---|
| **HT-01** | Investigar metalenguajes existentes |
| **ROL** | Equipo de desarrollo |
| **ACCIÓN** | Revisar cómo están hechos otros metalenguajes (JSON Schema, XML, Regex, ANTLR y SQL) |
| **PARA** | Tomar ideas y no copiar uno que ya existe |
| **CA1** | **Metalenguajes revisados:** dado que la investigación está terminada, cuando se revisa el documento, entonces tiene al menos 4 metalenguajes revisados. |
| **CA2** | **Detalle de cada uno:** dado que un metalenguaje ya revisado, cuando se lee su sección, entonces anota qué describe, cómo es su notación y qué idea nos sirve. |
| **CA3** | **Fuentes:** dado que el documento de investigación, cuando se revisan las referencias, entonces las fuentes están citadas. |
| **CA4** | **Conclusión:** dado que el documento llegó al final, cuando se lee el último apartado, entonces termina con una conclusión de qué ideas se van a usar en Cuestiona. |

Historia técnica | Prioridad Alta | 5 SP | Sprint 1

| CUESTIONA | |
|---|---|
| **HT-02** | Especificación del lenguaje (gramática y notación) |
| **ROL** | Equipo de desarrollo |
| **ACCIÓN** | Escribir la especificación del lenguaje (gramática y notación) |
| **PARA** | Que el equipo y la profesora sepan qué se puede escribir y qué no |
| **CA1** | **Gramática:** dado que la especificación está escrita, cuando se revisa la gramática, entonces está en EBNF (una forma estándar de escribir las reglas de un lenguaje). |
| **CA2** | **Notación con ejemplos:** dado que la especificación está escrita, cuando se revisa la notación, entonces se explica con al menos un ejemplo por tipo de pregunta. |
| **CA3** | **Palabras clave:** dado que la especificación está escrita, cuando se compara con el backlog, entonces cubre cuestionario, seccion, pregunta, puntos, respuesta, acepta, explicacion, aleatorio y los comentarios con #. |
| **CA4** | **Versión:** dado que la especificación está terminada, cuando se guarda en el repositorio, entonces el documento está marcado como versión 0.1. |

Historia técnica | Prioridad Alta | 3 SP | Sprint 1

| CUESTIONA | |
|---|---|
| **HT-03** | Definir los contratos entre las partes del programa |
| **ROL** | Equipo de desarrollo |
| **ACCIÓN** | Definir qué recibe y qué devuelve cada parte del programa (analizador, validador, intérprete y exportadores) |
| **PARA** | Que cada integrante pueda trabajar su parte sin esperar a que otra esté terminada |
| **CA1** | **Estructura del cuestionario:** dado que el documento de contratos, cuando se revisa la estructura del cuestionario ya leído, entonces están definidos cuestionario, sección, pregunta y opción con sus campos. |
| **CA2** | **Formato de error:** dado que el documento de contratos, cuando se revisa cómo se reporta un error, entonces está definido con archivo, línea, columna y mensaje. |
| **CA3** | **Entradas y salidas:** dado que una parte del programa (analizador, validador, intérprete o exportadores), cuando se consulta el documento, entonces indica qué datos recibe y cuáles devuelve. |
| **CA4** | **Revisión del equipo:** dado que el documento está terminado, cuando antes de empezar a programar, entonces está en el repositorio, en Markdown, y todo el equipo lo revisó. |

### Sprint 2: Núcleo, analizador y validador

Del 23 al 29 de noviembre de 2026. Puntos comprometidos: 15.

Historia de usuario | Prioridad Alta | 5 SP | Sprint 2

| CUESTIONA | |
|---|---|
| **HU-01** | Crear un cuestionario con título y comentarios |
| **ROL** | Docente |
| **ACCIÓN** | Crear un archivo .cst con el nombre del cuestionario y poder dejar notas dentro |
| **PARA** | Empezar a armarlo y recordar de dónde saqué cada pregunta |
| **CA1** | **Título válido:** dado que un archivo con cuestionario "Título", cuando se procesa el archivo, entonces se procesa sin errores. |
| **CA2** | **Sin título:** dado que un archivo sin título o con el título vacío, cuando se procesa el archivo, entonces muestra un error que indica que falta el título. |
| **CA3** | **Conteo de preguntas:** dado que un archivo válido con preguntas, cuando se procesa el archivo, entonces muestra cuántas preguntas encontró. |
| **CA4** | **Comentarios:** dado que una línea con #, cuando se procesa la línea, entonces todo lo que va después del # se ignora. |
| **CA5** | **# dentro de comillas:** dado que un # dentro de un texto entre comillas, cuando se procesa la línea, entonces no cuenta como comentario. |
| **CA6** | **Archivo sin contenido:** dado que un archivo vacío o que solo tiene comentarios, cuando se procesa el archivo, entonces se marca como error, porque no tiene título. |

Historia de usuario | Prioridad Alta | 5 SP | Sprint 2

| CUESTIONA | |
|---|---|
| **HU-02** | Preguntas de opción múltiple y de verdadero/falso |
| **ROL** | Docente |
| **ACCIÓN** | Escribir preguntas con varias opciones (marcando la correcta) y preguntas de verdadero o falso |
| **PARA** | Hacer preguntas de selección y preguntas rápidas |
| **CA1** | **Opción correcta:** dado que una pregunta de opción múltiple, cuando se marca una opción con * y las demás con -, entonces la opción con * es la correcta y las marcadas con - son incorrectas. |
| **CA2** | **Pocas opciones:** dado que una pregunta con menos de 2 opciones, cuando se procesa el archivo, entonces muestra un error, porque necesita al menos 2 opciones. |
| **CA3** | **Sin opción correcta:** dado que una pregunta donde ninguna opción tiene *, cuando se procesa el archivo, entonces muestra un error. |
| **CA4** | **Varias correctas:** dado que una pregunta con más de una opción marcada con *, cuando se procesa el archivo, entonces muestra un error. |
| **CA5** | **Verdadero/falso válida:** dado que una pregunta de verdadero/falso, cuando se escribe respuesta verdadero o respuesta falso, entonces la respuesta se acepta. |
| **CA6** | **Valor inválido:** dado que una pregunta de verdadero/falso, cuando en respuesta se escribe otro valor, entonces se marca como error. |
| **CA7** | **Sin respuesta:** dado que una pregunta de verdadero/falso sin respuesta, cuando se procesa el archivo, entonces muestra un error. |

Historia de usuario | Prioridad Alta | 5 SP | Sprint 2

| CUESTIONA | |
|---|---|
| **HU-05** | Mensajes de error con número de línea |
| **ROL** | Docente |
| **ACCIÓN** | Que cuando me equivoque el programa me diga la línea y el problema |
| **PARA** | Corregirlo rápido |
| **CA1** | **Datos del error:** dado que un archivo con un error, cuando se procesa el archivo, entonces el error indica el archivo, la línea y la columna. |
| **CA2** | **Mensaje claro:** dado que un error encontrado, cuando se muestra el mensaje, entonces está en español y sin términos internos del analizador. |
| **CA3** | **Varios errores:** dado que un archivo con varios errores, cuando se procesa el archivo, entonces se muestran todos y no solo el primero. |
| **CA4** | **Conteo final:** dado que un archivo con errores, cuando termina de procesarse, entonces al final se muestra cuántos errores se encontraron. |

### Sprint 3: Ampliación y validación con la profesora

Del 30 de noviembre al 6 de diciembre de 2026. Puntos comprometidos: 19.

Historia de usuario | Prioridad Alta | 3 SP | Sprint 3

| CUESTIONA | |
|---|---|
| **HU-03** | Preguntas de respuesta abierta |
| **ROL** | Docente |
| **ACCIÓN** | Escribir una pregunta donde el alumno escribe la respuesta |
| **PARA** | Evaluar definiciones cortas |
| **CA1** | **Varias respuestas aceptadas:** dado que una pregunta abierta, cuando se escribe acepta "a", "b", entonces todas esas respuestas se aceptan como correctas. |
| **CA2** | **Sin respuestas aceptadas:** dado que una pregunta abierta sin acepta, cuando se procesa el archivo, entonces muestra un error, porque necesita al menos una respuesta aceptada. |
| **CA3** | **Comparación flexible:** dado que una respuesta aceptada y una respuesta del alumno, cuando se comparan, entonces se ignoran mayúsculas, acentos y espacios de más. |

Historia de usuario | Prioridad Alta | 8 SP | Sprint 3

| CUESTIONA | |
|---|---|
| **HU-06** | Aplicar el cuestionario en consola |
| **ROL** | Estudiante |
| **ACCIÓN** | Contestar el cuestionario en la terminal |
| **PARA** | Practicar y ver mi calificación |
| **CA1** | **Preguntas una por una:** dado que un cuestionario válido, cuando el estudiante lo inicia, entonces se muestran las preguntas una por una, con su sección y sus puntos. |
| **CA2** | **Respuesta inválida:** dado que una pregunta en pantalla, cuando el estudiante escribe algo inválido (por ejemplo, una letra que no existe), entonces la pregunta se vuelve a hacer. |
| **CA3** | **Calificación:** dado que el estudiante contestó todo, cuando termina el cuestionario, entonces se ve la calificación total y por sección. |
| **CA4** | **Revisión de errores:** dado que el cuestionario terminó, cuando se muestra el resultado, entonces se ven las preguntas que estuvieron mal y cuál era la respuesta correcta. |
| **CA5** | **Archivo con errores:** dado que un archivo .cst con errores, cuando se intenta aplicar, entonces no se aplica y se muestran los errores. |

Historia de usuario | Prioridad Media | 5 SP | Sprint 3

| CUESTIONA | |
|---|---|
| **HU-04** | Puntos por pregunta y secciones |
| **ROL** | Docente |
| **ACCIÓN** | Asignar puntos a cada pregunta y dividir el cuestionario en secciones |
| **PARA** | Que la calificación sea justa y los temas estén organizados |
| **CA1** | **Puntos de una pregunta:** dado que una pregunta con puntos N, cuando se procesa el archivo, entonces la pregunta vale N puntos. |
| **CA2** | **Sin puntos:** dado que una pregunta sin puntos, cuando se procesa el archivo, entonces vale 1 punto. |
| **CA3** | **Valor inválido:** dado que un valor negativo, cero o que no es número, cuando se procesa el archivo, entonces se marca como error. |
| **CA4** | **Total:** dado que un cuestionario con puntos, cuando se procesa el archivo, entonces el programa calcula el total. |
| **CA5** | **Sección:** dado que una línea seccion "Nombre", cuando se procesa el archivo, entonces agrupa las preguntas que siguen hasta la siguiente sección. |
| **CA6** | **Sin sección:** dado que preguntas antes de la primera sección, cuando se procesa el archivo, entonces quedan en una sección general. |
| **CA7** | **Resultado por sección:** dado que un cuestionario con secciones, cuando se muestra el resultado, entonces aparece el puntaje por sección y el total. |

Historia de usuario | Prioridad Media | 3 SP | Sprint 3

| CUESTIONA | |
|---|---|
| **HU-10** | Validar el lenguaje con la docente |
| **ROL** | Docente |
| **ACCIÓN** | Probar la herramienta con un cuestionario mío y dar mi opinión |
| **PARA** | Confirmar que el lenguaje me sirve y detectar qué le falta |
| **CA1** | **Cuestionario real:** dado que un cuestionario de la docente con 10 o más preguntas, cuando lo escribe en un archivo .cst y lo procesa, entonces lo logra sin tener que tocar código. |
| **CA2** | **Errores entendibles:** dado que un error en el archivo de la docente, cuando la herramienta muestra el mensaje, entonces la docente lo entiende sin que el equipo se lo explique. |
| **CA3** | **Registro de comentarios:** dado que la docente terminó de probar la herramienta, cuando se hace el Sprint Review, entonces sus comentarios quedan anotados en el acta. |
| **CA4** | **Cambios al backlog:** dado que comentarios que piden cambios, cuando se revisan en el Sprint Review, entonces se agregan al backlog con su prioridad. |

### Sprint 4: Cierre, documentación y demostración

Del 7 al 13 de diciembre de 2026. Puntos comprometidos: 16.

Historia de usuario | Prioridad Alta | 3 SP | Sprint 4

| CUESTIONA | |
|---|---|
| **HU-09** | Manual de usuario con ejemplos |
| **ROL** | Docente |
| **ACCIÓN** | Un manual corto con ejemplos |
| **PARA** | Aprender a usar el lenguaje sin ayuda |
| **CA1** | **Instalación:** dado que el manual terminado, cuando el docente lo lee, entonces incluye cómo instalar y ejecutar la herramienta. |
| **CA2** | **Palabras clave:** dado que el manual terminado, cuando el docente busca una pregunta o palabra clave, entonces explica cada tipo de pregunta y cada palabra clave del lenguaje. |
| **CA3** | **Ejemplos:** dado que el manual terminado, cuando se revisan los ejemplos, entonces hay al menos 5 válidos y 5 inválidos con el resultado esperado. |

Historia de usuario | Prioridad Media | 8 SP | Sprint 4

| CUESTIONA | |
|---|---|
| **HU-08** | Exportar el cuestionario a JSON y HTML |
| **ROL** | Docente o desarrollador |
| **ACCIÓN** | Obtener el cuestionario en JSON y en una página HTML |
| **PARA** | Usarlo en otra aplicación o compartirlo con los alumnos |
| **CA1** | **Exportar a JSON:** dado que un cuestionario válido, cuando se usa el comando de exportación a JSON, entonces se genera un archivo .json válido. |
| **CA2** | **Contenido del JSON:** dado que un archivo .json generado, cuando se revisa su contenido, entonces conserva todas las preguntas, opciones, respuestas, puntos y secciones. |
| **CA3** | **Exportar a HTML:** dado que un cuestionario válido, cuando se usa el comando de exportación a HTML, entonces se genera un archivo .html con el cuestionario. |
| **CA4** | **Abrir la página:** dado que un archivo .html generado, cuando se abre en el navegador, entonces funciona sin instalar nada. |
| **CA5** | **Respuestas ocultas:** dado que la página generada, cuando el alumno revisa el código visible, entonces las respuestas correctas no aparecen. |
| **CA6** | **Archivo con errores:** dado que un archivo .cst con errores, cuando se intenta exportar, entonces no se genera ningún archivo y se muestran los errores. |

Historia de usuario | Prioridad Baja | 5 SP | Sprint 4

| CUESTIONA | |
|---|---|
| **HU-07** | Retroalimentación y orden aleatorio |
| **ROL** | Docente |
| **ACCIÓN** | Escribir una explicación para cada pregunta y hacer que las preguntas y opciones salgan en desorden |
| **PARA** | Que el alumno entienda en qué se equivocó y no se copien entre ellos |
| **CA1** | **Explicación tras un error:** dado que una pregunta con explicacion "texto", cuando el alumno responde mal, entonces se muestra la explicación. |
| **CA2** | **Respuesta correcta:** dado que una pregunta con explicación, cuando el alumno responde bien, entonces la explicación no se muestra. |
| **CA3** | **Pregunta sin explicación:** dado que una pregunta sin explicacion, cuando se aplica el cuestionario, entonces funciona igual que antes. |
| **CA4** | **Orden aleatorio:** dado que aleatorio en el encabezado del cuestionario, cuando se aplica el cuestionario, entonces las preguntas y las opciones salen en desorden. |
| **CA5** | **Calificación con desorden:** dado que una opción correcta que cambió de lugar, cuando el alumno la elige, entonces se califica bien. |
| **CA6** | **Sin aleatorio:** dado que un cuestionario sin aleatorio, cuando se aplica el cuestionario, entonces el orden es el mismo que en el archivo. |
