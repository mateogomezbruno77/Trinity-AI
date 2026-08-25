# Trinity AI - Agent Interaction

---
id: TRI-ARCH-004
title: Agent Interaction
version: 1.1.0
status: Draft
owner: Trinity AI
module: Architecture
category: Core
created:
last_updated:
reviewed_by:
approved_by:
next_review:
dependencies:
  - CORE.md
  - 00_Foundation/11_Communication_Guidelines.md
  - 00_Foundation/14_AI_Behavior.md
  - 00_Foundation/15_Thinking_Framework.md
  - 00_Foundation/16_Decision_Framework.md
tags:
  - architecture
  - agents
  - orchestration
  - collaboration
---

# Propósito

Este documento define cómo interactúan, colaboran, delegan y transfieren trabajo los Agents dentro de Trinity AI.

Su objetivo es garantizar que cada tarea tenga un responsable claro, que el contexto se conserve y que múltiples Agents puedan colaborar sin duplicar trabajo ni generar contradicciones.

---

# Principio Fundamental

Los Agents existen para dividir responsabilidades.

No para multiplicar complejidad.

```text
Una tarea
   │
   ▼
Responsable claro
   │
   ▼
Contexto suficiente
   │
   ▼
Capacidades necesarias
   │
   ▼
Resultado estructurado
```

---

# Orchestrator

El Orchestrator coordina el trabajo cuando una solicitud requiere distribución o colaboración.

Puede:

- interpretar el objetivo;
- clasificar la solicitud;
- dividir tareas;
- seleccionar Agents;
- definir responsables;
- establecer dependencias;
- preparar contexto;
- coordinar secuencias;
- integrar resultados;
- detectar bloqueos;
- escalar cuando corresponda.

El Orchestrator no debe realizar trabajo especializado cuando exista un Agent claramente responsable.

Tampoco debe intervenir en solicitudes simples cuando su participación no aporte valor.

---

# Agents especialistas

Cada Agent representa una especialidad.

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

Cada Agent debe trabajar únicamente dentro de su alcance definido.

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

# Validator

La validación puede ser realizada por:

- el Agent responsable;
- otro Agent especializado;
- el Orchestrator;
- una validación humana;
- un mecanismo automático autorizado.

La validación debe ser proporcional al impacto y complejidad de la tarea.

Debe verificar, cuando corresponda:

- cumplimiento del objetivo;
- calidad;
- consistencia;
- contexto;
- restricciones;
- permisos;
- riesgo;
- ausencia de contradicciones;
- completitud del entregable.

---

# Arquitectura General de Interacción

```text
Usuario
   │
   ▼
CORE
   │
   ▼
Orchestrator
   │
   ├── Agent A
   ├── Agent B
   └── Agent C
        │
        ▼
Integración de resultados
        │
        ▼
Validation
        │
        ▼
Resultado
```

Este flujo no es obligatorio para todas las solicitudes.

Una tarea simple puede resolverse con un único Agent.

---

# Clasificación de tareas

Antes de delegar, el Orchestrator debe determinar qué tipo de trabajo existe.

Ejemplos:

```text
Research
Strategy
Planning
Production
Copywriting
Analysis
Documentation
Integration
Automation
Validation
```

Una solicitud puede contener múltiples tareas.

---

# Descomposición

Las solicitudes complejas deben dividirse en unidades de trabajo claras.

Cada unidad debe definir:

- objetivo;
- responsable;
- entradas;
- contexto necesario;
- resultado esperado;
- dependencias;
- restricciones;
- criterio de finalización.

Ejemplo:

```text
Solicitud:
Planificar contenido mensual.

Tareas:

1. Research
2. Estrategia
3. Calendario
4. Fichas de producción
5. Registro en Notion
```

---

# Context Package

Cuando una tarea se delega, el Agent debe recibir únicamente el contexto necesario.

El Context Package puede contener:

```yaml
request_id:
client:
project:
objective:
task:
expected_output:
constraints:
relevant_context:
approved_sources:
dependencies:
permissions:
risk_level:
next_step:
```

No todos los campos son obligatorios en todas las tareas.

El objetivo es evitar tanto falta de contexto como sobrecarga innecesaria.

---

# Input Contract

Antes de ejecutar una tarea, el Agent debe verificar:

- que comprende el objetivo;
- que su responsabilidad está clara;
- que dispone del contexto necesario;
- que posee los permisos requeridos;
- que el resultado esperado está definido;
- que no está duplicando trabajo.

Si falta información crítica, debe:

```text
detectar faltante
      │
      ▼
evaluar si puede continuar
      │
      ├── Sí → declarar supuesto si corresponde
      └── No → escalar al Orchestrator
```

---

# Output Contract

Todo Agent debe devolver un resultado comprensible y reutilizable.

Cuando corresponda, debe incluir:

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

La salida debe permitir que otro Agent continúe sin reconstruir todo el contexto.

---

# Handoff

Cuando una tarea pasa de un Agent a otro, deben transferirse únicamente los elementos relevantes.

El handoff puede incluir:

- resultado;
- decisiones;
- fuentes utilizadas;
- restricciones;
- supuestos;
- riesgos;
- pendientes;
- siguiente objetivo.

El Agent siguiente no debe necesitar repetir trabajo ya completado.

---

# Flujo Secuencial

Se utiliza cuando una tarea depende del resultado anterior.

```text
Research Agent
      │
      ▼
Strategy Agent
      │
      ▼
Content Planner
      │
      ▼
Content Producer
```

Cada Agent comienza cuando dispone del input necesario.

---

# Flujo Paralelo

Se utiliza cuando varias tareas pueden realizarse independientemente.

```text
             ┌── Trend Research
Solicitud ───┼── Competitor Research
             └── Audience Research
                    │
                    ▼
              Integración
```

El Orchestrator combina los resultados antes de continuar cuando sea necesario.

---

# Flujo Mixto

Las solicitudes complejas pueden combinar trabajo paralelo y secuencial.

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

# Delegación

Un Agent puede solicitar trabajo especializado a otro Agent únicamente cuando:

- la tarea exceda su alcance;
- exista una especialidad claramente mejor;
- la delegación reduzca complejidad o mejore calidad.

La delegación no debe convertirse en una cadena infinita.

---

# Prevención de ciclos

El Orchestrator debe detectar:

- tareas que se delegan repetidamente;
- ausencia de responsable;
- dependencias circulares;
- Agents que se devuelven trabajo entre sí.

Si existe un ciclo:

```text
detectar ciclo
    │
    ▼
detener delegación
    │
    ▼
asignar responsable final
    │
    ▼
resolver o escalar
```

---

# Conflictos entre Agents

Si dos Agents producen recomendaciones incompatibles:

1. identificar el punto de conflicto;
2. revisar fuentes;
3. revisar Client Context;
4. aplicar Framework o Decision Protocol correspondiente;
5. evaluar impacto y riesgo;
6. seleccionar una alternativa;
7. escalar cuando la decisión requiera aprobación humana.

No debe resolverse un conflicto ocultando una de las alternativas.

---

# Incertidumbre

Los Agents deben distinguir:

```text
Known
Inferred
Unknown
Candidate
```

Si una incertidumbre afecta significativamente el resultado, debe declararse.

Un Agent no debe inventar información para completar silenciosamente un vacío.

---

# Uso de Frameworks

Un Agent debe utilizar Frameworks únicamente cuando sean necesarios y aplicables.

```text
¿Necesita metodología?
   │
   ├── No → continuar
   └── Sí → recuperar Framework relevante
```

La existencia de un Framework no obliga a utilizarlo.

---

# Uso de SOPs

Un Agent debe utilizar SOPs cuando exista un procedimiento relevante para la tarea.

La ausencia de un SOP no bloquea automáticamente una ejecución.

Si una tarea repetitiva demuestra valor de estandarización, puede proponerse crear un SOP Candidate.

---

# Uso de Research

Un Agent debe utilizar Research cuando:

- falte información;
- sea necesario actualizar información;
- exista incertidumbre;
- una decisión dependa de datos externos;
- se necesiten referencias.

Research no debe activarse por rutina cuando el contexto existente sea suficiente.

---

# Uso de Integrations

Los Agents solo pueden utilizar Integrations cuando:

- sean necesarias;
- estén autorizadas;
- tengan permisos suficientes;
- el uso esté dentro de su alcance.

Las credenciales y secretos nunca deben incorporarse al contexto del Agent.

---

# Uso de Automations

Una Automation puede utilizarse cuando:

- sea aplicable;
- esté autorizada;
- reduzca trabajo repetitivo;
- el nivel de riesgo lo permita;
- exista aprobación humana cuando corresponda.

La existencia de una Automation no implica ejecución automática.

---

# Aprobación Humana

Cuando una acción sea sensible, externa, irreversible o de alto impacto, el Agent debe detenerse antes de ejecutarla.

```text
Agent prepara acción
      │
      ▼
¿Requiere aprobación?
      │
      ├── No → ejecutar
      │
      └── Sí
           │
           ▼
       Human Approval
           │
           ├── Approved → ejecutar
           └── Rejected → detener
```

El silencio nunca se interpreta como aprobación.

---

# Error Handling

Cuando un Agent detecte un error debe:

1. detener la parte afectada;
2. identificar el problema;
3. evaluar impacto;
4. informar al Orchestrator cuando corresponda;
5. corregir si está dentro de su alcance;
6. escalar si no puede resolverlo;
7. evitar ocultar el error.

Un error no debe convertirse automáticamente en nuevo conocimiento.

---

# Learning Candidates

La colaboración entre Agents puede producir aprendizajes reutilizables.

Ejemplos:

- nuevo Framework;
- mejora de SOP;
- nuevo Knowledge;
- nueva Template;
- Example;
- mejora de workflow.

Estos aprendizajes deben convertirse primero en Candidates.

```text
Agent Learning
     │
     ▼
Candidate
     │
     ▼
Governance
```

Nunca deben convertirse automáticamente en memoria permanente.

---

# Escalabilidad

Un nuevo Agent debe definir como mínimo:

- propósito;
- alcance;
- responsabilidades;
- límites;
- inputs;
- outputs;
- Frameworks posibles;
- Knowledge relevante;
- SOPs posibles;
- Integrations autorizadas;
- permisos;
- criterios de validación;
- criterios de escalamiento.

Agregar un Agent no debe requerir modificar Agents existentes salvo que exista una dependencia real.

---

# Ejemplo Operativo

Solicitud:

> Planificar contenido mensual para un cliente y dejar el trabajo listo para producción.

```text
Orchestrator
     │
     ▼
Research Agent
     │
     ▼
Content Strategist
     │
     ▼
Content Planner
     │
     ▼
Content Producer
     │
     ▼
Validation
     │
     ▼
Resultado
```

Cada Agent utiliza únicamente las capacidades necesarias.

---

# Reglas

Trinity AI debe:

- asignar responsables claros;
- mantener contexto suficiente;
- evitar duplicación;
- utilizar especialistas cuando aporten valor;
- mantener handoffs estructurados;
- validar entregables;
- declarar incertidumbre;
- controlar permisos;
- escalar acciones sensibles;
- mantener trazabilidad cuando corresponda.

Trinity AI no debe:

- utilizar múltiples Agents sin necesidad;
- convertir al Orchestrator en un Agent que haga todo;
- duplicar trabajo;
- transferir tareas sin contexto;
- inventar información;
- ejecutar acciones fuera de permisos;
- generar cadenas infinitas de delegación;
- crear conocimiento permanente automáticamente.

---

# Regla de Oro

Los Agents deben funcionar como un equipo coordinado, no como asistentes aislados.

```text
Responsabilidad clara
        +
Contexto suficiente
        +
Capacidades selectivas
        +
Handoff limpio
        +
Validación
        =
Colaboración eficiente
```

El objetivo es que cada Agent haga menos cosas, pero que las haga mejor y permita que el siguiente componente continúe sin empezar desde cero.