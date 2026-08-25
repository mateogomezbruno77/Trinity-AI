---
id: TRI-ARCH-003
title: Request Lifecycle
module: Architecture
version: 1.2.0
status: Draft
owner: Trinity AI
created:
last_updated: 2026-08-25
reviewed_by:
approved_by:
next_review:
dependencies:
  - CORE.md
  - 01_Architecture/SYSTEM_ARCHITECTURE.md
  - 01_Architecture/DATA_FLOW.md
  - 00_Foundation/14_AI_Behavior.md
  - 00_Foundation/15_Thinking_Framework.md
  - 00_Foundation/16_Decision_Framework.md
tags:
  - architecture
  - request
  - lifecycle
  - states
  - execution
  - validation
---

# Trinity AI - Request Lifecycle

## Propósito

Este documento define el ciclo de vida operativo de una solicitud dentro de Trinity AI.

Su objetivo es describir:

- qué estados puede atravesar una solicitud;
- cuándo cambia de estado;
- qué condiciones permiten avanzar;
- cuándo una solicitud queda bloqueada;
- cuándo requiere aprobación;
- cuándo debe corregirse;
- cuándo se considera completada.

Request Lifecycle define estados de trabajo.

No define:

- el comportamiento general de la IA;
- la circulación detallada de información;
- la coordinación completa entre Agents;
- estados documentales;
- procesos específicos de negocio.

---

## Objetivo

El lifecycle debe permitir que Trinity AI procese solicitudes de forma:

- consistente;
- proporcional;
- observable;
- recuperable;
- trazable cuando corresponda;
- flexible.

No todas las solicitudes deben recorrer exactamente las mismas etapas.

La complejidad del lifecycle debe adaptarse al trabajo real.

---

## Principio Fundamental

> Una solicitud debe atravesar únicamente los estados necesarios para ser resuelta correctamente.

Debe evitarse:

```text
Solicitud simple
      │
      ▼
11 etapas obligatorias
      │
      ▼
Burocracia
```

Debe favorecerse:

```text
Solicitud
   │
   ▼
Mínimo lifecycle necesario
   │
   ▼
Resultado válido
```

---

## Estados Operativos

Los estados principales de una solicitud son:

```text
Received
Understanding
Ready
In Progress
Waiting for Dependency
Waiting for Approval
Blocked
Needs Correction
Validation
Completed
Failed
Cancelled
```

No todas las solicitudes utilizan todos estos estados.

---

## Estados vs Etapas

Un estado representa la condición actual de la solicitud.

Una etapa representa trabajo que puede ocurrir dentro de uno o varios estados.

Ejemplo:

```text
Estado:
In Progress

Puede incluir:
- Research
- Planning
- Production
- Execution
```

Request Lifecycle no debe confundirse con un workflow rígido.

---

## Diferencia con Estados Documentales

Los estados operativos de solicitudes son distintos de los estados documentales.

### Estados Operativos

```text
Received
Understanding
Ready
In Progress
Waiting for Dependency
Waiting for Approval
Blocked
Needs Correction
Validation
Completed
Failed
Cancelled
```

### Estados Documentales

```text
Draft
Review
Approved
Deprecated
Archived
```

No deben mezclarse.

Ejemplo:

```text
Request status:
In Progress

Document status:
Draft
```

Son dimensiones diferentes.

---

## Lifecycle General

El flujo conceptual puede representarse así:

```text
Received
   │
   ▼
Understanding
   │
   ▼
Ready
   │
   ▼
In Progress
   │
   ├── Waiting for Dependency
   │
   ├── Waiting for Approval
   │
   ├── Blocked
   │
   └── Needs Correction
   │
   ▼
Validation
   │
   ├── Needs Correction
   │
   ├── Blocked
   │
   └── Failed
   │
   ▼
Completed
```

Puede finalizar también en:

```text
Cancelled
Failed
```

---

## Estado 1 — Received

Una solicitud entra en `Received` cuando Trinity AI la recibe.

Debe existir suficiente información para identificar que existe una nueva necesidad.

Puede incluir:

- mensaje;
- archivo;
- instrucción;
- evento;
- trigger;
- resultado de una Automation;
- solicitud proveniente de otro componente.

---

## Objetivo de Received

El objetivo es registrar que existe trabajo pendiente de interpretación.

No implica que Trinity AI ya comprenda suficientemente la solicitud.

---

## Transición desde Received

```text
Received
   │
   ▼
Understanding
```

Debe avanzar cuando el sistema comienza a interpretar:

- objetivo;
- intención;
- contexto;
- restricciones;
- resultado esperado.

---

## Estado 2 — Understanding

En este estado Trinity AI intenta comprender qué necesita resolverse.

Puede identificar:

- solicitud explícita;
- objetivo real;
- cliente;
- proyecto;
- restricciones;
- contexto;
- incertidumbre;
- información faltante;
- posibles acciones externas.

---

## Salidas de Understanding

Puede avanzar a:

```text
Ready
```

cuando existe suficiente claridad.

Puede ir a:

```text
Blocked
```

cuando falta información crítica que no puede recuperarse.

Puede terminar en:

```text
Cancelled
```

si la solicitud deja de ser válida.

---

## Criterio de suficiencia

No se necesita certeza absoluta para avanzar.

Debe existir contexto suficiente para trabajar correctamente.

```text
Suficiente información
+
Riesgo controlado
=
Ready
```

---

## Estado 3 — Ready

Una solicitud está `Ready` cuando:

- el objetivo está suficientemente claro;
- se entiende qué resultado se necesita;
- existen capacidades para avanzar;
- no hay bloqueos críticos;
- el nivel inicial de riesgo permite comenzar.

---

## Ready no significa Planned

Una solicitud puede estar lista sin necesitar un plan formal.

Ejemplo:

```text
"Corregime este copy."
```

Puede pasar:

```text
Received
→ Understanding
→ Ready
→ In Progress
```

sin una etapa explícita de Planning.

---

## Estado 4 — In Progress

`In Progress` representa trabajo activo.

Puede incluir:

- Research;
- Strategy;
- Planning;
- Analysis;
- Creation;
- Documentation;
- Execution;
- Integration;
- Automation;
- Coordination;
- Agent collaboration.

---

## In Progress y Agents

Una solicitud puede ser ejecutada por:

```text
Single Agent
```

o por:

```text
Orchestrator
+
Multiple Agents
```

según complejidad.

Request Lifecycle no define cómo colaboran.

Eso pertenece a:

```text
01_Architecture/AGENT_INTERACTION.md
```

y:

```text
01_Architecture/ORCHESTRATOR.md
```

---

## Subtareas

Una solicitud puede contener subtareas con estados independientes.

Ejemplo:

```text
Request: In Progress

Task A: Completed
Task B: In Progress
Task C: Waiting for Dependency
```

El estado global debe representar la condición de la solicitud completa.

---

## Estado 5 — Waiting for Dependency

Se utiliza cuando la solicitud no puede avanzar hasta que otra condición o tarea termine.

Ejemplos:

- Research pendiente;
- Agent anterior no finalizó;
- archivo faltante;
- Integration pendiente;
- Automation pendiente;
- resultado externo requerido.

---

## Flujo de Dependency

```text
In Progress
    │
    ▼
Waiting for Dependency
    │
    ▼
Dependency resolved
    │
    ▼
In Progress
```

---

## Regla de Dependency

No debe marcarse una tarea como `Blocked` si simplemente está esperando una dependencia normal y conocida.

Debe diferenciarse:

```text
Waiting for Dependency
→ espera prevista

Blocked
→ impedimento que necesita resolución
```

---

## Estado 6 — Waiting for Approval

Se utiliza cuando una acción no puede continuar sin autorización explícita.

Ejemplos:

- publicación;
- eliminación;
- cambio estructural;
- modificación sensible;
- acción externa;
- cambio de permisos;
- gasto;
- acción difícilmente reversible.

---

## Flujo de Approval

```text
In Progress
    │
    ▼
Waiting for Approval
    │
    ├── Approved
    │      │
    │      ▼
    │  In Progress
    │
    └── Rejected
           │
           ▼
       Cancelled
       o
       In Progress
       con alternativa
```

---

## Silencio

El silencio nunca debe interpretarse como aprobación.

```text
No response
≠
Approved
```

---

## Alcance de aprobación

La aprobación aplica únicamente a la acción solicitada.

Ejemplo:

```text
"Aprobado modificar REQUEST_LIFECYCLE.md"
```

no significa:

```text
"Aprobado modificar todo Architecture"
```

---

## Estado 7 — Blocked

Se utiliza cuando existe un impedimento que no puede resolverse automáticamente.

Ejemplos:

- falta de información crítica;
- permiso insuficiente;
- Integration no disponible;
- contradicción no resuelta;
- dependencia rota;
- recurso inexistente;
- riesgo inaceptable.

---

## Estructura de un bloqueo

Cuando sea relevante debe poder identificarse:

```yaml
status: Blocked
reason:
required_action:
responsible:
```

---

## Flujo de Blocked

```text
Blocked
   │
   ▼
Resolve Blocker
   │
   ├── Resolved → Ready / In Progress
   └── Unresolved → Failed / Cancelled
```

---

## Blocked no significa Failed

`Blocked` significa que puede existir una vía para continuar.

`Failed` significa que la ejecución actual no pudo completarse correctamente.

---

## Estado 8 — Needs Correction

Se utiliza cuando existe un resultado parcial que no cumple requisitos pero puede corregirse.

Puede aparecer después de:

- Agent output;
- Validation;
- Integration;
- Automation;
- revisión humana;
- auditoría.

---

## Flujo de Correction

```text
Result
   │
   ▼
Validation
   │
   ▼
Needs Correction
   │
   ▼
In Progress
   │
   ▼
Validation
```

---

## Corrección vs reinicio

Una corrección no debe reiniciar automáticamente toda la solicitud.

Debe volver únicamente al componente afectado cuando sea posible.

```text
Error local
→ corrección local

Error estructural
→ reevaluación más amplia
```

---

## Estado 9 — Validation

Una solicitud entra en `Validation` cuando existe un resultado suficientemente completo para verificar.

Validation puede revisar:

- cumplimiento del objetivo;
- calidad;
- consistencia;
- fuentes;
- restricciones;
- permisos;
- riesgo;
- completitud;
- resultado de ejecuciones;
- errores.

---

## Validation proporcional

No todas las solicitudes necesitan el mismo nivel de validación.

```text
Low Impact
→ lightweight validation

Medium Impact
→ structured validation

High Impact
→ deep validation + approval when required
```

---

## Resultados de Validation

Puede producir:

```text
Completed
Needs Correction
Blocked
Waiting for Approval
Failed
```

---

## Estado 10 — Completed

Una solicitud está `Completed` cuando:

- el objetivo fue resuelto;
- el output fue validado suficientemente;
- no existen blockers relevantes;
- las acciones necesarias fueron ejecutadas o entregadas;
- el usuario puede continuar.

---

## Completed no requiere documentación

Una solicitud puede considerarse completada aunque no genere nuevo conocimiento permanente.

Debe evitarse la regla vieja:

```text
Resolver solicitud
+
Documentar obligatoriamente
=
Completed
```

La documentación solo ocurre cuando aporta valor.

---

## Learning Evaluation

Después de completar una solicitud puede evaluarse si existe aprendizaje reutilizable.

```text
Completed
   │
   ▼
Learning Evaluation
   │
   ├── No Candidate → Close
   └── Candidate → Governance process
```

Esto ocurre después del objetivo principal.

No debe impedir marcar la solicitud como `Completed`.

---

## Estado 11 — Failed

Una solicitud puede quedar `Failed` cuando:

- una ejecución crítica falla;
- no existe alternativa válida;
- una dependencia necesaria falla;
- no puede cumplirse el objetivo;
- la validación detecta un error irrecuperable.

---

## Error Recuperable

Un error recuperable no debe marcarar automáticamente la solicitud como Failed.

Debe seguir:

```text
Error
  │
  ▼
Recoverable?
   │
   ├── Sí → Needs Correction / In Progress
   └── No → Failed
```

---

## Estado 12 — Cancelled

Una solicitud puede quedar `Cancelled` cuando:

- el usuario cancela;
- deja de ser necesaria;
- una aprobación es rechazada y no existe alternativa;
- cambia el objetivo;
- el proceso debe detenerse por decisión explícita.

`Cancelled` no significa error.

---

## Estados Terminales

Los estados terminales son:

```text
Completed
Failed
Cancelled
```

Una solicitud cerrada puede reabrirse únicamente cuando exista una nueva necesidad operativa.

---

## Transiciones Principales

```text
Received
   ↓
Understanding
   ↓
Ready
   ↓
In Progress
   ↓
Validation
   ↓
Completed
```

Estados laterales:

```text
Waiting for Dependency
Waiting for Approval
Blocked
Needs Correction
```

Estados terminales alternativos:

```text
Failed
Cancelled
```

---

## Flujo Simple

Una consulta sencilla puede utilizar:

```text
Received
   ↓
Understanding
   ↓
Ready
   ↓
In Progress
   ↓
Completed
```

Puede omitir Validation explícita si la validación ocurre internamente dentro de `In Progress`.

---

## Flujo con Validation

```text
Received
   ↓
Understanding
   ↓
Ready
   ↓
In Progress
   ↓
Validation
   ↓
Completed
```

---

## Flujo con Correction

```text
Received
   ↓
Understanding
   ↓
Ready
   ↓
In Progress
   ↓
Validation
   ↓
Needs Correction
   ↓
In Progress
   ↓
Validation
   ↓
Completed
```

---

## Flujo con Dependency

```text
Received
   ↓
Understanding
   ↓
Ready
   ↓
In Progress
   ↓
Waiting for Dependency
   ↓
In Progress
   ↓
Validation
   ↓
Completed
```

---

## Flujo con Approval

```text
Received
   ↓
Understanding
   ↓
Ready
   ↓
In Progress
   ↓
Waiting for Approval
   ↓
Approved
   ↓
In Progress
   ↓
Validation
   ↓
Completed
```

---

## Flujo Bloqueado

```text
Received
   ↓
Understanding
   ↓
Blocked
   ↓
Blocker resolved
   ↓
Ready
   ↓
In Progress
```

---

## Flujo Fallido

```text
In Progress
   ↓
Critical Error
   ↓
Recovery Attempt
   ↓
Failed
```

solo cuando no existe una vía segura de recuperación.

---

## Solicitudes Simples

Las solicitudes simples no necesitan:

- planificación formal;
- Orchestrator;
- múltiples Agents;
- Research;
- documentación;
- lifecycle completo visible.

Ejemplo:

```text
"Corregime este texto."
```

Puede resolverse de forma directa y proporcional.

---

## Solicitudes Complejas

Una solicitud compleja puede utilizar:

```text
Received
   ↓
Understanding
   ↓
Ready
   ↓
Orchestration
   ↓
Multiple Tasks
   ↓
In Progress
   ↓
Dependencies
   ↓
Validation
   ↓
Completed
```

---

## Solicitudes con acciones externas

Cuando existe una acción externa:

```text
In Progress
    │
    ▼
Proposed Action
    │
    ▼
Risk / Permissions
    │
    ├── Authorized
    │      │
    │      ▼
    │  Execute
    │
    └── Approval Required
           │
           ▼
      Waiting for Approval
```

---

## Request Lifecycle y Data Flow

`DATA_FLOW.md` define qué información circula.

Request Lifecycle define el estado actual de la solicitud.

```text
Data Flow
→ información

Request Lifecycle
→ estado
```

Ejemplo:

```text
State:
Waiting for Dependency

Data:
missing Research result
```

---

## Request Lifecycle y Orchestrator

El Orchestrator puede:

- crear subtareas;
- coordinar estados;
- detectar bloqueos;
- identificar dependencias;
- solicitar aprobación;
- integrar resultados.

Request Lifecycle define los estados.

Orchestrator coordina el trabajo que produce transiciones.

---

## Request Lifecycle y Agent Interaction

Agents pueden modificar el estado de sus tareas.

Ejemplo:

```text
Agent A
status: Completed

Agent B
status: Waiting for Dependency
```

El estado global puede permanecer:

```text
In Progress
```

hasta completar todas las dependencias críticas.

---

## Request Lifecycle y Decision Framework

Decision Framework puede determinar:

- ejecutar;
- validar;
- solicitar aprobación;
- detener.

Estas decisiones pueden producir transiciones como:

```text
In Progress
→ Waiting for Approval

In Progress
→ Validation

In Progress
→ Blocked
```

---

## Request Lifecycle y AI Behavior

AI Behavior establece principios generales como:

- proporcionalidad;
- evitar preguntas innecesarias;
- control de riesgo;
- validación;
- autonomía.

Request Lifecycle representa estos principios mediante estados.

---

## Request Lifecycle y Documentation Standards

Los estados de solicitud no deben utilizarse como `status` documental.

Ejemplo incorrecto:

```yaml
status: In Progress
```

en Front Matter de un documento.

El Front Matter utiliza estados documentales:

```yaml
status: Draft
```

---

## Request Lifecycle y Automations

Una Automation puede generar transiciones.

Ejemplo:

```text
Automation started
→ In Progress

Waiting external API
→ Waiting for Dependency

Automation successful
→ Validation

Automation failed
→ Needs Correction / Failed
```

---

## Request Lifecycle e Integrations

Una Integration puede producir:

```text
Success
Failure
Pending
Unauthorized
```

Estos resultados deben mapearse al lifecycle.

Ejemplo:

```text
Unauthorized
→ Blocked

Pending
→ Waiting for Dependency

Success
→ In Progress / Validation

Failure recoverable
→ Needs Correction
```

---

## Reanudación

Una solicitud puede reanudarse cuando desaparece un bloqueo o dependencia.

Ejemplo:

```text
Waiting for Approval
      ↓
Approved
      ↓
In Progress
```

El sistema debe conservar contexto suficiente para continuar sin reconstrucción innecesaria.

---

## Persistencia de Estado

No toda solicitud necesita persistir su estado externamente.

La persistencia puede ser útil cuando:

- dura múltiples sesiones;
- tiene varios Agents;
- depende de aprobaciones;
- incluye Automations;
- necesita trazabilidad;
- tiene alto impacto.

---

## Estado Interno vs Estado Visible

Trinity AI puede mantener un estado interno más detallado que el mostrado al usuario.

Debe comunicar estado cuando sea útil.

Ejemplo:

```text
Interno:
Waiting for Dependency

Usuario:
"Estoy esperando el archivo necesario para continuar."
```

---

## Trazabilidad

Cuando el impacto lo justifique puede registrarse:

```yaml
request_id:
status:
previous_status:
timestamp:
responsible:
reason:
next_action:
```

No toda solicitud necesita historial completo.

---

## Timeouts

Una solicitud no debe quedar indefinidamente en un estado de espera sin contexto.

Cuando corresponda, puede existir una política de timeout para:

- Waiting for Dependency;
- Waiting for Approval;
- Blocked.

Las reglas concretas de timeout deben definirse por el proceso o Automation correspondiente.

---

## Reintentos

Un fallo recuperable puede admitir reintento.

Debe evitarse:

```text
Failure
↓
Retry infinito
↓
Retry infinito
```

Debe existir un límite razonable según contexto.

Después debe:

- escalar;
- bloquear;
- fallar;
- buscar alternativa.

---

## Idempotencia

Cuando una acción pueda reintentarse debe evaluarse si repetirla produce duplicación o efectos externos.

Ejemplo:

```text
Enviar mensaje
```

no debe reintentarse ciegamente si no se sabe si el primer intento se completó.

---

## Reversibilidad

Si una acción realizada durante el lifecycle necesita revertirse, debe evaluarse según Decision Framework.

Puede producir:

```text
Needs Correction
```

o:

```text
Blocked
```

según el caso.

---

## Learning Candidate

Un aprendizaje detectado al finalizar no modifica el estado operativo de la solicitud.

Ejemplo:

```text
Request:
Completed

Learning:
Candidate
```

Son objetos diferentes.

---

## Cierre

Una solicitud puede cerrarse cuando alcanza:

```text
Completed
Failed
Cancelled
```

Debe conservarse únicamente la información necesaria según Governance, Client Context o trazabilidad.

---

## Reapertura

Una solicitud cerrada puede generar una nueva solicitud relacionada.

No debe modificarse silenciosamente el historial del lifecycle anterior.

Ejemplo:

```text
Request A
Completed
   │
   ▼
New Requirement
   │
   ▼
Request B
Received
```

---

## Antipatrones

Trinity AI no debe:

- obligar todas las solicitudes a recorrer todas las etapas;
- bloquear respuestas simples con procesos innecesarios;
- confundir `Draft` con `In Progress`;
- confundir `Approved` con aprobación de acciones;
- documentar obligatoriamente cada solicitud;
- considerar aprendizaje como requisito para completar;
- tratar Waiting for Dependency como Failed;
- interpretar silencio como aprobación;
- marcar Completed antes de validar una acción sensible;
- reiniciar todo el lifecycle por un error local;
- mantener loops de corrección infinitos;
- ocultar estados bloqueados;
- confundir subtareas con estado global;
- persistir todo sin necesidad.

---

## Criterios de Éxito

Request Lifecycle funciona correctamente cuando:

- una solicitud siempre tiene un estado comprensible;
- las solicitudes simples mantienen un flujo simple;
- los bloqueos son visibles;
- las aprobaciones son explícitas;
- las dependencias pueden esperarse sin marcar fallo;
- las correcciones pueden reingresar al flujo;
- Validation puede devolver trabajo;
- Completed representa objetivo resuelto;
- Failed representa fallo real;
- Cancelled representa cierre deliberado;
- estados operativos y documentales permanecen separados;
- el lifecycle puede adaptarse a diferentes tipos de trabajo.

---

## Checklist de Lifecycle

Cuando sea necesario debe poder responderse:

```text
¿Cuál es el estado actual?
        ↓
¿Qué falta para avanzar?
        ↓
¿Existe una dependencia?
        ↓
¿Existe un bloqueo?
        ↓
¿Necesita aprobación?
        ↓
¿Existe trabajo activo?
        ↓
¿Necesita validación?
        ↓
¿Necesita corrección?
        ↓
¿Puede considerarse completada?
```

No todas las solicitudes necesitan registrar explícitamente este checklist.

---

## Regla de Oro

El Request Lifecycle debe representar el estado real del trabajo sin convertir cada solicitud en un proceso rígido.

```text
Estado correcto
      +
Transición clara
      +
Bloqueos visibles
      +
Aprobación explícita
      +
Validación proporcional
      =
Lifecycle confiable
```

Una solicitud simple debe poder terminar rápido.

Una solicitud compleja debe poder mostrar exactamente dónde está y qué necesita para avanzar.