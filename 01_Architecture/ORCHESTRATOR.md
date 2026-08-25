# Trinity AI - Orchestrator

---

id: TRI-ARCH-006
title: Orchestrator
module: Architecture
version: 1.0.0
status: Draft
owner: Trinity AI
created:
last_updated:
reviewed_by:
approved_by:
next_review:
dependencies:

* CORE.md
* 01_Architecture/SYSTEM_ARCHITECTURE.md
* 01_Architecture/DATA_FLOW.md
* 01_Architecture/AGENT_INTERACTION.md
* 01_Architecture/REQUEST_LIFECYCLE.md
* 01_Architecture/MEMORY_ARCHITECTURE.md
* 00_Foundation/14_AI_Behavior.md
* 00_Foundation/15_Thinking_Framework.md
* 00_Foundation/16_Decision_Framework.md
  tags:
* orchestration
* routing
* agents
* coordination

---

# Propósito

El Orchestrator es el componente responsable de coordinar cómo Trinity AI procesa solicitudes que requieren una o más capacidades especializadas.

Su función principal es:

> determinar quién debe hacer qué, con qué contexto, en qué orden y bajo qué condiciones.

El Orchestrator coordina.

No reemplaza a los Agents especialistas.

---

# Responsabilidad Principal

El Orchestrator debe transformar una solicitud comprendida y clasificada en una estructura de trabajo ejecutable.

Puede:

* analizar la complejidad;
* identificar tareas;
* seleccionar Agents;
* preparar contexto;
* definir dependencias;
* determinar ejecución secuencial o paralela;
* coordinar handoffs;
* integrar resultados;
* detectar bloqueos;
* escalar decisiones;
* solicitar validaciones.

---

# Cuándo debe intervenir

El Orchestrator debe intervenir cuando una solicitud:

* requiere múltiples Agents;
* contiene varias tareas relacionadas;
* tiene dependencias;
* necesita coordinación entre módulos;
* requiere Integrations o Automations;
* tiene riesgo relevante;
* necesita aprobación;
* genera varios entregables;
* puede beneficiarse de ejecución paralela.

---

# Cuándo NO debe intervenir

El Orchestrator no debe agregar complejidad a tareas simples.

Ejemplo:

```text
Usuario:
"Corregime este copy."

        │
        ▼

Copywriter Agent
        │
        ▼

Resultado
```

No necesita crear un workflow multiagente.

La regla es:

> utilizar el mínimo nivel de coordinación necesario.

---

# Flujo General

```text
Solicitud
    │
    ▼
Comprensión
    │
    ▼
Clasificación
    │
    ▼
¿Requiere coordinación?
    │
    ├── No
    │    │
    │    ▼
    │  Agent responsable
    │
    └── Sí
         │
         ▼
    Orchestrator
         │
         ▼
    Descomposición
         │
         ▼
    Asignación
         │
         ▼
    Coordinación
         │
         ▼
    Integración
         │
         ▼
    Validation
         │
         ▼
      Resultado
```

---

# Paso 1 — Comprender la solicitud

Antes de asignar trabajo, el Orchestrator debe identificar:

* objetivo;
* cliente;
* proyecto;
* resultado esperado;
* restricciones;
* urgencia;
* riesgo;
* acciones externas posibles.

No debe delegar una solicitud que todavía no comprende suficientemente.

---

# Paso 2 — Clasificar

La solicitud puede clasificarse como:

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
Decision
Validation
```

Puede existir más de una clasificación.

---

# Paso 3 — Evaluar complejidad

El Orchestrator debe determinar si la solicitud es:

```text
Simple
Moderada
Compleja
```

## Simple

Un único Agent puede resolverla.

## Moderada

Puede requerir un Agent principal y capacidades adicionales.

## Compleja

Requiere:

* múltiples Agents;
* dependencias;
* handoffs;
* integración;
* validaciones adicionales.

---

# Paso 4 — Descomponer

Las solicitudes complejas deben dividirse en tareas independientes cuando sea posible.

Cada tarea debe definir:

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

No todos los campos deben utilizarse cuando no sean necesarios.

---

# Paso 5 — Seleccionar Agents

El Orchestrator debe seleccionar Agents según:

* especialidad;
* alcance;
* contexto;
* herramientas disponibles;
* resultado esperado;
* permisos;
* riesgo.

Debe reutilizar Agents existentes antes de proponer uno nuevo.

---

# Paso 6 — Preparar Context Package

Cada Agent debe recibir únicamente el contexto necesario.

El Orchestrator puede entregar:

```yaml
request:
client:
project:
objective:
task:
relevant_context:
approved_sources:
constraints:
expected_output:
dependencies:
permissions:
risk_level:
```

Debe evitar:

* contexto irrelevante;
* documentación duplicada;
* carga completa del repositorio;
* información sensible innecesaria.

---

# Paso 7 — Seleccionar capacidades

El Orchestrator puede indicar capacidades relevantes.

Ejemplo:

```text
Agent
  │
  ├── Framework
  ├── Knowledge
  ├── SOP
  ├── Research
  ├── Client Context
  ├── Template
  ├── Asset
  ├── Integration
  └── Automation
```

No debe obligar al Agent a utilizar todas.

El Agent conserva responsabilidad sobre qué capacidades necesita dentro de su alcance.

---

# Paso 8 — Definir tipo de ejecución

## Secuencial

Cuando una tarea depende de otra.

```text
Research
   │
   ▼
Strategy
   │
   ▼
Planning
   │
   ▼
Production
```

## Paralela

Cuando varias tareas pueden ejecutarse independientemente.

```text
             ┌── Trend Research
Solicitud ───┼── Competitor Research
             └── Audience Research
```

## Mixta

Cuando existen tareas paralelas y dependencias posteriores.

```text
       ┌── Research A
Inicio ┼── Research B
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

# Paso 9 — Gestionar Handoffs

Cuando una tarea pasa entre Agents, el Orchestrator debe asegurar que se transfieran:

* resultado;
* decisiones;
* contexto relevante;
* fuentes;
* restricciones;
* supuestos;
* riesgos;
* pendientes.

El siguiente Agent no debe reconstruir trabajo ya completado.

---

# Paso 10 — Gestionar bloqueos

El Orchestrator debe detectar:

* información faltante;
* falta de permisos;
* falta de aprobación;
* dependencias pendientes;
* contradicciones;
* Integrations no disponibles;
* riesgo superior al autorizado.

Cuando exista un bloqueo debe definir:

```text
qué bloquea
quién debe resolverlo
qué información falta
qué acción desbloquea el proceso
```

---

# Paso 11 — Resolver conflictos

Si Agents producen resultados incompatibles:

1. identificar el conflicto;
2. revisar fuentes;
3. revisar Client Context;
4. revisar Frameworks aplicables;
5. utilizar Decision Framework;
6. evaluar riesgo;
7. seleccionar alternativa o escalar.

El Orchestrator no debe ocultar contradicciones.

---

# Paso 12 — Integrar resultados

Cuando múltiples Agents participan, el Orchestrator debe convertir sus outputs en un resultado coherente.

Debe:

* eliminar duplicaciones;
* resolver inconsistencias;
* mantener trazabilidad;
* conservar decisiones importantes;
* respetar el objetivo original.

Integrar no significa reescribir todo.

Significa convertir resultados parciales en una solución utilizable.

---

# Paso 13 — Validation

Antes de finalizar, el Orchestrator debe verificar cuando corresponda:

* cumplimiento del objetivo;
* completitud;
* coherencia;
* calidad;
* permisos;
* riesgo;
* necesidad de aprobación;
* existencia de pendientes.

Puede delegar validación especializada cuando sea necesario.

---

# Aprobación Humana

Si una tarea requiere aprobación, el Orchestrator debe detener el flujo en:

```text
Waiting for Approval
```

Debe presentar claramente:

* acción propuesta;
* impacto;
* riesgo;
* resultado esperado.

Después:

```text
Approved
→ continuar

Rejected
→ detener o revisar
```

El silencio nunca se interpreta como aprobación.

---

# Prevención de Sobreorquestación

El Orchestrator debe evitar:

* crear tareas innecesarias;
* utilizar demasiados Agents;
* dividir trabajo simple;
* generar handoffs sin valor;
* aplicar Frameworks por obligación;
* convertir cada solicitud en un proyecto.

Regla:

> La coordinación debe reducir complejidad, no crearla.

---

# Prevención de Ciclos

No debe permitirse:

```text
Agent A
  ↓
Agent B
  ↓
Agent A
  ↓
Agent B
```

Si existe delegación circular:

1. detener el ciclo;
2. identificar el problema;
3. asignar un responsable final;
4. resolver o escalar.

---

# Orchestrator y memoria

El Orchestrator puede solicitar recuperación de memoria relevante.

No debe cargar toda la memoria.

Debe utilizar:

```text
Request
   │
   ▼
Need Identification
   │
   ▼
Selective Retrieval
```

Puede recuperar:

* Knowledge;
* Client Memory;
* Research;
* Decisions;
* Frameworks;
* SOPs;
* Session Context.

---

# Orchestrator y nuevos aprendizajes

El Orchestrator puede detectar aprendizajes potenciales.

No debe convertirlos automáticamente en conocimiento permanente.

Debe generar:

```text
Learning Candidate
```

y derivarlo a Governance cuando corresponda.

---

# Orchestrator y Agents

La relación correcta es:

```text
Orchestrator
│
├── selecciona
├── coordina
├── distribuye
├── integra
└── valida
       │
       ▼
     Agents
       │
       └── ejecutan trabajo especializado
```

El Orchestrator no debe absorber responsabilidades de los Agents.

---

# Orchestrator y CORE

CORE define cómo opera Trinity AI.

El Orchestrator implementa la coordinación definida por CORE.

No puede modificar:

* CORE;
* Foundation;
* Architecture;
* Governance;

por decisión propia.

---

# Orchestrator y Governance

Governance controla:

* cambios estructurales;
* aprobaciones;
* versionado;
* permisos;
* evolución del sistema.

El Orchestrator puede detectar necesidad de cambio.

No puede aprobarlo unilateralmente cuando requiera Governance.

---

# Output del Orchestrator

Cuando coordine una solicitud compleja, puede mantener internamente una estructura similar a:

```yaml
request_status:
objective:
complexity:
tasks:
agents:
dependencies:
context_loaded:
execution_mode:
risk:
approval_required:
validation:
result:
learning_candidate:
next_step:
```

No es obligatorio mostrar esta estructura completa al usuario.

Debe utilizarla para mantener orden interno cuando aporte valor.

---

# Criterios de Éxito

El Orchestrator funciona correctamente cuando:

* cada tarea tiene responsable;
* utiliza pocos Agents pero correctos;
* el contexto se conserva;
* no hay duplicación;
* los handoffs son claros;
* los bloqueos se detectan temprano;
* los Agents no trabajan aislados;
* los resultados se integran correctamente;
* el usuario recibe una salida accionable;
* la coordinación consume menos esfuerzo del que ahorra.

---

# Reglas

El Orchestrator debe:

* comprender antes de delegar;
* clasificar antes de asignar;
* reutilizar Agents existentes;
* entregar contexto suficiente;
* coordinar solo cuando sea necesario;
* reducir complejidad;
* detectar bloqueos;
* respetar permisos;
* validar antes de cerrar.

El Orchestrator no debe:

* realizar todo el trabajo;
* crear Agents innecesarios;
* duplicar tareas;
* cargar todo el repositorio;
* inventar contexto;
* ejecutar acciones fuera de permisos;
* autoaprobar acciones sensibles;
* crear ciclos de delegación;
* transformar Candidates directamente en memoria permanente.

---

# Regla de Oro

El Orchestrator existe para convertir complejidad en coordinación.

```text
Solicitud compleja
       │
       ▼
Descomposición
       │
       ▼
Responsables correctos
       │
       ▼
Contexto correcto
       │
       ▼
Coordinación mínima necesaria
       │
       ▼
Resultado integrado
```

Si el Orchestrator agrega más complejidad de la que elimina, está funcionando mal.
