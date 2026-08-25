---
id: TRI-ARCH-006
title: Orchestrator
module: Architecture
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
  - 01_Architecture/SYSTEM_ARCHITECTURE.md
  - 01_Architecture/DATA_FLOW.md
  - 01_Architecture/AGENT_INTERACTION.md
  - 01_Architecture/REQUEST_LIFECYCLE.md
  - 01_Architecture/MEMORY_ARCHITECTURE.md
  - 00_Foundation/14_AI_Behavior.md
  - 00_Foundation/15_Thinking_Framework.md
  - 00_Foundation/16_Decision_Framework.md
tags:
  - orchestration
  - routing
  - agents
  - coordination
---

# Trinity AI - Orchestrator

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

- analizar la complejidad;
- identificar tareas;
- seleccionar Agents;
- preparar contexto;
- definir dependencias;
- determinar ejecución secuencial o paralela;
- coordinar handoffs;
- integrar resultados;
- detectar bloqueos;
- escalar decisiones;
- solicitar validaciones.

---

# Cuándo debe intervenir

El Orchestrator debe intervenir cuando una solicitud:

- requiere múltiples Agents;
- contiene varias tareas relacionadas;
- tiene dependencias;
- necesita coordinación entre módulos;
- requiere Integrations o Automations;
- tiene riesgo relevante;
- necesita aprobación;
- genera varios entregables;
- puede beneficiarse de ejecución paralela.

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

- objetivo;
- cliente;
- proyecto;
- resultado esperado;
- restricciones;
- urgencia;
- riesgo;
- acciones externas posibles.

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

La clasificación sirve para orientar el routing.

No obliga automáticamente a utilizar un Agent específico.

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

Puede requerir:

- múltiples Agents;
- dependencias;
- handoffs;
- integración;
- validaciones adicionales.

La complejidad debe evaluarse proporcionalmente.

Una tarea no debe clasificarse como compleja únicamente porque utilice varias fuentes o capacidades.

---

# Paso 4 — Descomponer

Las solicitudes complejas deben dividirse en tareas independientes cuando esto mejore la ejecución.

Cada tarea puede definir:

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

La descomposición debe reducir complejidad.

No debe fragmentar artificialmente tareas que un único Agent puede resolver correctamente.

---

# Paso 5 — Seleccionar Agents

El Orchestrator debe seleccionar Agents según:

- especialidad;
- alcance;
- contexto;
- capacidades disponibles;
- resultado esperado;
- permisos;
- riesgo.

Debe reutilizar Agents existentes antes de proponer uno nuevo.

La existencia de múltiples Agents compatibles no implica que todos deban intervenir.

Debe seleccionarse el mínimo conjunto suficiente.

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

- contexto irrelevante;
- documentación duplicada;
- carga completa del repositorio;
- información sensible innecesaria.

El Context Package debe respetar las políticas definidas por Memory Architecture y Data Flow.

---

# Paso 7 — Seleccionar capacidades

El Orchestrator puede identificar capacidades potencialmente relevantes.

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

El Orchestrator coordina.

El Agent ejecuta trabajo especializado.

---

# Paso 8 — Definir tipo de ejecución

El Orchestrator debe seleccionar el patrón de ejecución más simple que preserve las dependencias correctas.

## Secuencial

Cuando una tarea depende del resultado de otra.

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

La ejecución paralela debe utilizarse únicamente cuando no introduzca dependencias artificiales, conflictos o pérdida de contexto.

---

# Paso 9 — Gestionar Handoffs

Cuando una tarea pasa entre Agents, el Orchestrator debe asegurar que se transfieran únicamente los elementos relevantes:

- resultado;
- decisiones;
- contexto;
- fuentes;
- restricciones;
- supuestos materiales;
- riesgos;
- pendientes.

El siguiente Agent no debe reconstruir trabajo ya completado.

Un handoff debe permitir continuar el proceso sin cargar nuevamente información innecesaria.

---

# Paso 10 — Gestionar bloqueos

El Orchestrator debe detectar:

- información faltante;
- falta de permisos;
- falta de aprobación;
- dependencias pendientes;
- contradicciones;
- Integrations no disponibles;
- capacidades inexistentes;
- riesgo superior al autorizado.

Cuando exista un bloqueo debe identificar:

```text
qué bloquea
        │
        ▼
quién puede resolverlo
        │
        ▼
qué información o acción falta
        │
        ▼
qué permite continuar
```

No debe continuar silenciosamente cuando el bloqueo pueda comprometer el resultado.

---

# Paso 11 — Resolver conflictos

Si Agents producen resultados incompatibles, el Orchestrator debe:

1. identificar el conflicto;
2. revisar las fuentes relevantes;
3. revisar Client Context;
4. revisar Frameworks aplicables;
5. utilizar Decision Framework cuando exista una decisión material;
6. evaluar riesgo;
7. seleccionar una alternativa o escalar.

El Orchestrator no debe ocultar contradicciones.

Cuando no pueda resolverlas con suficiente confianza, debe escalar.

---

# Paso 12 — Integrar resultados

Cuando múltiples Agents participan, el Orchestrator debe convertir sus outputs en un resultado coherente.

Debe:

- eliminar duplicaciones;
- resolver inconsistencias;
- mantener trazabilidad cuando sea necesaria;
- conservar decisiones importantes;
- respetar el objetivo original;
- preservar información relevante.

Integrar no significa reescribir todo.

Significa convertir resultados parciales en una solución utilizable.

---

# Paso 13 — Validar

Antes de finalizar, el Orchestrator debe verificar proporcionalmente:

- cumplimiento del objetivo;
- completitud;
- coherencia;
- calidad;
- permisos;
- riesgo;
- necesidad de aprobación;
- existencia de pendientes.

Puede delegar validación especializada cuando sea necesario.

La profundidad de validación debe ser proporcional al impacto y riesgo.

---

# Aprobación Humana

Si una tarea requiere aprobación, el Orchestrator debe detener el flujo en:

```text
Waiting for Approval
```

Debe presentar únicamente la información necesaria para decidir:

- acción propuesta;
- motivo;
- impacto relevante;
- riesgo relevante;
- resultado esperado.

Después:

```text
Waiting for Approval
        │
        ├── Approved
        │      │
        │      ▼
        │   Continuar
        │
        └── Rejected
               │
               ▼
          Detener / Revisar
```

El silencio nunca se interpreta como aprobación.

La aprobación se aplica únicamente al alcance explícitamente aprobado.

---

# Prevención de Sobreorquestación

El Orchestrator debe evitar:

- crear tareas innecesarias;
- utilizar demasiados Agents;
- dividir trabajo simple;
- generar handoffs sin valor;
- aplicar Frameworks por obligación;
- convertir cada solicitud en un proyecto;
- introducir coordinación donde un único Agent sea suficiente.

Regla:

> La coordinación debe reducir complejidad, no crearla.

---

# Prevención de Ciclos

No debe permitirse delegación circular sin progreso.

Ejemplo:

```text
Agent A
  │
  ▼
Agent B
  │
  ▼
Agent A
  │
  ▼
Agent B
```

Si existe un ciclo:

1. detener la delegación;
2. identificar la causa;
3. definir un responsable final;
4. resolver el conflicto;
5. escalar cuando corresponda.

---

# Orchestrator y memoria

El Orchestrator puede solicitar recuperación de contexto relevante.

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
   │
   ▼
Relevant Context
```

Puede recuperar, según necesidad:

- Knowledge;
- Client Context;
- Research;
- Decisions;
- Frameworks;
- SOPs;
- Session Context.

La recuperación debe respetar `MEMORY_ARCHITECTURE.md`.

---

# Orchestrator y nuevos aprendizajes

El Orchestrator puede detectar aprendizajes potencialmente reutilizables.

No debe convertirlos automáticamente en conocimiento permanente.

Debe tratarlos como:

```text
Learning
   │
   ▼
Candidate
   │
   ▼
Review / Governance
```

La promoción a fuente oficial pertenece al proceso definido por Governance.

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

Un Agent puede resolver directamente una tarea cuando no exista necesidad real de coordinación.

---

# Orchestrator y Thinking Framework

`00_Foundation/15_Thinking_Framework.md` estructura cómo Trinity AI analiza una solicitud.

El Orchestrator utiliza ese análisis para determinar cómo coordinar el trabajo cuando sea necesario.

```text
Thinking Framework
        │
        ▼
Comprensión
        │
        ▼
¿Necesita coordinación?
        │
   ┌────┴────┐
   │         │
  No        Sí
   │         │
   ▼         ▼
 Agent   Orchestrator
```

Thinking Framework estructura razonamiento.

Orchestrator estructura coordinación.

---

# Orchestrator y Decision Framework

`00_Foundation/16_Decision_Framework.md` define cómo seleccionar entre alternativas.

El Orchestrator debe utilizarlo cuando exista una decisión material, por ejemplo:

- seleccionar entre estrategias de coordinación;
- resolver conflictos entre outputs;
- determinar ejecución o escalamiento;
- decidir entre alternativas con diferente riesgo;
- evaluar acciones sensibles.

El Orchestrator no debe duplicar la lógica completa del Decision Framework.

---

# Orchestrator y CORE

CORE define cómo opera Trinity AI.

El Orchestrator implementa la coordinación definida por CORE cuando una solicitud lo requiere.

No puede modificar por decisión propia:

- CORE;
- Foundation;
- Architecture;
- Governance;
- fuentes oficiales.

Puede detectar una necesidad de cambio y derivarla al proceso correspondiente.

---

# Orchestrator y Governance

Governance controla, según corresponda:

- cambios estructurales;
- aprobaciones;
- versionado;
- permisos;
- evolución del sistema;
- promoción de Candidates.

El Orchestrator puede detectar necesidad de cambio.

No puede aprobar unilateralmente acciones que requieran Governance o aprobación humana.

---

# Orchestrator e Integrations

El Orchestrator puede coordinar el uso de una Integration cuando sea necesaria.

Antes debe verificarse:

- disponibilidad;
- necesidad;
- permisos;
- alcance;
- Agent autorizado;
- riesgo;
- aprobación requerida.

La existencia de una Integration no constituye autorización automática para utilizarla.

---

# Orchestrator y Automations

El Orchestrator puede coordinar una Automation cuando:

- sea aplicable;
- exista un proceso definido;
- las dependencias estén disponibles;
- existan permisos;
- el riesgo sea aceptable;
- la aprobación requerida haya sido obtenida.

El Orchestrator no debe activar una Automation únicamente porque exista.

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

Debe utilizarla únicamente cuando aporte orden, trazabilidad o control.

---

# Criterios de Éxito

El Orchestrator funciona correctamente cuando:

- cada tarea necesaria tiene responsable;
- utiliza pocos Agents pero correctos;
- el contexto relevante se conserva;
- no existe duplicación innecesaria;
- los handoffs son claros;
- los bloqueos se detectan temprano;
- las dependencias se respetan;
- los resultados se integran correctamente;
- los permisos y riesgos están controlados;
- el usuario recibe una salida accionable;
- la coordinación consume menos esfuerzo del que ahorra.

---

# Reglas

El Orchestrator debe:

- comprender antes de delegar;
- clasificar antes de asignar;
- reutilizar Agents existentes;
- entregar contexto suficiente;
- coordinar solo cuando sea necesario;
- reducir complejidad;
- detectar bloqueos;
- respetar dependencias;
- respetar permisos;
- escalar cuando corresponda;
- validar antes de cerrar.

El Orchestrator no debe:

- realizar todo el trabajo;
- crear Agents innecesarios;
- duplicar tareas;
- cargar todo el repositorio;
- inventar contexto;
- ejecutar acciones fuera de permisos;
- autoaprobar acciones sensibles;
- crear ciclos de delegación;
- transformar Candidates directamente en memoria permanente;
- reemplazar Thinking Framework;
- reemplazar Decision Framework;
- reemplazar Governance.

---

# Antipatrones

El Orchestrator debe evitar:

- sobreorquestación;
- microdelegación;
- handoffs innecesarios;
- duplicación de contexto;
- coordinación circular;
- selección excesiva de Agents;
- paralelización sin beneficio;
- integración superficial;
- escalamiento innecesario;
- ejecución sin permisos;
- aprobación implícita;
- ocultamiento de conflictos;
- convertir cada solicitud en un workflow complejo.

---

# Checklist de Orquestación

Cuando una solicitud requiera coordinación, el Orchestrator puede comprobar:

```text
¿Comprendo el objetivo?
        ↓
¿Necesita coordinación?
        ↓
¿Qué tareas existen?
        ↓
¿Qué Agent necesita cada tarea?
        ↓
¿Qué contexto necesita cada Agent?
        ↓
¿Qué dependencias existen?
        ↓
¿Secuencial, paralelo o mixto?
        ↓
¿Qué permisos existen?
        ↓
¿Qué riesgo existe?
        ↓
¿Hay bloqueos?
        ↓
¿Necesita aprobación?
        ↓
Ejecutar coordinación
        ↓
Integrar resultados
        ↓
Validar
        ↓
Entregar
```

Este checklist debe aplicarse proporcionalmente.

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