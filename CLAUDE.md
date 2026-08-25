# CLAUDE.md

Este archivo define cómo Claude Code debe trabajar dentro del repositorio Trinity AI.

---

# Qué es Trinity AI

Trinity AI es un AI Operating System orientado a planificación, organización y ejecución de procesos de marketing y contenido mediante inteligencia artificial.

El repositorio funciona como su fuente documental compartida.

Claude Code debe trabajar como colaborador dentro de Trinity AI y respetar:

* CORE;
* Foundation;
* Architecture;
* Governance;
* estados documentales;
* permisos;
* dependencias.

---

# Idioma

La documentación debe mantenerse principalmente en español salvo que exista una necesidad específica de utilizar otro idioma.

---

# Punto de Entrada

Claude debe comenzar por:

```text
CORE.md
```

CORE define el comportamiento operativo general.

Después debe recuperar únicamente la documentación necesaria para la tarea.

No debe recorrer todos los módulos obligatoriamente.

---

# Arquitectura

Trinity AI utiliza una arquitectura modular por capas.

Claude debe consultar selectivamente:

```text
CORE
Foundation
Architecture
Agents
Frameworks
Knowledge
SOPs
Research
Integrations
Automations
Client Context
Templates
Assets
Examples
Governance
```

La existencia de un componente no implica que deba utilizarse.

---

# Estados Documentales

Los estados oficiales son:

```text
Planned
Draft
Review
Approved
Deprecated
Archived
```

## Durante desarrollo

Claude puede utilizar:

```text
Approved
→ fuente oficial

Review
→ referencia de desarrollo

Draft
→ material de construcción
```

`Draft` y `Review` nunca deben presentarse como reglas definitivas.

## Durante producción

Claude debe utilizar `Approved` como fuente oficial.

`Review` puede consultarse como referencia no autoritativa cuando sea necesario.

`Draft` no debe gobernar decisiones operativas de producción.

---

# Reutilización

Antes de crear algo nuevo Claude debe:

```text
Buscar
  ↓
Reutilizar
  ↓
Adaptar
  ↓
Crear
```

Debe evitar duplicar:

* Knowledge;
* Frameworks;
* SOPs;
* Agents;
* Templates;
* Research;
* Integrations;
* Automations.

---

# Recuperación Selectiva

Claude no debe cargar todo el repositorio.

Debe identificar primero qué información necesita y recuperar únicamente las fuentes relevantes.

Más contexto no significa automáticamente mejor resultado.

---

# Orchestrator

Cuando una solicitud requiera coordinación entre múltiples Agents o capacidades, Claude debe respetar:

```text
01_Architecture/ORCHESTRATOR.md
```

El Orchestrator coordina.

No reemplaza a los Agents especializados.

---

# Agents

Los Agents deben trabajar dentro de su alcance.

Pueden utilizar selectivamente:

* Frameworks;
* Knowledge;
* SOPs;
* Research;
* Client Context;
* Templates;
* Assets;
* Integrations;
* Automations.

No existe obligación de utilizar todas estas capacidades.

---

# Client Context

La información específica de clientes debe permanecer dentro de:

```text
08_Clients/
```

No debe convertirse automáticamente en conocimiento global.

---

# Research

Research no constituye automáticamente Knowledge.

Un aprendizaje debe pasar primero por:

```text
Candidate
   ↓
Review
   ↓
Approval
```

antes de convertirse en memoria permanente cuando corresponda.

---

# Integrations y Automations

Claude solo debe utilizarlas cuando:

* sean necesarias;
* estén disponibles;
* existan permisos;
* el riesgo lo permita;
* exista aprobación humana cuando corresponda.

Una Automation disponible no debe ejecutarse únicamente porque exista.

---

# Riesgo y Aprobación

Claude debe respetar los niveles definidos por CORE y el Decision Framework.

Como principio:

```text
Bajo riesgo + reversible + autorizado
→ ejecutar

Riesgo moderado
→ validar

Alto riesgo o baja reversibilidad
→ solicitar aprobación

Sin permisos
→ no ejecutar
```

El silencio nunca constituye aprobación.

---

# Documentación

Todo documento nuevo debe:

* comenzar como `Draft`;
* respetar `13_Documentation_Standards.md`;
* utilizar una Template cuando exista;
* declarar dependencias relevantes;
* evitar duplicación;
* mantener una responsabilidad clara.

Los documentos `Approved` no deben modificarse silenciosamente.

---

# Credenciales

Claude nunca debe almacenar directamente en el repositorio:

* API keys;
* tokens;
* passwords;
* claves privadas;
* secrets;
* credenciales.

---

# GitHub

Antes de realizar cambios relevantes:

* revisar estado del repositorio;
* identificar archivos afectados;
* evitar cambios no relacionados.

Después:

* revisar diferencias;
* validar formato;
* crear commits descriptivos;
* verificar push;
* confirmar sincronización.

---

# Restricciones

Claude no debe:

* inventar información;
* tratar Draft como fuente oficial;
* duplicar conocimiento;
* utilizar múltiples Agents sin necesidad;
* cargar todo el repositorio;
* ejecutar acciones sensibles sin autorización;
* confundir Research con Knowledge;
* mezclar Client Context con Knowledge global;
* modificar Architecture por conveniencia local;
* ocultar errores o incertidumbre.

---

# Regla de Oro

Claude Code debe trabajar como parte de Trinity AI, no como un sistema paralelo.

```text
Comprender
   ↓
Recuperar lo necesario
   ↓
Reutilizar
   ↓
Ejecutar dentro de permisos
   ↓
Validar
   ↓
Documentar solo cuando aporta valor
```

Toda intervención debe reducir trabajo repetitivo y fortalecer el sistema sin agregar complejidad innecesaria.
