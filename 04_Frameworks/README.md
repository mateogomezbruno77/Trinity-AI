---
id: TRI-FWK-000
title: Frameworks Module
module: Frameworks
version: 1.0.0
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
  - frameworks
  - methodology
  - reasoning
  - strategy
  - capabilities
---

# Trinity AI — Frameworks

## Propósito

`04_Frameworks` contiene las metodologías reutilizables que Trinity AI utiliza para estructurar y razonar sobre categorías recurrentes de problemas.

Un Framework responde principalmente:

> ¿Cómo debería abordarse este tipo de problema?

El módulo permite que Trinity AI no tenga que reinventar su forma de pensar cada vez que enfrenta un problema conocido, sin convertir esa forma de pensar en un procedimiento operativo rígido.

---

## Objetivo

Los Frameworks existen para reducir:

- razonamiento improvisado;
- inconsistencia entre respuestas;
- pérdida de criterio metodológico entre Agents;
- dependencia de la experiencia individual de quien resuelve el problema;
- reconstrucción de metodología en cada solicitud.

Y aumentar:

- consistencia de análisis;
- calidad de las decisiones;
- velocidad de resolución;
- reutilización de metodología validada;
- capacidad de comparar alternativas con criterios explícitos;
- escalabilidad del razonamiento del sistema.

---

## Principio Fundamental

> Un Framework proporciona una metodología reutilizable para estructurar un tipo de problema sin convertirse en un procedimiento operativo.

La relación buscada es:

```text
Problem
   +
Relevant Methodology
   +
Evidence
   +
Context
   =
Structured Resolution
```

El Framework aporta estructura de razonamiento.

No debe eliminar adaptación ni criterio.

---

## Responsabilidad del Módulo

`04_Frameworks` es responsable de:

- almacenar metodologías reutilizables y globales;
- definir el estándar de creación de Frameworks;
- facilitar descubrimiento y reutilización;
- documentar cuándo aplicar cada metodología;
- estructurar etapas, principios y criterios de razonamiento;
- definir cómo se valida una aplicación correcta;
- permitir que diferentes Agents y modelos razonen de forma consistente.

No es responsable de:

- ejecutar tareas operativas;
- almacenar conocimiento general;
- almacenar contexto de clientes;
- definir procedimientos paso a paso de ejecución;
- asignar Agents;
- otorgar permisos;
- ejecutar Integrations o Automations;
- gobernar cambios documentales.

---

## Qué es un Framework

Un Framework es una metodología para estructurar un tipo de problema:

```text
Recurrent Problem
+
Reusable Methodology
+
Identifiable Criteria
+
Value Across Executions
=
Framework Candidate
```

Ejemplos:

- estructurar una investigación;
- analizar performance;
- desarrollar estrategia creativa;
- planificar contenido;
- priorizar oportunidades;
- estructurar reporting.

---

## Qué NO es un Framework

No todo conocimiento o proceso merece convertirse en Framework.

No debe crearse un Framework para:

- una tarea operativa paso a paso;
- información conceptual sin metodología;
- un procedimiento repetible sin ambigüedad de enfoque;
- contexto específico de un cliente;
- un problema completamente único;
- una acción trivial sin valor reutilizable.

Ejemplos:

```text
"Cómo estructurar una estrategia de contenido"
→ Framework

"Crear el calendario mensual de contenido"
→ SOP

"Principios de Meta Ads"
→ Knowledge

"Líneas Rectas utiliza negro, blanco y gris"
→ Client Context
```

---

## Framework vs Otros Módulos

Un Framework se distingue de otras capacidades del sistema por lo que aporta.

### Framework vs SOP

```text
Framework
    │
    ▼
define cómo abordar y estructurar el problema

SOP
    │
    ▼
define cómo ejecutar la tarea paso a paso
```

Un SOP puede utilizar uno o varios Frameworks. Un Framework no reemplaza la ejecución.

### Framework vs Knowledge

```text
Knowledge
    │
    ▼
qué necesita saber Trinity AI

Framework
    │
    ▼
cómo debe razonar Trinity AI sobre ese conocimiento
```

Un Framework consulta Knowledge cuando lo necesita. No debe copiarlo ni convertirse en un repositorio de conocimiento.

### Framework vs Agent

```text
Agent
    │
    ▼
quién es responsable de resolver la tarea

Framework
    │
    ▼
qué metodología puede utilizar ese responsable
```

Un Framework no define responsables, límites ni permisos. Un Agent puede aplicar varios Frameworks distintos.

### Framework vs Research

```text
Research
    │
    ▼
evidencia externa, reciente o específica

Framework
    │
    ▼
metodología estable para estructurar el análisis
```

Un Framework puede requerir Research como input. No debe almacenar resultados de investigación como si fueran metodología permanente.

### Framework vs Client Context

```text
Framework
    │
    ▼
metodología reutilizable entre clientes

Client Context
    │
    ▼
información específica de un cliente
```

Un Framework se aplica utilizando Client Context como input. No debe absorber información específica de un cliente dentro de su definición global.

### Framework vs Integration

```text
Framework
    │
    ▼
estructura el razonamiento

Integration
    │
    ▼
permite acceder a una herramienta externa
```

Un Framework no ejecuta Integrations. Puede indicar que su aplicación depende de información obtenida mediante una.

### Framework vs Automation

```text
Framework
    │
    ▼
define cómo pensar el problema

Automation
    │
    ▼
ejecuta un proceso autorizado
```

Un Framework no se automatiza directamente. Un SOP derivado de su aplicación puede ser parcialmente automatizado.

---

## Relación con CORE

CORE determina qué capacidades necesita una solicitud.

```text
Solicitud
    │
    ▼
CORE
    │
    ▼
Capability Selection
    │
    ▼
Framework aplicable
    │
    ▼
Structured Reasoning
```

CORE no debe duplicar la metodología contenida dentro de un Framework.

---

## Relación con Orchestrator

Cuando una solicitud requiere coordinación entre múltiples Agents o capacidades, el Orchestrator puede indicar qué Framework corresponde utilizar.

```text
Orchestrator
    │
    ▼
Identifica tipo de problema
    │
    ▼
¿Existe Framework aplicable?
    │
    ├── Sí → asignarlo al Agent responsable
    │
    └── No → continuar sin Framework
```

El Orchestrator no debe aplicar la metodología por sí mismo cuando exista un Agent responsable.

---

## Relación con SOPs

Framework y SOP cumplen funciones diferentes y complementarias.

```text
Objetivo:
Crear planificación mensual

Framework:
Content Planning Framework

SOP:
Monthly Content Planning SOP
```

El Framework aporta metodología. El SOP aporta ejecución. Ver `02_SOPs/README.md`.

---

## Relación con Knowledge

Knowledge proporciona la información que un Framework necesita para aplicarse correctamente.

```text
Framework
 │
 ├── Knowledge relevante
 │
 ▼
Structured Reasoning
```

Un Framework no debe copiar grandes cantidades de Knowledge. Debe identificar qué conocimiento necesita consultar.

---

## Relación con Client Context

Cuando un Framework se aplica para un cliente:

```text
Framework Global
    +
Relevant Client Context
    │
    ▼
Applied Methodology
```

El Framework define la metodología. `08_Clients` aporta el contexto. Esto permite reutilizar el mismo Framework sin crear una copia por cliente.

---

## Frameworks Globales y Específicos de Cliente

Trinity AI distingue entre metodologías globales y metodologías específicas de cliente.

### Frameworks Globales

Viven en:

```text
04_Frameworks/
```

Deben ser reutilizables entre diferentes clientes o proyectos.

Ejemplo:

```text
Research Framework
Content Planning Framework
Performance Analysis Framework
```

### Frameworks Específicos de Cliente

Cuando una metodología existe únicamente por una diferencia real de enfoque de un cliente, debe permanecer dentro de su contexto.

Ejemplo conceptual:

```text
08_Clients/
└── Cliente/
    └── Frameworks/
        └── CLIENT_SPECIFIC_FRAMEWORK.md
```

No debe crearse esta carpeta salvo que exista una diferencia metodológica real, no solo una diferencia de branding, audiencia o producto.

---

## Cuándo Utilizar un Framework

Debe considerarse un Framework cuando exista:

```text
Problema recurrente
        +
Necesidad metodológica
        +
Estructura reutilizable
        +
Criterios identificables
        =
Framework aplicable
```

---

## Cuándo NO Utilizar un Framework

No debe utilizarse un Framework cuando:

- la respuesta sea directa;
- el problema sea completamente único;
- la tarea sea puramente operativa;
- agregar estructura no mejore el resultado;
- otro Framework más simple sea suficiente.

Agregar metodología a un problema simple aumenta carga mental sin aumentar calidad.

---

## Selección de Framework

Un Framework debe seleccionarse según:

- el tipo de problema;
- el objetivo buscado;
- la información disponible;
- el Agent responsable;
- el resultado esperado;
- la existencia de Frameworks relacionados.

El nombre del Framework por sí solo no debe ser el único criterio de selección.

---

## Aplicabilidad

Antes de aplicar un Framework debe verificarse:

```text
¿El problema coincide con su propósito?
        ↓
¿Están disponibles los inputs necesarios?
        ↓
¿El Framework está vigente?
        ↓
¿Existe evidencia suficiente para aplicarlo?
        ↓
Apply
```

Si una condición crítica falla, el Framework no debe aplicarse como si fuera aplicable.

---

## Recuperación Selectiva

Los Agents no deben cargar todos los Frameworks del sistema.

```text
Task
 │
 ▼
Identify Methodological Need
 │
 ▼
Retrieve Relevant Framework
 │
 ▼
Validate Applicability
 │
 ▼
Apply
```

Más contexto no significa automáticamente mejor resultado.

---

## Uso de Múltiples Frameworks

Pueden combinarse cuando resuelvan dimensiones diferentes del mismo problema.

```text
Research Framework
        ↓
Evidence

Performance Analysis Framework
        ↓
Diagnosis

Creative Strategy Framework
        ↓
Strategic Direction
```

Debe evitarse combinar Frameworks redundantes o que resuelvan la misma dimensión del problema.

---

## Inputs

Todo Framework debe identificar la información necesaria para aplicarse.

Puede clasificarse como:

```text
Required
Optional
Conditional
```

Ejemplo:

```text
Required:
- objetivo;
- problema.

Optional:
- referencias;
- antecedentes.

Conditional:
- performance histórica;
- Research externa.
```

No debe inventarse información faltante.

---

## Principios

Los principios definen reglas metodológicas propias de cada Framework.

Deben:

- orientar el análisis;
- reducir ambigüedad;
- mantenerse dentro de su dominio;
- evitar duplicar Foundation.

Ejemplo:

```text
Priorizar evidencia sobre intuición cuando exista evidencia suficiente.
```

---

## Etapas Metodológicas

Cuando corresponda, un Framework puede estructurarse en etapas de razonamiento.

```text
Stage 1
Understand
    │
    ▼
Stage 2
Analyze
    │
    ▼
Stage 3
Structure
    │
    ▼
Stage 4
Prioritize
    │
    ▼
Stage 5
Recommend
```

Las etapas representan fases de razonamiento, no pasos operativos.

---

## Criterios de Decisión

Cuando la metodología produzca decisiones debe definir criterios relevantes.

Ejemplo:

```text
Relevance
Impact
Evidence
Feasibility
Risk
```

Decisiones de alto impacto deben respetar `00_Foundation/16_Decision_Framework.md`. Un Framework específico no debe duplicarlo.

---

## Preguntas Guía

Pueden utilizarse preguntas para orientar el análisis.

```text
¿Qué objetivo se busca?
¿Qué problema impide alcanzarlo?
¿Qué sabemos?
¿Qué estamos suponiendo?
¿Qué evidencia falta?
¿Qué alternativas existen?
```

Estas preguntas estructuran razonamiento. No implican que deban formularse todas al usuario.

---

## Adaptación

Un Framework debe poder adaptarse al contexto sin perder su propósito.

```text
Framework
    +
Problem Context
    +
Client Context
    +
Evidence
    =
Applied Methodology
```

Adaptar un Framework durante una ejecución no modifica automáticamente su fuente oficial.

---

## Resultado Esperado

Todo Framework debe indicar qué resultado metodológico produce.

Ejemplos:

- diagnóstico estructurado;
- estrategia;
- hipótesis priorizadas;
- mapa de oportunidades;
- recomendación;
- clasificación.

Ese resultado puede convertirse después en input de un SOP, Agent u otro Framework.

---

## Validación

Todo Framework debe permitir determinar si fue aplicado correctamente.

Puede evaluarse:

- cobertura;
- consistencia;
- evidencia;
- relevancia;
- alineación;
- claridad;
- priorización.

La validación de un Framework comprueba calidad metodológica. La validación de un SOP comprueba correcta ejecución. Ambas pueden coexistir.

---

## Manejo de Incertidumbre

Debe respetarse la clasificación definida por Foundation:

```text
Known
Inferred
Unknown
Candidate
```

Cuando una incertidumbre pueda cambiar materialmente el resultado debe investigarse, declararse, validarse o escalarse.

---

## Evidencia

Debe diferenciarse entre:

```text
Fact
Data
Observation
Inference
Hypothesis
Unknown
```

Un Framework no debe tratar hipótesis como hechos ni ocultar evidencia contradictoria.

---

## Estados

Los Frameworks utilizan los estados documentales definidos por Trinity AI:

```text
Draft
Review
Approved
Deprecated
Archived
```

### Draft

Metodología en construcción.

### Review

Metodología lista para revisión.

### Approved

Metodología validada y autorizada como fuente oficial dentro de su alcance.

### Deprecated

Metodología que no debe utilizarse para nuevas aplicaciones.

### Archived

Metodología conservada por trazabilidad o historia.

---

## Uso según Estado

Como principio general:

```text
Approved
→ metodología oficial

Review
→ referencia controlada

Draft
→ metodología en construcción

Deprecated
→ no utilizar para nuevas aplicaciones

Archived
→ referencia histórica
```

---

## Aprendizaje y Evolución

Los Frameworks deben evolucionar mediante evidencia y aprendizaje, no por conveniencia puntual.

```text
Application
    │
    ▼
Observation
    │
    ▼
Reusable Learning
    │
    ▼
Candidate
    │
    ▼
Review
    │
    ▼
Approved Change
```

Un Framework oficial no debe modificarse silenciosamente durante una ejecución.

---

## Deprecación

Un Framework debe deprecarse cuando:

- fue reemplazado;
- dejó de ser útil;
- produce resultados inconsistentes;
- quedó conceptualmente obsoleto;
- existe una metodología superior validada.

Debe indicarse el reemplazo cuando exista.

---

## Nomenclatura

Formato recomendado:

```text
<DOMAIN>_FRAMEWORK.md
```

Ejemplos:

```text
RESEARCH_FRAMEWORK.md
CONTENT_PLANNING_FRAMEWORK.md
CREATIVE_STRATEGY_FRAMEWORK.md
PERFORMANCE_ANALYSIS_FRAMEWORK.md
```

Debe evitarse:

```text
FRAMEWORK_FINAL.md
NEW_FRAMEWORK.md
METHOD_2.md
```

---

## Organización del Módulo

La estructura inicial es:

```text
04_Frameworks/
├── README.md
└── FRAMEWORK_STANDARD.md
```

A medida que el sistema crezca puede evolucionar hacia categorías.

Ejemplo conceptual:

```text
04_Frameworks/
├── README.md
├── FRAMEWORK_STANDARD.md
├── Research/
├── Content/
├── Strategy/
└── Reporting/
```

No deben crearse carpetas vacías o categorías anticipadamente. La estructura debe crecer por necesidad real.

---

## Relación con FRAMEWORK_STANDARD.md

`FRAMEWORK_STANDARD.md` define la estructura y requisitos que debe cumplir cada Framework.

Este README define el módulo.

La relación es:

```text
README.md
   │
   └── qué es y cómo funciona el módulo

FRAMEWORK_STANDARD.md
   │
   └── cómo debe documentarse un Framework
```

---

## Modelo Agnóstico

Los Frameworks deben poder ser interpretados por diferentes modelos de IA.

No deben depender innecesariamente de:

- Claude;
- ChatGPT;
- Gemini;
- un proveedor específico.

Cuando una metodología requiera una herramienta particular, debe declararlo explícitamente.

---

## Antipatrones

Los Frameworks no deben:

- convertirse en procedimientos operativos disfrazados;
- duplicar un SOP;
- duplicar Knowledge;
- almacenar Client Context;
- contener credenciales;
- ejecutar Integrations o Automations;
- definir Agents completos;
- crear falsa precisión;
- ignorar incertidumbre;
- ocultar evidencia contradictoria;
- convertirse en global automáticamente;
- crecer sin necesidad metodológica real;
- utilizarse por obligación cuando el problema es simple.

---

## Criterios de Calidad

Un Framework de calidad debe ser:

```text
Relevant
+
Reusable
+
Structured
+
Evidence-aware
+
Adaptable
+
Validatable
```

Debe permitir que otro Agent o modelo aplique la metodología sin depender del criterio implícito de quien la creó.

---

## Criterios de Éxito del Módulo

`04_Frameworks` funciona correctamente cuando:

- los problemas recurrentes se resuelven con metodología consistente;
- los Agents no necesitan reconstruir razonamiento desde cero;
- Frameworks y SOPs permanecen separados;
- Knowledge no se duplica;
- Client Context permanece aislado;
- las aplicaciones pueden validarse;
- las metodologías evolucionan mediante Governance;
- el sistema puede crecer sin acumular Frameworks redundantes.

---

## Checklist de Selección

Antes de utilizar un Framework:

```text
¿Existe?
   ↓
¿Es aplicable?
   ↓
¿Está vigente?
   ↓
¿Tengo los inputs?
   ↓
¿Necesito Knowledge?
   ↓
¿Necesito Research?
   ↓
¿Necesito Client Context?
   ↓
Apply
   ↓
Validate
```

---

## Regla de Oro

> Un Framework debe proporcionar la estructura suficiente para mejorar el razonamiento sin convertir la metodología en una receta rígida.

```text
Clear Problem
     +
Reusable Methodology
     +
Relevant Evidence
     +
Correct Context
     +
Validation
     =
Reliable Framework
```

Los Frameworks existen para que Trinity AI no tenga que inventar nuevamente cómo pensar problemas que ya aprendió a estructurar.
