# CLAUDE.md

Este archivo define cómo Claude Code debe trabajar dentro del repositorio Trinity AI.

Su objetivo es asegurar que Claude entienda:

- qué es Trinity AI;
- cómo está organizado;
- qué documentos tienen autoridad;
- cómo debe leer el repositorio;
- cuándo puede crear, modificar o ejecutar algo;
- cómo debe reutilizar conocimiento;
- cómo debe respetar Governance;
- cómo debe trabajar sin inventar información ni duplicar documentación.

---

# Qué es Trinity AI

Trinity AI es un AI Operating System orientado a planificación, creación, organización y ejecución de procesos de marketing y contenido mediante inteligencia artificial.

No es una aplicación tradicional.

No es solamente una colección de archivos Markdown.

No es una biblioteca de prompts.

Es un sistema compuesto por:

- CORE;
- Foundation;
- Architecture;
- Agents;
- Frameworks;
- SOPs;
- Knowledge;
- Research;
- Integrations;
- Automations;
- Client Context;
- Templates;
- Assets;
- Examples;
- Governance.

El repositorio funciona como la fuente documental compartida del sistema.

Claude Code debe trabajar sobre esta documentación respetando sus responsabilidades, estados, dependencias y jerarquías.

---

# Idioma

La documentación principal del repositorio debe mantenerse en español salvo que exista una necesidad específica de utilizar otro idioma.

Claude debe responder y crear documentación en español por defecto.

---

# Punto de entrada

Antes de realizar trabajo relevante dentro del repositorio, Claude debe comenzar por:

```text
CORE.md
```

CORE.md define el flujo operativo completo y enumera todos los módulos del sistema (00_Foundation a 13_Governance) con su responsabilidad. No debe duplicarse esa lista aquí.

---

# Naturaleza del repositorio

Trinity AI no es un repositorio de código.

No existe build, lint ni test suite.

Todo el contenido es documentación en Markdown, principalmente en español.

El trabajo de Claude en este repositorio es leer, redactar o reestructurar documentación siguiendo las reglas de este archivo y las de `00_Foundation` y `01_Architecture`.

---

# Fuente de verdad documental

Todo documento del sistema incluye un campo `status` en su front matter (`Planned`, `Draft`, `Review`, `Approved`, `Deprecated`, `Archived`).

Claude Code únicamente debe tratar como fuente oficial los documentos en estado `Approved`.

Los documentos `Draft`, `Review` o `Planned` no deben usarse para tomar decisiones ni citarse como conocimiento definitivo.

Un documento `Approved` nunca se edita directamente: todo cambio vuelve a pasar por `Draft → Review → Approved` (ver `13_Governance/`).

Hoy la mayoría de los documentos del sistema, incluido CORE.md, están en `Draft`. Esto debe señalarse cuando sea relevante para la respuesta.

---

# Documentos nuevos

Todo documento nuevo debe partir de la plantilla correspondiente en `09_Templates/` y seguir la estructura y el front matter definidos en `00_Foundation/13_Documentation_Standards.md`.