---
id: TRI-SOP-000
title: SOPs Module
module: SOPs
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
  - sops
  - procedures
  - execution
  - operations
---

# Trinity AI — SOPs

## Propósito

`02_SOPs` contiene los procedimientos operativos estandarizados utilizados por Trinity AI para ejecutar tareas repetibles de forma consistente, verificable y reutilizable.

Un SOP responde principalmente:

> ¿Cómo debe ejecutarse correctamente esta tarea?

El módulo permite transformar capacidades y metodologías del sistema en procedimientos operativos claros sin duplicar responsabilidades pertenecientes a Agents, Frameworks, Knowledge, Integrations o Automations.

---

## Objetivo

Los SOPs existen para reducir:

- improvisación;
- variabilidad innecesaria;
- errores repetitivos;
- reconstrucción de procesos;
- dependencia de conocimiento implícito;
- carga mental;
- inconsistencias entre Agents.

Y aumentar:

- consistencia;
- velocidad;
- calidad;
- reutilización;
- trazabilidad cuando corresponda;
- capacidad de validación;
- escalabilidad operativa.

---

## Principio Fundamental

> Un SOP documenta una forma validada de ejecutar una tarea repetible.

Un SOP debe ser suficientemente específico para permitir ejecución consistente, pero no debe absorber responsabilidades pertenecientes a otros módulos.

La relación conceptual es:

```text
Framework
│
└── cómo abordar y estructurar el problema

Knowledge
│
└── qué necesita saber Trinity AI

SOP
│
└── cómo ejecutar la tarea

Agent
│
└── quién es responsable de resolverla

Integration
│
└── qué acceso externo puede utilizarse

Automation
│
└── qué proceso puede ejecutarse automáticamente
```

---

## Responsabilidad del Módulo

`02_SOPs` es responsable de:

- almacenar procedimientos operativos reutilizables;
- definir estándares para crear SOPs;
- facilitar descubrimiento y reutilización;
- documentar entradas y resultados esperados;
- definir pasos de ejecución;
- incorporar validaciones;
- identificar dependencias operativas;
- identificar condiciones de finalización;
- identificar puntos de aprobación cuando correspondan;
- permitir ejecución consistente por diferentes Agents o modelos.

No es responsable de:

- definir estrategia;
- almacenar conocimiento general;
- definir comportamiento de IA;
- asignar Agents;
- coordinar trabajo multi-Agent;
- almacenar contexto específico de clientes;
- definir credenciales;
- otorgar permisos;
- ejecutar Automations por sí mismo;
- gobernar cambios documentales.

---

## Qué es un SOP

Un SOP es un procedimiento documentado para una tarea:

```text
Repetible
+
Definible
+
Ejecutable
+
Validable
=
SOP Candidate
```

Ejemplos:

- realizar una investigación;
- crear un calendario de contenido;
- preparar una ficha de producción;
- generar un reporte;
- realizar una auditoría;
- actualizar información mediante una Integration;
- preparar un entregable recurrente.

---

## Qué NO es un SOP

No todo proceso merece convertirse en SOP.

No debe crearse un SOP para:

- una tarea completamente única;
- una decisión estratégica;
- una metodología de pensamiento;
- conocimiento conceptual;
- información específica de un cliente;
- una simple instrucción;
- una acción trivial sin valor reutilizable.

Ejemplos:

```text
"Cómo estructurar una estrategia de contenido"
→ Framework

"Principios de Meta Ads"
→ Knowledge

"Crear el calendario mensual de contenido"
→ SOP

"Líneas Rectas utiliza negro, blanco y gris"
→ Client Context
```

---

## SOP Global vs SOP Específico de Cliente

Trinity AI distingue entre procedimientos globales y procedimientos específicos de cliente.

### SOP Global

Vive en:

```text
02_SOPs/
```

Debe ser reutilizable entre diferentes clientes o proyectos.

Ejemplo:

```text
Monthly Content Planning SOP
Research SOP
Performance Reporting SOP
```

### SOP específico de cliente

Cuando un procedimiento existe únicamente por necesidades particulares de un cliente, debe permanecer dentro de su contexto.

Ejemplo conceptual:

```text
08_Clients/
└── Cliente/
    └── SOPs/
        └── CLIENT_SPECIFIC_SOP.md
```

Solo debe crearse esta carpeta cuando exista una necesidad real.

Un procedimiento específico de cliente no debe convertirse automáticamente en SOP global.

---

## Relación con CORE

CORE determina qué capacidades necesita una solicitud.

Cuando existe una tarea repetible con un SOP aplicable:

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
SOP aplicable
    │
    ▼
Execution
```

CORE no debe duplicar el procedimiento contenido dentro del SOP.

---

## Relación con Agents

Los Agents pueden ejecutar SOPs dentro de su alcance.

```text
Agent
  │
  ▼
Identifica tarea
  │
  ▼
¿Existe SOP aplicable?
  │
  ├── Sí → utilizar SOP
  │
  └── No → continuar dentro de su alcance
```

Un Agent no debe copiar el contenido completo de un SOP dentro de su propia definición.

Debe referenciarlo cuando corresponda.

---

## Relación con Frameworks

Framework y SOP cumplen funciones diferentes.

```text
Framework
    │
    ▼
define cómo abordar el problema

SOP
    │
    ▼
define cómo ejecutar la tarea
```

Un SOP puede utilizar uno o varios Frameworks.

Ejemplo:

```text
Objetivo:
Crear planificación mensual

Framework:
Content Planning Framework

SOP:
Monthly Content Planning SOP
```

El Framework aporta metodología.

El SOP aporta ejecución.

---

## Relación con Knowledge

Knowledge proporciona información necesaria para ejecutar correctamente una tarea.

```text
SOP
 │
 ├── Knowledge relevante
 │
 ▼
Execution
```

Un SOP no debe copiar grandes cantidades de Knowledge.

Debe identificar qué conocimiento necesita consultar.

---

## Relación con Research

Un SOP puede requerir Research cuando la ejecución depende de información:

- externa;
- reciente;
- no disponible;
- incierta;
- específica de una investigación.

El SOP debe definir cuándo Research es necesaria.

No debe almacenar resultados temporales de Research como parte permanente del procedimiento.

---

## Relación con Client Context

Cuando un SOP se ejecuta para un cliente:

```text
SOP Global
    +
Relevant Client Context
    │
    ▼
Client-specific execution
```

El SOP define el procedimiento.

`08_Clients` aporta el contexto.

Esto permite reutilizar el mismo SOP sin crear una copia por cliente.

---

## Relación con Integrations

Un SOP puede requerir una Integration.

Ejemplo:

```text
SOP
 │
 ▼
Necesita actualizar Notion
 │
 ▼
Authorized Integration
 │
 ▼
Execution
```

El SOP puede indicar:

- Integration necesaria;
- operación requerida;
- permisos necesarios;
- validación posterior.

No debe almacenar:

- API keys;
- tokens;
- passwords;
- secrets;
- credenciales.

---

## Relación con Automations

Una Automation puede implementar total o parcialmente un SOP.

La relación correcta es:

```text
SOP
 │
 └── define procedimiento

Automation
 │
 └── automatiza ejecución autorizada
```

Toda Automation debe depender de un procedimiento suficientemente definido.

La existencia de un SOP no implica que deba automatizarse.

---

## Relación con Governance

Governance controla:

- aprobación;
- versionado;
- modificación;
- deprecación;
- auditoría;
- promoción.

Un SOP nuevo no se convierte automáticamente en procedimiento oficial.

Debe respetar su estado documental.

---

## Estados

Los SOPs utilizan los estados documentales definidos por Trinity AI:

```text
Draft
Review
Approved
Deprecated
Archived
```

### Draft

Procedimiento en construcción.

### Review

Procedimiento listo para revisión.

### Approved

Procedimiento validado y autorizado como fuente oficial dentro de su alcance.

### Deprecated

Procedimiento que no debe utilizarse para nuevas ejecuciones.

### Archived

Procedimiento conservado por trazabilidad o historia.

---

## Uso según Estado

Como principio general:

```text
Approved
→ procedimiento oficial

Review
→ referencia controlada

Draft
→ procedimiento en construcción

Deprecated
→ no utilizar para nuevas ejecuciones

Archived
→ referencia histórica
```

Durante desarrollo pueden consultarse documentos no aprobados cuando exista una razón válida, pero su estado debe permanecer explícito.

---

## Descubrimiento de SOPs

Antes de crear un procedimiento nuevo debe buscarse uno existente.

El orden recomendado es:

```text
Need
  │
  ▼
Search Existing SOP
  │
  ├── Exact Match
  │      │
  │      ▼
  │    Reuse
  │
  ├── Partial Match
  │      │
  │      ▼
  │    Adapt
  │
  └── No Match
         │
         ▼
     New Candidate
```

Crear un SOP nuevo debe ser la última opción cuando exista capacidad reutilizable.

---

## Selección de SOP

Un SOP debe seleccionarse según:

- objetivo;
- tipo de tarea;
- condiciones de entrada;
- alcance;
- Agent responsable;
- Framework aplicable;
- contexto;
- herramientas necesarias;
- output esperado.

El nombre del SOP por sí solo no debe ser el único criterio.

---

## Aplicabilidad

Antes de ejecutar un SOP debe verificarse:

```text
¿La tarea coincide con su propósito?
        ↓
¿Se cumplen las condiciones de entrada?
        ↓
¿Existen los inputs necesarios?
        ↓
¿Las dependencias están disponibles?
        ↓
¿Existen permisos suficientes?
        ↓
¿El SOP está vigente?
        ↓
Execute
```

Si alguna condición crítica falla, el SOP no debe ejecutarse como si fuera aplicable.

---

## Ejecución Parcial

Un SOP puede aplicarse parcialmente cuando:

- solo una parte del procedimiento sea necesaria;
- la tarea no requiera todas sus etapas;
- el contexto permita omitir pasos sin afectar calidad o seguridad.

Los pasos obligatorios de validación, riesgo o aprobación no deben omitirse arbitrariamente.

---

## Adaptación

Los SOPs deben permitir adaptación proporcional cuando el contexto lo requiera.

```text
Standard Procedure
        +
Context
        =
Adapted Execution
```

Adaptar un SOP no significa modificar su fuente oficial.

Si una adaptación se vuelve repetitiva y reusable, puede convertirse en Candidate para revisión.

---

## Inputs

Todo SOP debe identificar los inputs necesarios.

Pueden incluir:

- objetivo;
- brief;
- Client Context;
- archivos;
- datos;
- Research;
- decisiones;
- permisos;
- Assets;
- información externa.

Debe distinguirse entre inputs:

```text
Required
Optional
Conditional
```

cuando aporte claridad operativa.

---

## Preconditions

Cuando corresponda, un SOP debe definir condiciones que deben cumplirse antes de comenzar.

Ejemplos:

- acceso disponible;
- cliente identificado;
- información mínima disponible;
- Framework aprobado;
- Integration conectada;
- aprobación previa.

---

## Procedimiento

El procedimiento debe describir pasos ejecutables en orden lógico.

Debe evitar:

- razonamiento abstracto innecesario;
- repetir Knowledge;
- duplicar Frameworks;
- instrucciones ambiguas;
- microgestión sin valor.

Cada paso debe contribuir directamente al resultado.

---

## Validaciones

Todo SOP debe definir cómo determinar si la ejecución fue correcta.

Las validaciones pueden ocurrir:

```text
Before Execution
During Execution
After Execution
```

La profundidad debe ser proporcional al riesgo y al impacto.

---

## Output

Todo SOP debe definir el resultado esperado.

Ejemplos:

- documento;
- calendario;
- análisis;
- reporte;
- actualización;
- archivo;
- registro;
- acción completada.

El output debe poder evaluarse contra criterios claros.

---

## Definition of Done

Todo SOP debe definir cuándo la tarea puede considerarse finalizada.

Puede incluir:

```text
Required Output Created
+
Validation Passed
+
Required Approval Obtained
+
Required Action Confirmed
=
Done
```

No todas las tareas requieren todos estos elementos.

---

## Manejo de Errores

Cuando una ejecución falle, el SOP debe indicar cuando corresponda:

- qué puede recuperarse;
- qué debe detenerse;
- qué debe reintentarse;
- cuándo escalar;
- qué debe comunicarse;
- qué evidencia conservar.

No debe ocultarse un fallo para marcar el procedimiento como completado.

---

## Riesgo

Cuando un SOP incluya acciones relevantes debe considerar:

- impacto;
- reversibilidad;
- permisos;
- alcance;
- sensibilidad;
- consecuencias externas.

Las reglas de decisión y aprobación pertenecen a Foundation y Governance.

El SOP debe aplicarlas, no redefinirlas.

---

## Aprobación Humana

Cuando una etapa requiera aprobación:

```text
Prepare
   │
   ▼
Validate
   │
   ▼
Request Approval
   │
   ├── Approved → Continue
   │
   └── Rejected → Stop / Revise
```

El silencio nunca constituye aprobación.

---

## Trazabilidad

Cuando el impacto lo requiera, una ejecución puede registrar:

```yaml
sop:
version:
request:
agent:
inputs:
execution_status:
approval:
output:
validation:
timestamp:
```

La trazabilidad debe ser proporcional.

---

## Versionado

Cuando un SOP aprobado cambia de forma material debe respetarse el sistema de versionado definido por Governance y Documentation Standards.

Cambios materiales pueden incluir:

- procedimiento;
- responsabilidades;
- validaciones;
- permisos;
- outputs;
- criterios de finalización;
- dependencias críticas.

Correcciones puramente editoriales no necesariamente requieren el mismo nivel de revisión.

---

## Creación de Nuevos SOPs

Antes de crear un SOP debe evaluarse:

```text
¿La tarea se repite?
        ↓
¿Existe valor en estandarizarla?
        ↓
¿Ya existe un SOP aplicable?
        ↓
¿Puede adaptarse uno existente?
        ↓
¿La necesidad es global o específica de cliente?
        ↓
Create Candidate
```

---

## SOP Candidate

Un procedimiento nuevo debe comenzar como:

```text
status: Draft
```

No debe convertirse automáticamente en `Approved`.

Debe pasar por el proceso de revisión definido por Governance.

---

## Promoción desde Aprendizajes

Una ejecución puede revelar una mejora.

```text
Execution
   │
   ▼
Learning
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

El SOP oficial no debe modificarse automáticamente durante una ejecución.

---

## Deprecación

Un SOP puede deprecarse cuando:

- fue reemplazado;
- dejó de ser seguro;
- dejó de ser aplicable;
- una Integration cambió;
- el procedimiento ya no representa la operación real.

Un SOP deprecated debe indicar, cuando exista:

- motivo;
- fecha;
- reemplazo.

---

## Nombres de SOP

Los nombres deben describir claramente el procedimiento.

Formato recomendado:

```text
<Proceso>_SOP.md
```

Ejemplos:

```text
RESEARCH_SOP.md
MONTHLY_CONTENT_PLANNING_SOP.md
CONTENT_PRODUCTION_SOP.md
PERFORMANCE_REPORTING_SOP.md
```

Debe evitarse:

```text
SOP_FINAL.md
NEW_SOP.md
PROCESS_2.md
UPDATED_SOP.md
```

---

## Organización del Módulo

La estructura inicial es:

```text
02_SOPs/
├── README.md
└── SOP_STANDARD.md
```

A medida que el sistema crezca puede evolucionar hacia categorías.

Ejemplo conceptual:

```text
02_SOPs/
├── README.md
├── SOP_STANDARD.md
├── Research/
├── Content/
├── Reporting/
├── Operations/
└── Documentation/
```

No deben crearse carpetas vacías o categorías anticipadamente.

La estructura debe crecer por necesidad real.

---

## SOP_STANDARD.md

`SOP_STANDARD.md` define la estructura y requisitos que debe cumplir cada SOP.

Este README define el módulo.

`SOP_STANDARD.md` define cómo construir sus documentos.

La relación es:

```text
README.md
   │
   └── qué es y cómo funciona el módulo

SOP_STANDARD.md
   │
   └── cómo debe documentarse un SOP
```

---

## Recuperación Selectiva

Los Agents no deben cargar todos los SOPs.

Deben recuperar únicamente procedimientos potencialmente relevantes.

```text
Task
 │
 ▼
Identify Procedure Need
 │
 ▼
Retrieve Relevant SOP
 │
 ▼
Validate Applicability
 │
 ▼
Execute
```

---

## Modelo Agnóstico

Los SOPs deben poder ser interpretados por diferentes modelos de IA.

No deben depender innecesariamente de:

- Claude;
- ChatGPT;
- Gemini;
- un proveedor específico.

Cuando un procedimiento requiera una herramienta particular, debe declararlo explícitamente.

---

## Antipatrones

Los SOPs no deben:

- convertirse en Frameworks disfrazados;
- almacenar Knowledge general;
- almacenar Client Context;
- copiar instrucciones completas de Integrations;
- contener credenciales;
- duplicar otros SOPs;
- definir responsabilidades completas de Agents;
- ejecutar Automations por sí mismos;
- asumir permisos;
- interpretar silencio como aprobación;
- esconder errores;
- convertirse automáticamente en oficiales;
- crecer hasta documentar todo el sistema;
- crearse para tareas que no tienen valor reutilizable.

---

## Criterios de Calidad

Un SOP de calidad debe ser:

```text
Relevant
+
Reusable
+
Executable
+
Clear
+
Validatable
+
Maintainable
```

Debe permitir que otro Agent o modelo pueda ejecutar el procedimiento sin depender del conocimiento implícito de quien lo creó.

---

## Criterios de Éxito del Módulo

`02_SOPs` funciona correctamente cuando:

- los procedimientos repetibles pueden reutilizarse;
- los Agents no necesitan reconstruir procesos;
- Frameworks y SOPs permanecen separados;
- Knowledge no se duplica;
- Client Context permanece aislado;
- Integrations se utilizan con permisos;
- Automations pueden apoyarse en procedimientos definidos;
- las ejecuciones pueden validarse;
- los procedimientos evolucionan mediante Governance;
- el sistema puede crecer sin acumular SOPs redundantes.

---

## Checklist de Selección

Antes de utilizar un SOP:

```text
¿Existe?
   ↓
¿Es aplicable?
   ↓
¿Está vigente?
   ↓
¿Tengo los inputs?
   ↓
¿Tengo permisos?
   ↓
¿Necesito Framework?
   ↓
¿Necesito Client Context?
   ↓
¿Necesito Integration?
   ↓
Execute
   ↓
Validate
```

---

## Regla de Oro

> Estandarizar únicamente aquello que aporta consistencia sin eliminar la capacidad de adaptación.

```text
Proceso repetible
      +
Procedimiento claro
      +
Contexto correcto
      +
Validación
      =
Ejecución consistente
```

Los SOPs deben hacer que Trinity AI ejecute mejor.

No hacer que Trinity AI sea más burocrático.