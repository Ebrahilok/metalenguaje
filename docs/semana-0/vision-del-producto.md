# Visión del producto: Cuestiona

**Fecha:** 12 de noviembre de 2026
**Etapa:** Semana 0 (preparación)

## El problema

Cuando un docente hace un examen casi siempre lo escribe en Word o lo arma a mano en una plataforma. Si después quiere usar las mismas preguntas en otro lado (en una página, en un formulario o en una app) tiene que volver a copiarlas una por una. Además no hay nada que le avise si se le olvidó marcar la respuesta correcta o si una pregunta quedó sin opciones. Esos errores se notan hasta que los alumnos ya están contestando.

## La propuesta

**Cuestiona** es un lenguaje pequeño, con palabras en español, para describir cuestionarios en un archivo de texto (`.cst`). Con ese archivo la herramienta va a poder:

1. **Revisar** que el cuestionario esté bien escrito y decir en qué línea está el error y por qué.
2. **Aplicar** el cuestionario en la consola y calificar las respuestas.
3. **Convertir** el cuestionario a otros formatos (HTML y JSON) para usarlo en otras herramientas.

Es un metalenguaje porque no es un examen en sí, sino una forma de **describir** exámenes. El mismo archivo sirve para generar varias cosas distintas.

## ¿Para quién es?

- **Docentes**, que escriben y mantienen los cuestionarios. Es el usuario principal.
- **Estudiantes**, que contestan el cuestionario ya generado.
- **Desarrolladores**, que quieren leer los cuestionarios desde otro sistema usando el JSON.

## Lo que lo hace diferente

- Las palabras clave están en español (`cuestionario`, `pregunta`, `seccion`, `respuesta`), para que alguien que no programa lo pueda leer sin manual.
- Los mensajes de error explican el problema con palabras sencillas, no con términos del analizador.
- No depende de ninguna plataforma. Es un archivo de texto que se puede guardar en Git y comparar entre versiones.

## Alcance del producto mínimo (al final del Sprint 4)

- Preguntas de opción múltiple, verdadero/falso y respuesta abierta.
- Puntos por pregunta y secciones.
- Validador con mensajes de error que incluyan la línea.
- Aplicar el cuestionario en consola y mostrar la calificación.
- Exportar a JSON y a HTML.
- Especificación del lenguaje, manual de usuario y pruebas.

## Fuera del alcance

- Interfaz gráfica o página web para editar cuestionarios.
- Guardar las respuestas de los alumnos en una base de datos.
- Preguntas con imágenes o fórmulas matemáticas.

## Cómo sabremos que funciona

- Se puede escribir un cuestionario de al menos 10 preguntas sin tocar código.
- Un archivo con errores muestra mensajes que la docente entiende sin explicación extra.
- El mismo archivo `.cst` genera una versión en consola, una en HTML y una en JSON con las mismas preguntas.
