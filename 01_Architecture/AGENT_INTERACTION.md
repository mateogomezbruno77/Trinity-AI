---
id: TRI-ARCH-004
title: Agent Interaction
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
  - 00_Foundation/11_Communication_Guidelines.md
  - 00_Foundation/14_AI_Behavior.md
  - 00_Foundation/15_Thinking_Framework.md
  - 00_Foundation/16_Decision_Framework.md
tags:
  - architecture
  - agents
  - collaboration
  - handoff
  - delegation
  - coordination
---

# Trinity AI - Agent Interaction

## Propósito

Este documento define cómo interactúan, colaboran, delegan y transfieren trabajo los Agents dentro de Trinity AI.

Su objetivo es garantizar que:

- cada tarea tenga un responsable claro;
- el contexto necesario se conserve;
- los Agents trabajen dentro de su especialidad;
- los handoffs sean estructurados;
- no exista duplicación innecesaria;
- los conflictos sean visibles;
- las dependencias se respeten;
- múltiples Agents puedan colaborar sin convertirse en sistemas aislados.

Agent Interaction define reglas de colaboración.

No define cómo funciona todo el Orchestrator.

No define el comportamiento general de Trinity AI.

No define procedimientos específicos de negocio.

---

## Objetivo

La interacción entre Agents debe permitir:

```text
Especialización
      +
Responsabilidad clara
      +
Contexto suficiente
      +
Handoffs limpios
      +
Coordinación proporcional
      =
Colaboración eficiente
```

La colaboración debe reducir trabajo.

No agregar capas innecesarias.

---

## Principio Fundamental

> Un Agent debe realizar únicamente el trabajo para el cual tiene responsabilidad y entregar un resultado que permita continuar sin reconstruir contexto innecesariamente.

Los Agents existen para dividir responsabilidades.

No para multiplicar complejidad.

---

## Principio de Especialización

Cada Agent representa una capacidad especializada.

Ejemplos:

- Research Agent;
- Content Strategist;
- Content Planner;
- Content Producer;
- Copywriter;
- Creative Director;
- Performance Analyst;
- Documentation Agent;
- Integration Agent.

Un Agent no debe absorber responsabilidades pertenecientes a otro cuando exista una especialización clara.

---

## Principio de Mínimo Número de Agents

Más Agents no significa automáticamente mayor calidad.

Debe utilizarse:

```text
Mínimo número de Agents
        +
Especialidades correctas
        =
Mejor coordinación
```

Debe evitarse:

```text
Tarea simple
    │
    ▼
5 Agents
    │
    ▼
6 handoffs
    │
    ▼
Más complejidad que valor
```

---

## Principio de Responsable Claro

Toda tarea debe tener un responsable principal.

Debe evitarse:

```text
Tarea
  │
  ├── Agent A parcialmente
  ├── Agent B parcialmente
  └── nadie responsable del resultado final
```

Debe favorecerse:

```text
Tarea
  │
  ▼
Responsible Agent
  │
  ▼
Resultado
```

Cuando varios Agents colaboren, debe quedar claro quién responde por cada etapa.

---

## Arquitectura General de Interacción

```text
Solicitud
   │
   ▼
CORE
   │
   ▼
¿Requiere especialización?
   │
   ├── No
   │    │
   │    ▼
   │ Respuesta directa
   │
   └── Sí
        │
        ▼
     Agent
        │
        ▼
¿Requiere colaboración?
   │
   ├── No
   │    │
   │    ▼
   │ Resultado
   │
   └── Sí
        │
        ▼
   Coordinación
        │
   ┌────┼────┐
   ▼    ▼    ▼
Agent A B    C
   │    │    │
   └────┼────┘
        ▼
   Integración
        │
        ▼
    Validation
        │
        ▼
     Resultado
```

El Orchestrator puede coordinar este proceso cuando la complejidad lo requiera.

No todas las solicitudes necesitan Orchestrator.

---

## Relación con Orchestrator

`01_Architecture/ORCHESTRATOR.md` define cómo Trinity AI coordina solicitudes complejas.

Agent Interaction define cómo los Agents colaboran una vez que existe interacción entre especialistas.

La relación conceptual es:

```text
Orchestrator
│
└── coordina responsables y dependencias

Agent Interaction
│
└── define reglas de colaboración entre Agents
```

Este documento puede referenciar conceptualmente al Orchestrator sin declararlo como dependencia formal.

Esto evita dependencias circulares innecesarias.

---

## Agents Especialistas

Cada Agent debe poseer como mínimo:

- propósito;
- alcance;
- responsabilidades;
- límites;
- inputs;
- outputs;
- capacidades disponibles;
- permisos;
- criterios de validación;
- criterios de escalamiento.

Un Agent puede utilizar selectivamente:

```text
Agent
  │
  ├── Frameworks
  ├── Knowledge
  ├── SOPs
  ├── Research
  ├── Client Context
  ├── Templates
  ├── Assets
  ├── Integrations
  └── Automations
```

No todas las capacidades deben utilizarse en todas las tareas.

---

## Responsabilidad del Agent

El Agent responsable debe:

- comprender la tarea;
- verificar que esté dentro de su alcance;
- identificar contexto necesario;
- utilizar capacidades relevantes;
- ejecutar trabajo especializado;
- declarar incertidumbre;
- respetar permisos;
- validar su resultado;
- entregar un output utilizable.

---

## Lo que un Agent no debe hacer

Un Agent no debe:

- asumir responsabilidades ajenas sin necesidad;
- duplicar Knowledge;
- copiar Frameworks dentro de su definición;
- reconstruir trabajo ya completado;
- delegar únicamente para reducir su propio trabajo;
- utilizar Integrations fuera de permisos;
- activar Automations solo porque existan;
- inventar contexto;
- convertir aprendizajes automáticamente en memoria permanente.

---

## Clasificación de Tareas

Antes de asignar trabajo puede clasificarse la tarea según especialidad.

Ejemplos:

```text
Research
Strategy
Planning
Production
Copywriting
Creative
Analysis
Documentation
Integration
Automation
Validation
```

Una solicitud puede contener múltiples tipos de trabajo.

La clasificación ayuda a seleccionar responsabilidad.

No obliga a crear un Agent diferente para cada categoría.

---

## Complejidad de Colaboración

La colaboración puede clasificarse como:

```text
Single Agent
Multi-Agent Sequential
Multi-Agent Parallel
Multi-Agent Mixed
```

---

## Single Agent

Debe utilizarse cuando una sola especialidad puede resolver correctamente la tarea.

```text
Solicitud
   │
   ▼
Agent
   │
   ▼
Validation
   │
   ▼
Resultado
```

Debe ser la opción preferida cuando sea suficiente.

---

## Multi-Agent Sequential

Debe utilizarse cuando una tarea depende del output anterior.

```text
Agent A
   │
   ▼
Output A
   │
   ▼
Agent B
   │
   ▼
Output B
```

Ejemplo:

```text
Research Agent
      │
      ▼
Strategy Agent
      │
      ▼
Content Planner
```

---

## Multi-Agent Parallel

Debe utilizarse cuando varias tareas pueden ejecutarse independientemente.

```text
             ┌── Agent A
             │
Solicitud ───┼── Agent B
             │
             └── Agent C
                    │
                    ▼
               Integration
```

La paralelización debe aportar una mejora real.

No debe utilizarse si crea:

- resultados incompatibles;
- dependencias ocultas;
- duplicación;
- pérdida de contexto.

---

## Multi-Agent Mixed

Puede combinar ejecución paralela y secuencial.

```text
          ┌── Research A
Inicio ───┼── Research B
          └── Research C
                 │
                 ▼
              Strategy
                 │
          ┌──────┴──────┐
          ▼             ▼
      Production       Copy
          │             │
          └──────┬──────┘
                 ▼
             Validation
```

---

## Descomposición

Las solicitudes complejas pueden dividirse en unidades de trabajo.

Cada unidad puede definir:

```yaml
task_id:
objective:
responsible_agent:
input:
expected_output:
dependencies:
constraints:
permissions:
risk_level:
```

La descomposición debe aportar claridad.

No debe fragmentar artificialmente trabajo simple.

---

## Regla de Descomposición

Antes de dividir una tarea debe preguntarse:

> ¿Separar esta tarea mejora especialización, coordinación o calidad?

```text
Sí
→ dividir

No
→ mantener unificada
```

---

## Context Package

Cuando una tarea se asigna a un Agent, debe recibir únicamente el contexto necesario.

Puede contener:

```yaml
request_id:
client:
project:
objective:
task:
expected_output:
constraints:
relevant_context:
sources:
dependencies:
permissions:
risk_level:
next_step:
```

No todos los campos son obligatorios.

---

## Principios del Context Package

Debe ser:

- suficiente;
- relevante;
- claro;
- mínimo;
- actualizado;
- seguro.

Debe evitar:

- contexto de otros clientes;
- documentación irrelevante;
- secretos;
- duplicación;
- archivos completos cuando solo se necesita una parte.

---

## Input Contract

Antes de ejecutar una tarea, el Agent debe verificar:

- que comprende el objetivo;
- que su responsabilidad está clara;
- que la tarea está dentro de su alcance;
- que posee contexto suficiente;
- que existen permisos necesarios;
- que comprende el output esperado;
- que las dependencias requeridas están disponibles;
- que no está duplicando trabajo existente.

---

## Input Incompleto

Cuando falte información debe evaluar:

```text
Información faltante
        │
        ▼
¿Es crítica?
    │        │
   No       Sí
    │        │
    ▼        ▼
Continuar  ¿Puede recuperarse?
              │        │
             Sí       No
              │        │
              ▼        ▼
          Recuperar  Escalar
```

No debe preguntar automáticamente si puede recuperar la información por otra vía autorizada.

---

## Supuestos

Un Agent puede utilizar un supuesto cuando:

- sea razonable;
- el impacto sea bajo;
- el riesgo sea limitado;
- no sustituya información crítica.

Debe declararlo cuando pueda afectar materialmente el resultado.

---

## Output Contract

Todo Agent debe producir un resultado comprensible y reutilizable.

Cuando corresponda puede contener:

```yaml
status:
summary:
deliverable:
sources_used:
assumptions:
decisions:
risks:
open_questions:
recommended_next_step:
```

No todos los campos deben aparecer siempre.

---

## Requisitos del Output

El output debe permitir:

- validación;
- integración;
- ejecución;
- handoff;
- entrega.

Debe evitar:

- ambigüedad;
- duplicación;
- información irrelevante;
- razonamiento interno innecesario.

---

## Handoff

Un handoff ocurre cuando el resultado de un Agent se convierte en input de otro.

Debe transferirse únicamente lo necesario.

Puede incluir:

```yaml
task:
result:
sources:
decisions:
constraints:
assumptions:
risks:
pending:
next_objective:
```

---

## Regla de Handoff

El siguiente Agent no debe tener que reconstruir todo lo que ya se hizo.

Debe poder responder:

```text
¿Qué se hizo?
¿Qué se decidió?
¿Qué evidencia se utilizó?
¿Qué falta?
¿Qué debo hacer ahora?
```

---

## Handoff Correcto

```text
Agent A
   │
   ▼
Output estructurado
   │
   ▼
Context Package reducido
   │
   ▼
Agent B
```

---

## Handoff Incorrecto

```text
Agent A
   │
   ▼
Conversación completa
   │
   ▼
Agent B intenta reconstruir contexto
```

Debe evitarse trasladar el historial completo cuando no sea necesario.

---

## Delegación

Un Agent puede identificar que una parte del trabajo necesita otra especialidad.

Debe delegarse cuando:

- la tarea exceda su alcance;
- exista un especialista claramente mejor;
- exista una dependencia legítima;
- la delegación mejore calidad o eficiencia.

---

## Delegación Directa

Cuando la arquitectura permita delegación directa entre Agents, esta debe permanecer dentro del alcance definido.

Si la delegación modifica:

- responsables;
- dependencias;
- permisos;
- riesgo;
- orden de ejecución;

debe informarse al Orchestrator cuando corresponda.

---

## Escalamiento al Orchestrator

Un Agent debe devolver control al Orchestrator cuando:

- la tarea exceda su alcance;
- aparezca una nueva dependencia importante;
- se necesite otro Agent;
- exista conflicto;
- exista bloqueo;
- cambie materialmente el riesgo;
- sea necesario reorganizar el workflow.

---

## Prevención de Delegación Infinita

No debe ocurrir:

```text
Agent A
  ↓
Agent B
  ↓
Agent C
  ↓
Agent A
```

Cuando aparezca un ciclo debe:

1. detenerse;
2. identificar la causa;
3. asignar responsable final;
4. resolver;
5. escalar cuando corresponda.

---

## Dependencias entre Agents

Una dependencia existe cuando un Agent necesita el output de otro para continuar.

Debe declararse cuando sea relevante.

Ejemplo:

```text
Research Agent
      │
      ▼
Research Output
      │
      ▼
Strategy Agent
```

No deben inventarse dependencias únicamente para justificar una arquitectura multi-Agent.

---

## Responsabilidad Final

Cuando varios Agents colaboren debe existir un responsable del resultado integrado.

Puede ser:

- el Orchestrator;
- un Agent principal;
- un Validator especializado;

según la arquitectura de la solicitud.

Debe evitarse una situación donde todos produjeron partes pero nadie responde por la solución final.

---

## Integración de Resultados

Cuando existan múltiples outputs deben integrarse.

La integración puede requerir:

- eliminar duplicación;
- reconciliar terminología;
- resolver conflictos;
- preservar evidencia;
- mantener decisiones;
- conservar restricciones;
- producir una salida única.

Integrar no significa simplemente concatenar outputs.

---

## Conflictos entre Agents

Puede existir conflicto cuando dos Agents producen:

- recomendaciones incompatibles;
- interpretaciones diferentes;
- prioridades distintas;
- resultados contradictorios.

Debe seguirse:

```text
Conflict
   │
   ▼
Identify disagreement
   │
   ▼
Compare sources
   │
   ▼
Review context
   │
   ▼
Decision Framework
   │
   ▼
Resolve / Escalate
```

---

## Resolución de Conflictos

Cuando sea posible resolver el conflicto debe evaluarse:

- autoridad de fuentes;
- Client Context;
- restricciones;
- evidencia;
- objetivo;
- impacto;
- riesgo.

Cuando no pueda resolverse con suficiente confianza debe escalarse.

---

## Decision Framework

Cuando exista una decisión material debe utilizarse conceptualmente:

```text
00_Foundation/16_Decision_Framework.md
```

Los Agents no deben inventar sistemas de decisión paralelos.

---

## Incertidumbre

Los Agents deben distinguir:

```text
Known
Inferred
Unknown
Candidate
```

La incertidumbre debe transferirse en un handoff cuando pueda afectar al siguiente componente.

---

## Known

Información respaldada suficientemente.

---

## Inferred

Conclusión razonable.

Debe identificarse cuando su carácter inferido pueda afectar decisiones posteriores.

---

## Unknown

Información que falta.

Si es crítica debe bloquear o escalar.

---

## Candidate

Aprendizaje potencialmente reutilizable.

No debe transformarse automáticamente en memoria permanente.

---

## Frameworks

Un Agent puede utilizar Frameworks cuando exista necesidad metodológica.

```text
¿Necesita metodología?
        │
   ┌────┴────┐
   │         │
  No        Sí
   │         │
   ▼         ▼
Continue  Framework
```

No debe utilizarse un Framework solo porque esté disponible.

---

## SOPs

Un Agent puede utilizar SOPs cuando exista un procedimiento relevante.

La ausencia de SOP no bloquea automáticamente una tarea.

Si un proceso repetido demuestra valor futuro puede proponerse como Candidate.

---

## Knowledge

Los Agents pueden consultar Knowledge cuando necesiten conocimiento global validado.

No deben copiar Knowledge permanente dentro de su definición.

---

## Research

Research debe utilizarse cuando:

- falta información;
- la información puede haber cambiado;
- existe incertidumbre;
- se necesita evidencia;
- una decisión depende de información externa.

No debe investigarse nuevamente información suficientemente válida.

---

## Client Context

Los Agents pueden consultar Client Context únicamente cuando sea relevante para la tarea.

Debe mantenerse aislamiento entre clientes.

```text
Client A
≠
Client B
```

Información específica no debe viajar a otro cliente salvo que haya sido promovida correctamente a Knowledge global.

---

## Templates

Un Agent puede utilizar Templates cuando el output necesita una estructura reutilizable.

Template define estructura.

No sustituye metodología ni conocimiento.

---

## Assets

Un Agent puede utilizar Assets cuando necesite recursos existentes.

Debe recuperar únicamente los relevantes.

---

## Integrations

Los Agents solo pueden utilizar Integrations cuando:

- sean necesarias;
- estén disponibles;
- estén autorizadas;
- existan permisos suficientes;
- el uso esté dentro del alcance;
- el riesgo sea aceptable.

```text
Integration available
≠
Agent authorized
```

---

## Credenciales

Los Agents nunca deben recibir como contexto normal:

- passwords;
- API keys;
- tokens;
- private keys;
- secrets.

Las credenciales deben gestionarse mediante mecanismos seguros externos.

---

## Automations

Una Automation puede utilizarse cuando:

- sea aplicable;
- esté autorizada;
- el proceso esté suficientemente definido;
- existan dependencias;
- existan permisos;
- el riesgo lo permita;
- exista aprobación cuando corresponda.

La existencia de una Automation no implica ejecución automática.

---

## Acciones Externas

Antes de una acción externa debe evaluarse:

```text
Action
  │
  ▼
Permissions
  │
  ▼
Risk
  │
  ▼
Reversibility
  │
  ▼
Approval
when required
  │
  ▼
Execution
```

---

## Aprobación Humana

Cuando una acción requiera aprobación, el Agent no debe ejecutarla anticipadamente.

Debe detenerse en:

```text
Waiting for Approval
```

Después:

```text
Approved
→ ejecutar dentro del alcance aprobado

Rejected
→ detener
```

El silencio nunca constituye aprobación.

---

## Scope de Aprobación

Una aprobación específica no constituye permiso general.

```text
"Aprobado enviar este reporte"
≠
"Aprobado enviar futuros reportes"
```

---

## Validator

La validación puede realizarla:

- Agent responsable;
- Agent especializado;
- Orchestrator;
- mecanismo automático autorizado;
- humano.

La selección depende de:

- complejidad;
- riesgo;
- impacto;
- especialidad.

---

## Validation Contract

Cuando corresponda debe verificar:

- objetivo;
- completitud;
- consistencia;
- calidad;
- restricciones;
- permisos;
- riesgo;
- fuentes;
- resultado;
- errores;
- pendientes.

---

## Self-Validation

Un Agent debe validar su propio trabajo cuando esto sea suficiente.

No debe activarse otro Agent únicamente para revisar una tarea trivial.

---

## Independent Validation

Puede utilizarse otro Agent cuando:

- exista alto impacto;
- exista especialidad diferente;
- el resultado sea complejo;
- haya riesgo;
- sea necesario reducir sesgo;
- Governance lo exija.

---

## Error Handling

Cuando un Agent detecte un error debe:

1. detener la parte afectada;
2. identificar la causa;
3. evaluar impacto;
4. corregir cuando esté dentro de su alcance;
5. validar;
6. informar al Orchestrator cuando corresponda;
7. escalar cuando no pueda resolverlo.

No debe ocultar el error.

---

## Error en Handoff

Si un Agent detecta que recibió un handoff incompleto o incorrecto debe:

- identificar el problema;
- recuperar información si puede;
- pedir corrección al responsable cuando corresponda;
- escalar si bloquea la ejecución.

No debe reconstruir silenciosamente información crítica mediante suposiciones.

---

## Bloqueos

Un Agent puede quedar bloqueado por:

- falta de información;
- dependencia;
- permiso;
- Integration;
- aprobación;
- contradicción;
- riesgo;
- error.

Debe devolver un estado claro.

```yaml
status: blocked
reason:
required_action:
responsible:
```

---

## Status de Tareas

Estados operativos posibles pueden incluir:

```text
Ready
In Progress
Blocked
Waiting for Dependency
Waiting for Approval
Needs Correction
Completed
Failed
```

Estos estados operativos no deben confundirse con los estados documentales:

```text
Draft
Review
Approved
Deprecated
Archived
```

---

## Learning Candidates

La colaboración puede producir aprendizaje reutilizable.

Ejemplos:

- nueva metodología;
- mejora de SOP;
- nuevo Knowledge;
- Template;
- Example;
- mejora de Automation;
- mejora de workflow.

Debe seguir:

```text
Learning
   │
   ▼
Candidate
   │
   ▼
Review
   │
   ▼
Governance
```

Nunca debe convertirse automáticamente en fuente oficial.

---

## Memoria

Los Agents no deben almacenar automáticamente todo lo aprendido.

Debe distinguirse:

```text
Session Context
Client Context
Research
Knowledge
Candidate
```

La arquitectura completa pertenece a:

```text
01_Architecture/MEMORY_ARCHITECTURE.md
```

---

## Data Flow entre Agents

El intercambio de información debe respetar:

```text
01_Architecture/DATA_FLOW.md
```

Agent Interaction define colaboración.

Data Flow define circulación de información.

---

## Relación con System Architecture

`SYSTEM_ARCHITECTURE.md` define dónde encajan Agents y Orchestrator dentro del sistema.

Agent Interaction define cómo colaboran los Agents.

---

## Relación con Request Lifecycle

`REQUEST_LIFECYCLE.md` define estados generales de una solicitud.

Agent Interaction puede producir cambios de estado como:

- trabajo iniciado;
- dependencia pendiente;
- aprobación pendiente;
- tarea completada;
- fallo.

No debe duplicar el lifecycle completo.

---

## Relación con CORE

CORE determina cuándo existe necesidad de especialización o coordinación.

Agent Interaction define cómo se desarrolla la colaboración.

```text
CORE
  │
  ▼
Need
  │
  ▼
Agent / Coordination
  │
  ▼
Agent Interaction
```

---

## Relación con AI Behavior

Todos los Agents deben respetar:

```text
00_Foundation/14_AI_Behavior.md
```

Agent Interaction no redefine comportamiento global.

---

## Relación con Thinking Framework

Todos los Agents deben utilizar razonamiento proporcional según:

```text
00_Foundation/15_Thinking_Framework.md
```

No deben crear metodologías de razonamiento incompatibles.

---

## Relación con Communication Guidelines

Los Agents deben mantener consistencia de comunicación según:

```text
00_Foundation/11_Communication_Guidelines.md
```

La especialización no debe generar voces contradictorias cuando el output se integra.

---

## Trazabilidad

Cuando la tarea lo requiera puede conservarse:

- Agent responsable;
- tareas;
- inputs;
- outputs;
- fuentes;
- decisiones;
- handoffs;
- riesgos;
- aprobaciones;
- errores;
- resultado.

La trazabilidad debe ser proporcional al impacto.

---

## Escalabilidad

Agregar un Agent nuevo no debe requerir modificar todos los Agents existentes.

Un Agent nuevo debe integrarse mediante:

```text
Clear Responsibility
       +
Input Contract
       +
Output Contract
       +
Capabilities
       +
Permissions
       +
Escalation Rules
```

---

## Creación de Nuevos Agents

Debe proponerse un Agent nuevo únicamente cuando exista:

- especialidad claramente diferenciada;
- responsabilidad reutilizable;
- volumen de trabajo potencial;
- valor operativo;
- bajo solapamiento con Agents existentes.

No debe crearse un Agent nuevo para una tarea puntual.

---

## Antipatrones

Trinity AI no debe:

- utilizar múltiples Agents sin necesidad;
- crear micro-Agents para tareas triviales;
- permitir responsabilidades ambiguas;
- realizar handoffs sin contexto;
- pasar conversaciones completas como handoff por defecto;
- duplicar trabajo;
- permitir ciclos de delegación;
- ocultar conflictos;
- inventar información;
- mezclar Client Context;
- compartir credenciales;
- ejecutar acciones fuera de permisos;
- autoaprobar acciones sensibles;
- convertir Candidates automáticamente en memoria;
- utilizar Validator independiente para cada tarea trivial;
- convertir al Orchestrator en responsable de todo.

---

## Criterios de Éxito

Agent Interaction funciona correctamente cuando:

- cada tarea tiene responsable;
- cada Agent opera dentro de su alcance;
- se utiliza el mínimo número de Agents;
- los handoffs conservan contexto suficiente;
- los outputs son reutilizables;
- no existe duplicación crítica;
- los conflictos son visibles;
- los ciclos se detectan;
- los permisos se respetan;
- las acciones sensibles se escalan;
- los resultados pueden integrarse;
- el siguiente componente puede continuar sin empezar desde cero.

---

## Checklist de Interacción

Cuando varios Agents colaboren debe poder responderse:

```text
¿Quién es responsable?
        ↓
¿Qué necesita hacer?
        ↓
¿Qué contexto necesita?
        ↓
¿Qué output debe producir?
        ↓
¿Depende de otro Agent?
        ↓
¿Puede ejecutarse en paralelo?
        ↓
¿Qué permisos tiene?
        ↓
¿Qué riesgo existe?
        ↓
¿Hay handoff?
        ↓
¿Qué información debe transferirse?
        ↓
¿Quién integra?
        ↓
¿Quién valida?
```

No todos los campos requieren formalización en tareas simples.

---

## Regla de Oro

Los Agents deben funcionar como un equipo especializado y coordinado, no como asistentes independientes que reconstruyen el mismo problema.

```text
Responsabilidad clara
        +
Especialización correcta
        +
Contexto mínimo suficiente
        +
Handoff limpio
        +
Validación proporcional
        =
Colaboración eficiente
```

Si agregar otro Agent genera más coordinación de la que ahorra, probablemente ese Agent no sea necesario para esa tarea.