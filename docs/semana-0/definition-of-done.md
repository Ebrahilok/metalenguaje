# Definition of Done

Una historia de usuario se considera **terminada** solo si cumple con todo lo siguiente:

1. **Código funcional:** el código hace lo que dicen los criterios de aceptación de la historia y se puede ejecutar sin errores.
2. **Pruebas:** hay pruebas automáticas (pytest) que revisan los criterios de aceptación, y todas las pruebas del proyecto pasan.
3. **Documentación actualizada:** si la historia cambia el lenguaje, se actualiza la especificación. Si cambia cómo se usa la herramienta, se actualiza el manual o el README.
4. **Revisión por un compañero:** otro integrante del equipo revisó el cambio en un Pull Request y lo aprobó antes de unirlo a `main`.
5. **Ejemplos:** si se agrega una construcción nueva al lenguaje, se agrega al menos un ejemplo válido y uno inválido en la carpeta `ejemplos/`.
6. **Tablero al día:** la tarjeta de la historia está en la columna "Terminado" del tablero.

Para historias que solo son documentos (por ejemplo, la investigación o la especificación), los puntos 1, 2 y 5 se cambian por esto: el documento está en el repositorio, en formato Markdown y revisado por otro integrante.
