---
id: TRI-CLAUDE-001
title: Claude Code Repository Instructions
module: Root
version: 1.1.0
status: Draft
owner: Trinity AI
created:
last_updated: 2026-08-25
reviewed_by:
approved_by:
next_review:
dependencies:
  - CORE.md
  - 00_Foundation/13_Documentation_Standards.md
tags:
  - claude-code
  - repository
  - development
  - instructions
---

# Trinity AI — Claude Code Repository Instructions

Este archivo define cómo Claude Code debe trabajar dentro del repositorio Trinity AI.

Claude Code funciona como colaborador técnico dentro del sistema.

No constituye una arquitectura, fuente de conocimiento o sistema de gobernanza paralelo.

---

## Qué es Trinity AI

Trinity AI es un AI Operating System orientado a planificación, organización y ejecución de procesos de marketing y contenido mediante inteligencia artificial.

El repositorio funciona como fuente documental compartida del sistema.

Claude Code debe trabajar respetando:

- CORE;
- Foundation;
- Architecture;
- Governance;
- estados documentales;
- permisos;
- dependencias;
- límites de cada módulo.

Cuando exista una fuente oficial responsable de una regla, Claude debe respetarla en lugar de reconstruirla localmente.

---

## Propósito de este Archivo

Este archivo proporciona instrucciones específicas para Claude Code cuando trabaja dentro del repositorio.

Su responsabilidad es conectar el entorno de desarrollo con las reglas existentes de Trinity AI.

No debe duplicar innecesariamente:

- CORE;
- Foundation;
- Architecture;
- Governance;
- SOPs;
- Frameworks;
- Knowledge.

Cuando exista conflicto entre este archivo y una fuente superior vigente, debe respetarse la fuente superior.

---

## Idioma

La documentación debe mantenerse principalmente en español salvo que exista una necesidad específica de utilizar otro idioma.

Los nombres técnicos, identificadores, código y términos cuya traducción reduzca precisión pueden mantenerse en inglés.

---

## Punto de Entrada

Claude Code debe comenzar por:

```text
CORE.md
```

CORE define la referencia operativa principal.

Después debe recuperar únicamente la documentación necesaria para la tarea.

```text
Request
   │
   ▼
CORE
   │
   ▼
Identify Need
   │
   ▼
Selective Retrieval
```

No debe recorrer todos los módulos obligatoriamente.

---

## Arquitectura

Trinity AI utiliza una arquitectura modular.

Claude Code puede consultar selectivamente:

```text
CORE
Foundation
Architecture
SOPs
Agents
Frameworks
Knowledge
Integrations
Automations
Client Context
Templates
Assets
Examples
Research
Governance
```

La existencia de un componente no implica que deba utilizarse.

La recuperación debe responder a una necesidad real de la tarea.

---

## Jerarquía Documental

Como principio operativo:

```text
CORE
   │
   ▼
Foundation
   │
   ▼
Architecture
   │
   ▼
Module Standards
   │
   ▼
Specific Documents
```

Esta representación indica autoridad y responsabilidad conceptual.

No significa que Claude Code deba cargar todos esos niveles para cada tarea.

Cuando exista una fuente más específica compatible con las reglas superiores, puede utilizarse directamente después de recuperar el contexto mínimo necesario.

---

## Estados Documentales

Los estados oficiales son:

```text
Draft
Review
Approved
Deprecated
Archived
```

`Planned` no forma parte del lifecycle documental oficial.

### Durante Desarrollo

Claude Code puede utilizar:

```text
Approved
→ fuente oficial

Review
→ referencia controlada

Draft
→ material en construcción
```

`Draft` y `Review` no deben presentarse como reglas oficiales vigentes.

### Durante Producción

Claude Code debe priorizar documentos `Approved` como fuentes oficiales dentro de su alcance.

`Review` puede utilizarse como referencia no autoritativa cuando sea necesario.

`Draft` no debe gobernar decisiones operativas de producción salvo que exista una instrucción explícita y autorizada para trabajar sobre ese material.

### Deprecated

Un documento `Deprecated` no debe utilizarse para nuevas implementaciones cuando exista un reemplazo vigente.

Puede consultarse por:

- compatibilidad;
- migración;
- trazabilidad;
- contexto histórico.

### Archived

Un documento `Archived` se conserva principalmente por trazabilidad.

No debe utilizarse como fuente operativa vigente.

---

## Reutilización

Antes de crear algo nuevo Claude Code debe seguir:

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

- Knowledge;
- Frameworks;
- SOPs;
- Agents;
- Templates;
- Research;
- Integrations;
- Automations;
- reglas de Foundation;
- definiciones de Architecture.

Crear debe ser la última opción cuando una fuente existente no pueda resolver correctamente la necesidad.

---

## Recuperación Selectiva

Claude Code no debe cargar todo el repositorio.

Debe identificar primero:

```text
¿Qué tarea debo resolver?
        ↓
¿Qué responsabilidad está involucrada?
        ↓
¿Qué documentos necesito?
        ↓
¿Cuál es el contexto mínimo suficiente?
```

Más contexto no significa automáticamente mejor resultado.

La recuperación selectiva reduce:

- ruido;
- contradicciones;
- costo de contexto;
- dependencia innecesaria;
- riesgo de utilizar documentación irrelevante.

---

## Orchestrator

Cuando una solicitud requiera coordinación entre múltiples Agents o capacidades, Claude Code debe respetar:

```text
01_Architecture/ORCHESTRATOR.md
```

El Orchestrator coordina.

No reemplaza a los Agents especializados.

Claude Code no debe inventar una segunda lógica de orquestación paralela cuando ya exista una definición arquitectónica aplicable.

---

## Agents

Los Agents deben trabajar dentro de su alcance.

Pueden utilizar selectivamente:

- Frameworks;
- Knowledge;
- SOPs;
- Research;
- Client Context;
- Templates;
- Assets;
- Integrations;
- Automations.

No existe obligación de utilizar todas estas capacidades.

Claude Code debe evitar asignar responsabilidades a un Agent que pertenezcan claramente a otro componente del sistema.

---

## SOPs

Los SOPs definen procedimientos operativos repetibles.

Claude Code debe utilizarlos cuando exista una tarea operativa cubierta por un SOP aplicable.

Un SOP responde principalmente:

> ¿Cómo debe ejecutarse esta tarea?

Claude Code no debe convertir automáticamente un Framework o documento de Knowledge en un procedimiento operativo.

---

## Frameworks

Los Frameworks proporcionan metodologías reutilizables.

Responden principalmente:

> ¿Cómo debe estructurarse y abordarse este tipo de problema?

Claude Code debe reutilizar Frameworks existentes antes de crear metodologías nuevas.

Un Framework no debe tratarse como un SOP.

---

## Knowledge

Knowledge contiene información reutilizable.

Responde principalmente:

> ¿Qué necesita saber Trinity AI?

Claude Code debe recuperar únicamente Knowledge relevante para la tarea.

No debe convertir automáticamente información temporal, contexto de clientes o Research reciente en Knowledge global.

---

## Client Context

La información específica de clientes debe permanecer principalmente dentro de:

```text
08_Clients/
```

Esto incluye, cuando corresponda:

- objetivos;
- productos;
- branding;
- audiencias;
- campañas;
- performance;
- decisiones;
- restricciones;
- historial específico.

Client Context no debe convertirse automáticamente en conocimiento global.

---

## Research

Research permite obtener o validar información cuando:

- falta;
- puede haber cambiado;
- existe incertidumbre;
- se necesita evidencia;
- una decisión depende de información externa.

Research no constituye automáticamente Knowledge.

La promoción conceptual es:

```text
Research
   │
   ▼
Finding
   │
   ▼
Reusable?
   │
   ├── No → remain finding
   │
   └── Sí
          │
          ▼
       Candidate
          │
          ▼
        Review
          │
          ▼
       Approval
          │
          ▼
       Knowledge
```

La promoción debe respetar el proceso correspondiente.

---

## Integrations y Automations

Claude Code solo debe utilizar Integrations o Automations cuando:

- sean necesarias;
- estén disponibles;
- existan permisos;
- el riesgo lo permita;
- la acción esté dentro del alcance;
- exista aprobación humana cuando corresponda.

Una Integration disponible no implica permiso para cualquier acción.

Una Automation disponible no debe ejecutarse únicamente porque exista.

---

## Riesgo y Aprobación

Claude Code debe respetar los criterios definidos por CORE y Foundation.

Como principio:

```text
Bajo riesgo
+
Reversible
+
Autorizado
→ ejecutar cuando corresponda

Riesgo moderado
→ validar según contexto

Alto riesgo
o
Baja reversibilidad
→ solicitar aprobación cuando corresponda

Sin permisos
→ no ejecutar
```

El silencio nunca constituye aprobación.

Claude Code no debe ampliar permisos por inferencia.

---

## Documentación

Todo documento nuevo debe:

- comenzar como `Draft`;
- respetar `00_Foundation/13_Documentation_Standards.md`;
- utilizar una Template cuando exista y sea aplicable;
- declarar dependencias reales;
- evitar duplicación;
- mantener una responsabilidad clara;
- utilizar metadata especializada únicamente cuando esté definida por el estándar correspondiente.

Los documentos `Approved` no deben modificarse silenciosamente.

---

## Front Matter

Cuando un documento requiera Front Matter debe respetar Documentation Standards.

El bloque YAML debe comenzar en la primera línea del archivo.

Ejemplo:

```yaml
---
id: TRI-MOD-001
title: Example
module: Module
version: 1.0.0
status: Draft
owner: Trinity AI
dependencies: []
tags:
  - example
---
```

Los estándares modulares pueden agregar metadata especializada cuando esté formalmente definida.

---

## Jerarquía Markdown

Los documentos gobernados deben utilizar:

```text
# Título único

## Sección principal

### Subsección
```

Debe existir un único H1 por documento.

Los niveles de encabezado deben representar jerarquía conceptual, no únicamente estilo visual.

---

## Dependencias

Claude Code debe distinguir:

```text
Dependency
→ necesaria para interpretar o aplicar el documento

Reference
→ relacionada, pero no necesaria
```

No debe convertir:

- carpetas completas;
- módulos relacionados;
- menciones conceptuales;

en dependencias formales sin necesidad.

Debe evitar dependencias circulares.

---

## Credenciales

Claude Code nunca debe almacenar directamente en el repositorio:

- API keys;
- tokens;
- passwords;
- claves privadas;
- secrets;
- credenciales.

Tampoco debe incluir información sensible de clientes dentro de Knowledge global.

---

## Trabajo con Archivos

Antes de modificar un archivo Claude Code debe:

1. identificar su responsabilidad;
2. revisar las fuentes necesarias;
3. determinar el alcance del cambio;
4. evitar modificaciones no relacionadas;
5. preservar contenido correcto que esté fuera del alcance.

Cuando el usuario solicite una corrección específica, Claude Code no debe aprovecharla para rediseñar componentes no relacionados sin autorización.

---

## Cambios Múltiples

Cuando una tarea requiera modificar varios archivos:

```text
Identify Scope
      │
      ▼
Identify Dependencies
      │
      ▼
Modify
      │
      ▼
Cross-document Validation
      │
      ▼
git diff
```

Los cambios deben mantenerse dentro del alcance aprobado.

---

## GitHub

Antes de realizar cambios relevantes Claude Code debe:

- revisar el estado del repositorio;
- identificar archivos afectados;
- evitar cambios no relacionados;
- verificar la rama actual cuando sea relevante.

Después de modificar:

- revisar diferencias;
- validar formato;
- revisar archivos afectados;
- comprobar que no existan modificaciones accidentales.

Antes de commit:

```text
git status
    +
git diff
    +
scope validation
```

Cuando el usuario autorice commit y push:

- utilizar un commit descriptivo;
- verificar el resultado;
- confirmar sincronización.

Claude Code no debe hacer commit o push cuando el usuario haya solicitado explícitamente esperar aprobación.

---

## Cambios Arquitectónicos

Claude Code no debe modificar Architecture por conveniencia local.

Si una necesidad requiere cambiar:

- responsabilidades;
- módulos;
- relaciones;
- flujos;
- límites;
- coordinación;

debe tratarse como un cambio arquitectónico.

La secuencia conceptual es:

```text
Need
 │
 ▼
Architecture Impact?
 │
 ├── No → local change
 │
 └── Sí
       │
       ▼
   Impact Analysis
       │
       ▼
   Review / Approval
```

---

## Cambios a Foundation

Claude Code no debe modificar reglas fundamentales únicamente para hacer compatible un documento inferior.

Cuando exista una incompatibilidad debe determinarse primero:

```text
¿El documento inferior está incorrecto?
        │
        ├── Sí → corregir documento inferior
        │
        └── No
             │
             ▼
¿Existe una necesidad global real?
             │
             ├── No → mantener Foundation
             │
             └── Sí → proponer cambio gobernado
```

Esto evita que excepciones locales deformen reglas globales.

---

## Validación Cruzada

Cuando un cambio pueda afectar más de un documento, Claude Code debe comprobar:

- responsabilidades;
- términos;
- estados;
- dependencias;
- rutas;
- jerarquía;
- reglas compartidas;
- ausencia de contradicciones.

Una validación cruzada no implica modificar automáticamente todos los documentos relacionados.

---

## Incertidumbre

Claude Code debe diferenciar cuando corresponda:

```text
Known
Inferred
Unknown
Candidate
```

No debe presentar una inferencia como hecho.

Cuando falte información crítica debe:

- recuperarla;
- investigarla;
- solicitarla;
- o escalar;

según corresponda.

---

## Restricciones

Claude Code no debe:

- inventar información;
- tratar `Draft` como fuente oficial;
- tratar `Review` como `Approved`;
- utilizar `Deprecated` como fuente principal cuando exista reemplazo;
- utilizar `Archived` como fuente vigente;
- duplicar conocimiento;
- utilizar múltiples Agents sin necesidad;
- cargar todo el repositorio;
- ejecutar acciones sensibles sin autorización;
- confundir Research con Knowledge;
- mezclar Client Context con Knowledge global;
- modificar Architecture por conveniencia local;
- modificar Foundation para resolver excepciones locales sin justificación global;
- crear dependencias innecesarias;
- almacenar credenciales;
- ocultar errores;
- ocultar contradicciones;
- ocultar incertidumbre;
- hacer commit o push contra una instrucción explícita de esperar aprobación.

---

## Validación Final

Antes de considerar terminado un cambio documental relevante:

```text
Scope correct?
      ↓
Responsibilities preserved?
      ↓
Documentation Standards respected?
      ↓
Dependencies valid?
      ↓
Cross-document contradictions?
      ↓
git diff reviewed?
      ↓
Ready
```

Si una validación falla, el cambio no debe considerarse finalizado.

---

## Criterios de Éxito

Claude Code está trabajando correctamente dentro de Trinity AI cuando:

- comienza desde CORE;
- recupera únicamente contexto relevante;
- respeta Foundation;
- respeta Architecture;
- reutiliza antes de crear;
- diferencia SOP, Framework y Knowledge;
- mantiene Client Context aislado;
- utiliza Research cuando falta evidencia;
- respeta estados documentales;
- respeta permisos;
- mantiene cambios dentro del alcance;
- valida antes de cerrar;
- utiliza Git de forma controlada;
- fortalece el sistema sin crear arquitectura paralela.

---

## Regla de Oro

> Claude Code debe trabajar como parte de Trinity AI, no como un sistema paralelo.

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