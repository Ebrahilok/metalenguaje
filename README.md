# Cuestiona: un metalenguaje para describir cuestionarios

Proyecto de la materia **Procesadores de Lenguajes** (Ingeniería de Software, Grupo “04” J303, Universidad Autónoma de Occidente). Profesora: Nidia Deniss Lugo.

**Cuestiona** es un lenguaje de dominio específico (DSL), o sea, un lenguaje pequeño hecho para un solo tema. En este caso el tema son los cuestionarios y exámenes. La idea es que un docente pueda escribir un examen en un archivo de texto sencillo (`.cst`) y que la herramienta revise si está bien escrito, lo aplique en la consola y lo convierta a otros formatos como HTML o JSON.

El proyecto se trabaja con **Scrum** en 4 sprints de una semana.

## Estado actual

| Etapa | Contenido | Estado |
|---|---|---|
| Semana 0: Preparación | Visión, backlog inicial, Definition of Done, roles | ✅ Entregada |
| Sprint 1: Fundamentos y especificación | Investigación de metalenguajes, gramática y notación v0.1 | ⏳ Pendiente |
| Sprint 2: Núcleo | Analizador léxico y sintáctico, semántica, pruebas unitarias | ⏳ Pendiente |
| Sprint 3: Ampliación y validación | Más construcciones, mensajes de error, ejemplos, validación con la docente | ⏳ Pendiente |
| Sprint 4: Cierre | Manual de usuario, documentación técnica, demo final | ⏳ Pendiente |

## Una idea de cómo se va a ver

Esto es solo un **boceto preliminar**. La sintaxis oficial se define en el Sprint 1 y puede cambiar.

```text
cuestionario "Repaso de Procesadores de Lenguajes"

seccion "Conceptos básicos"

pregunta opcion "¿Qué es un metalenguaje?" puntos 2
  - "Un formato de imagen"
  * "Un lenguaje que sirve para describir otros lenguajes"
  - "Un sistema operativo"

pregunta vf "Un analizador léxico separa el texto en tokens." puntos 1
  respuesta verdadero

pregunta abierta "¿Qué significan las siglas DSL?" puntos 1
  acepta "lenguaje de dominio especifico", "domain specific language"
```

## Equipo

| Integrante | Rol Scrum |
|---|---|
| Ebrahim Ali | Product Owner y Development Team |
| Rey David Ayala Noriega | Scrum Master y Development Team |
| *(lugar disponible)* | Development Team |

Todos participamos en el desarrollo, aunque cada quien tenga un rol definido. Si entra un tercer integrante se agrega a esta tabla y al documento de roles.

## Documentación

- [Visión del producto](docs/semana-0/vision-del-producto.md)
- [Product Backlog](docs/semana-0/product-backlog.md)
- [Definition of Done](docs/semana-0/definition-of-done.md)
- [Equipo y roles](docs/semana-0/equipo-y-roles.md)
- [Plantillas para los eventos de cada sprint](docs/sprints/plantillas/)
- [Declaración de uso de IA](docs/uso-de-ia.md)

## Tecnología

- **Python 3.11 o superior** para el analizador, el validador y el intérprete.
- **pytest** para las pruebas.
- **GitHub Projects** como tablero Scrum.

## Estructura del repositorio

```text
metalenguaje/
├── README.md
├── docs/
│   ├── semana-0/          # Visión, backlog, DoD y roles
│   ├── sprints/           # Actas, sprint backlogs y burndown de cada sprint
│   │   └── plantillas/
│   └── uso-de-ia.md
├── src/                   # Código del metalenguaje (desde el Sprint 2)
├── ejemplos/              # Cuestionarios válidos e inválidos (desde el Sprint 2)
└── tests/                 # Pruebas unitarias y de integración (desde el Sprint 2)
```

Las carpetas `src/`, `ejemplos/` y `tests/` se crean cuando empiece la implementación.
