---
id: TRI-SOP-001
title: SOP Standard
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
  - 00_Foundation/14_AI_Behavior.md
  - 00_Foundation/16_Decision_Framework.md
  - 02_SOPs/README.md
tags:
  - sops
  - standards
  - procedures
  - execution
  - validation
  - documentation
---

# Trinity AI — SOP Standard

## Propósito

`SOP_STANDARD.md` define el estándar obligatorio para diseñar, documentar, revisar y mantener Standard Operating Procedures dentro de Trinity AI.

Su función es garantizar que todos los SOPs tengan una estructura consistente, sean ejecutables por diferentes Agents o modelos de IA y puedan integrarse correctamente con el resto del sistema.

Este documento responde:

> ¿Cómo debe estar construido un SOP dentro de Trinity AI?

No define procedimientos específicos.

Define el estándar que esos procedimientos deben respetar.

---

## Objetivo

Todo SOP debe permitir responder claramente:

```text
¿Qué tarea ejecuta?
        ↓
¿Cuándo aplica?
        ↓
¿Qué necesita para comenzar?
        ↓
¿Qué capacidades necesita?
        ↓
¿Qué pasos debe ejecutar?
        ↓
¿Qué decisiones o aprobaciones pueden intervenir?
        ↓
¿Cómo se valida?
        ↓
¿Qué resultado debe producir?
        ↓
¿Cuándo puede considerarse terminado?
```

Un SOP que no permita responder estas preguntas no está suficientemente definido.

---

## Principio Fundamental

> Un SOP debe convertir una tarea repetible en un procedimiento ejecutable, verificable y mantenible.

Debe existir suficiente precisión para reducir improvisación sin convertir el procedimiento en una secuencia rígida incapaz de adaptarse al contexto.

La estructura buscada es:

```text
Standard Procedure
        +
Relevant Context
        +
Authorized Capabilities
        +
Validation
        =
Reliable Execution
```

---

## Alcance

Este estándar aplica a todos los SOPs globales almacenados dentro de:

```text
02_SOPs/
```

También debe utilizarse como referencia para SOPs específicos de clientes cuando estos existan dentro de:

```text
08_Clients/
└── Cliente/
    └── SOPs/
```

Las particularidades de un cliente pueden extender un SOP cuando sea necesario, pero no deben eliminar controles fundamentales de:

- permisos;
- riesgo;
- aprobación;
- validación;
- trazabilidad cuando corresponda.

---

## Cuándo Crear un SOP

Debe considerarse un SOP cuando una tarea sea:

- repetible;
- suficientemente estable;
- operativamente definible;
- reutilizable;
- susceptible de validación;
- valiosa para más de una ejecución.

La evaluación mínima es:

```text
¿La tarea se repite?
        ↓
¿Existe valor en estandarizarla?
        ↓
¿Puede describirse un procedimiento?
        ↓
¿Puede validarse el resultado?
        ↓
¿No existe ya un SOP aplicable?
        ↓
SOP Candidate
```

---

## Cuándo NO Crear un SOP

No debe crearse un SOP cuando el contenido corresponda principalmente a:

```text
Cómo pensar un problema
→ Framework

Qué necesita saber el sistema
→ Knowledge

Quién debe resolverlo
→ Agent

Información específica de un cliente
→ Client Context

Cómo acceder a una herramienta
→ Integration

Qué proceso se ejecuta automáticamente
→ Automation
```

Tampoco debe crearse para una tarea única sin valor reutilizable.

---

## Reutilizar Antes de Crear

Antes de crear un SOP nuevo debe verificarse:

1. si existe un SOP equivalente;
2. si existe uno suficientemente cercano;
3. si puede reutilizarse directamente;
4. si puede adaptarse sin alterar su propósito;
5. si la necesidad es realmente reutilizable.

La secuencia es:

```text
Search
  │
  ▼
Reuse
  │
  ▼
Adapt
  │
  ▼
Create
```

Crear debe ser la última opción.

---

## Estructura Obligatoria

Todo SOP debe contemplar, cuando sean aplicables, los siguientes componentes:

```text
Front Matter
Título
Propósito
Resultado Esperado
Alcance
Cuándo Utilizar
Cuándo No Utilizar
Trigger
Inputs
Precondiciones
Responsable
Capacidades Relacionadas
Procedimiento
Puntos de Decisión
Validaciones
Manejo de Errores
Aprobación Humana
Output
Definition of Done
Trazabilidad
Escalamiento
Mantenimiento
```

Una sección puede omitirse únicamente cuando no tenga sentido para ese procedimiento.

No debe omitirse información crítica solo para reducir longitud.

---

## Front Matter

Todo SOP debe comenzar con Front Matter YAML válido.

Formato base:

```yaml
---
id: TRI-SOP-XXX
title:
module: SOPs
version: 1.0.0
status: Draft
owner: Trinity AI
created:
last_updated:
reviewed_by:
approved_by:
next_review:
dependencies: []
tags:
  - sop
---
```

El Front Matter debe respetar `00_Foundation/13_Documentation_Standards.md`.

---

## ID

Cada SOP debe tener un identificador único.

Formato recomendado:

```text
TRI-SOP-XXX
```

Ejemplo:

```text
TRI-SOP-101
TRI-SOP-102
TRI-SOP-103
```

Los IDs no deben reutilizarse para procedimientos diferentes.

---

## Title

El título debe describir el procedimiento claramente.

Correcto:

```text
Monthly Content Planning SOP
Research SOP
Performance Reporting SOP
```

Evitar:

```text
New SOP
Final Process
Procedure 2
Updated Workflow
```

---

## Module

Para SOPs globales:

```yaml
module: SOPs
```

Para SOPs específicos de cliente puede utilizarse la convención definida por Documentation Standards o Governance cuando corresponda.

---

## Version

Todo SOP debe tener versión.

Versión inicial recomendada:

```yaml
version: 1.0.0
```

Los cambios posteriores deben respetar las reglas de versionado definidas por Trinity AI.

---

## Status

Todo SOP nuevo debe comenzar como:

```yaml
status: Draft
```

Estados permitidos:

```text
Draft
Review
Approved
Deprecated
Archived
```

Un SOP no puede declararse `Approved` únicamente porque fue creado correctamente.

---

## Dependencies

Debe declarar únicamente dependencias documentales reales.

Ejemplo:

```yaml
dependencies:
  - CORE.md
  - 04_Frameworks/CONTENT_PLANNING_FRAMEWORK.md
```

No deben agregarse dependencias solo porque otro documento sea conceptualmente relacionado.

Esto evita dependencias innecesarias y ciclos documentales.

---

## Título Principal

Después del Front Matter debe existir exactamente un H1.

Ejemplo:

```text
# Monthly Content Planning SOP
```

Las secciones principales deben utilizar H2.

Las subsecciones deben respetar la jerarquía Markdown definida por Documentation Standards.

---

## Propósito

Debe explicar:

- qué procedimiento define;
- qué problema operativo resuelve;
- por qué existe.

Debe ser breve y operativo.

Ejemplo conceptual:

```text
Este SOP define el procedimiento para transformar los objetivos mensuales de un cliente en un calendario de contenido validado y listo para producción.
```

---

## Resultado Esperado

Debe definir qué debe existir al finalizar correctamente el procedimiento.

Ejemplo:

```text
Resultado esperado:

Calendario mensual completo, validado y listo para avanzar a producción.
```

Debe evitar resultados ambiguos como:

```text
"Mejor planificación."
```

---

## Alcance

Debe establecer qué incluye y qué queda fuera del procedimiento.

Ejemplo:

```text
Incluye:
- planificación;
- priorización;
- definición de piezas.

No incluye:
- grabación;
- edición;
- publicación.
```

Esto evita que el SOP absorba responsabilidades de otros procesos.

---

## Cuándo Utilizar

Debe indicar las condiciones bajo las cuales el SOP es aplicable.

Ejemplo:

```text
Utilizar cuando:
- exista una planificación mensual;
- el cliente esté identificado;
- existan objetivos de contenido.
```

---

## Cuándo No Utilizar

Debe indicar situaciones donde el procedimiento no corresponde.

Ejemplo:

```text
No utilizar para:
- contenido reactivo urgente;
- una pieza aislada;
- planificación de campañas pagas si existe un SOP específico.
```

---

## Trigger

Debe identificar qué inicia el procedimiento cuando exista un trigger reconocible.

Puede ser:

- solicitud del usuario;
- evento;
- calendario;
- Automation;
- cambio de estado;
- resultado de otro SOP;
- Agent;
- Integration.

Ejemplo:

```text
Trigger:
Solicitud aprobada de planificación mensual.
```

No todos los SOPs necesitan un trigger automático.

---

## Inputs

Debe identificar la información necesaria para comenzar.

Clasificación recomendada:

```text
Required
Optional
Conditional
```

Ejemplo:

```text
Required:
- cliente;
- objetivo;
- período.

Optional:
- referencias;
- campañas anteriores.

Conditional:
- performance histórica cuando exista.
```

---

## Precondiciones

Debe indicar qué debe ser verdadero antes de ejecutar.

Ejemplos:

- Client Context disponible;
- permisos suficientes;
- Integration conectada;
- datos mínimos disponibles;
- aprobación previa obtenida;
- dependencia completada.

Si una precondición crítica falla, el procedimiento debe detenerse o escalar.

---

## Responsable

Debe identificar el rol responsable de ejecutar o supervisar el SOP.

Preferentemente debe referenciar una capacidad o Agent, no una persona específica.

Ejemplo:

```text
Responsible Agent:
Content Planner
```

Un SOP no debe redefinir toda la descripción del Agent.

---

## Capacidades Relacionadas

Debe declarar únicamente las capacidades relevantes para la ejecución.

Puede incluir:

```text
Frameworks
Knowledge
Research
Client Context
Templates
Assets
Integrations
Automations
```

---

## Frameworks Relacionados

Cuando exista un Framework aplicable debe referenciarse.

Ejemplo:

```text
Framework:
Content Planning Framework
```

El SOP no debe copiar la metodología completa del Framework.

---

## Knowledge Requerido

Debe identificar qué conocimiento puede ser necesario.

Ejemplo:

```text
Knowledge:
- Content Marketing
- Instagram
- Audience Strategy
```

No debe copiarse Knowledge completo dentro del SOP.

---

## Research

Debe especificarse cuando la ejecución puede necesitar información externa o actualizada.

Ejemplo:

```text
Research required when:
- faltan datos;
- la información puede haber cambiado;
- se necesita benchmark;
- existe incertidumbre relevante.
```

Research debe mantenerse separado del procedimiento.

---

## Client Context

Cuando la tarea sea para un cliente, debe identificarse qué contexto puede ser necesario.

Ejemplo:

```text
Client Context:
- objetivos;
- audiencia;
- identidad;
- productos;
- decisiones aprobadas;
- historial relevante.
```

Debe recuperarse únicamente lo necesario.

---

## Templates

Si existe una plantilla obligatoria o recomendada debe declararse.

Ejemplo:

```text
Template:
Content Production Brief Template
```

---

## Assets

Cuando la tarea necesite recursos existentes debe especificarse.

Ejemplo:

```text
Assets:
- logo;
- fotografías;
- branding;
- referencias.
```

---

## Integrations

Cuando el SOP requiera interacción con una herramienta externa debe indicar:

- Integration;
- operación necesaria;
- nivel de acceso;
- permisos;
- validación posterior.

Ejemplo:

```text
Integration:
Notion

Operation:
Create approved content tasks
```

No debe incluir credenciales.

---

## Automations

Si existe una Automation relacionada puede referenciarse.

Ejemplo:

```text
Automation:
Content Planning Automation
```

El SOP continúa siendo la definición operativa.

La Automation es una implementación posible.

---

## Procedimiento

El procedimiento constituye el núcleo del SOP.

Debe dividirse en etapas o pasos claros.

Ejemplo:

```text
1. Recuperar contexto.
2. Validar inputs.
3. Aplicar Framework.
4. Generar propuesta.
5. Validar resultado.
6. Solicitar aprobación cuando corresponda.
7. Preparar output final.
```

Los pasos deben ser:

- accionables;
- ordenados;
- verificables;
- suficientemente claros;
- proporcionales.

---

## Etapas vs Pasos

Puede utilizarse una estructura por etapas cuando el procedimiento sea complejo.

Ejemplo:

```text
Etapa 1 — Context Retrieval
Etapa 2 — Analysis
Etapa 3 — Production
Etapa 4 — Validation
Etapa 5 — Delivery
```

Dentro de cada etapa pueden existir pasos.

No debe forzarse una estructura excesivamente granular.

---

## Flexibilidad Operativa

Un SOP no debe convertirse en una secuencia rígida cuando la tarea permite adaptación.

Puede definir:

```text
Required Steps
Conditional Steps
Optional Steps
```

Los pasos de:

- seguridad;
- permisos;
- aprobación;
- validación crítica;

no deben omitirse arbitrariamente.

---

## Puntos de Decisión

Cuando el procedimiento pueda tomar caminos diferentes debe documentarse.

Ejemplo:

```text
¿Existe información suficiente?
        │
   ┌────┴────┐
   │         │
  Sí        No
   │         │
   ▼         ▼
Continue   Research
```

Los puntos de decisión deben utilizar criterios explícitos cuando sea posible.

---

## Decision Framework

Cuando una decisión tenga impacto relevante debe aplicarse:

```text
00_Foundation/16_Decision_Framework.md
```

El SOP no debe reconstruir el sistema completo de decisión.

Debe indicar cuándo utilizarlo.

---

## Validaciones

Todo SOP debe definir criterios de validación.

Pueden existir:

### Pre-Execution Validation

Antes de comenzar.

### In-Process Validation

Durante la ejecución.

### Final Validation

Antes de considerar el procedimiento completado.

---

## Validación Proporcional

La validación debe adaptarse a:

```text
Risk
+
Impact
+
Reversibility
+
Complexity
```

No debe añadirse burocracia innecesaria a tareas de bajo riesgo.

---

## Criterios de Validación

Deben ser observables siempre que sea posible.

Ejemplo:

```text
- todos los inputs obligatorios fueron utilizados;
- el output cumple el formato requerido;
- no existen contradicciones críticas;
- las restricciones fueron respetadas;
- las acciones externas fueron confirmadas.
```

Evitar:

```text
"Verificar que esté bien."
```

---

## Manejo de Errores

Debe definir qué hacer ante errores previsibles.

Puede utilizar:

```text
Error
  │
  ▼
Identify Cause
  │
  ▼
Recoverable?
  │
 ┌┴──────────┐
 │           │
Sí          No
 │           │
 ▼           ▼
Correct     Escalate / Stop
```

---

## Reintentos

Si una operación admite reintentos debe indicarse cuando sea relevante.

No debe reintentarse indefinidamente.

Los límites pueden depender de:

- tipo de error;
- Integration;
- riesgo;
- costo;
- impacto.

---

## Fallos de Integration

Cuando una Integration falle:

1. no asumir éxito;
2. identificar si el fallo es recuperable;
3. reintentar únicamente cuando sea seguro;
4. utilizar alternativa autorizada cuando exista;
5. escalar si la ejecución no puede validarse.

---

## Aprobación Humana

Debe especificarse cuándo una acción requiere aprobación.

Ejemplos:

- publicación;
- eliminación;
- cambios sensibles;
- acciones externas de alto impacto;
- modificaciones irreversibles;
- acciones financieras;
- cambios de permisos.

La lógica general es:

```text
Prepare
  │
  ▼
Validate
  │
  ▼
Approval Required?
  │
 ┌┴─────────────┐
 │              │
No             Sí
 │              │
 ▼              ▼
Continue     Request Approval
                 │
            ┌────┴────┐
            │         │
         Approved   Rejected
            │         │
            ▼         ▼
         Continue    Stop
```

El silencio nunca constituye aprobación.

---

## Permisos

Un SOP nunca debe asumir permisos.

Antes de ejecutar una acción externa debe verificarse:

```text
Capability
+
Authorization
+
Scope
```

La existencia de una Integration no implica autorización para todas sus operaciones.

---

## Output

Debe definirse claramente qué produce el SOP.

Puede ser:

- documento;
- archivo;
- reporte;
- análisis;
- plan;
- registro;
- actualización;
- acción ejecutada;
- conjunto de tareas.

---

## Output Contract

Cuando aporte valor, puede definirse un contrato mínimo del output.

Ejemplo:

```yaml
output:
  type: content_calendar
  required_fields:
    - date
    - content_type
    - objective
    - concept
    - status
```

No es obligatorio utilizar YAML.

El objetivo es que el resultado pueda validarse.

---

## Definition of Done

Todo SOP debe incluir criterios claros de finalización.

Ejemplo:

```text
El procedimiento está terminado cuando:

- los inputs obligatorios fueron procesados;
- el output requerido fue generado;
- las validaciones obligatorias pasaron;
- las aprobaciones necesarias fueron obtenidas;
- las acciones externas requeridas fueron confirmadas;
- no existen bloqueos críticos pendientes.
```

Debe adaptarse al procedimiento.

---

## Completed ≠ Attempted

Debe mantenerse:

```text
Intentado
≠
Completado
```

Un SOP no puede marcarse completado si una acción crítica falló.

---

## Trazabilidad

Cuando sea necesaria puede registrarse:

```yaml
sop_id:
sop_version:
request_id:
agent:
started_at:
completed_at:
inputs:
decisions:
approvals:
integrations:
validation:
output:
status:
```

No todo SOP necesita registrar todos los campos.

---

## Escalamiento

Debe definir cuándo el procedimiento debe detenerse y escalar.

Ejemplos:

- falta información crítica;
- conflicto entre fuentes;
- falta autorización;
- riesgo superior al permitido;
- Integration crítica no disponible;
- resultado no validable;
- tarea fuera del alcance del Agent;
- contradicción con Governance.

---

## Destino del Escalamiento

Puede escalarse hacia:

```text
Orchestrator
Human
Governance
Specialized Agent
```

según el problema.

---

## Dependencias Operativas

Cuando un SOP dependa de otro proceso debe declararlo.

Ejemplo:

```text
SOP A
  │
  ▼
Output A
  │
  ▼
SOP B
```

Debe evitarse crear cadenas innecesariamente largas.

---

## SOPs Compuestos

Una tarea compleja puede utilizar varios SOPs.

Ejemplo:

```text
Research SOP
     │
     ▼
Content Planning SOP
     │
     ▼
Production Brief SOP
```

Cada SOP debe mantener una responsabilidad clara.

---

## Subprocedimientos

Un SOP puede referenciar otro SOP en lugar de duplicarlo.

Correcto:

```text
Ejecutar Research SOP cuando sea necesario.
```

Incorrecto:

copiar todo Research SOP dentro de otro procedimiento.

---

## Modificación durante Ejecución

Un Agent no debe modificar silenciosamente un SOP oficial durante una ejecución.

Si detecta una mejora:

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
```

El procedimiento actual continúa siendo la fuente vigente hasta que exista aprobación.

---

## Aprendizajes

Un aprendizaje puede convertirse en Candidate cuando:

- aparece repetidamente;
- mejora resultados;
- reduce errores;
- reduce costo;
- mejora seguridad;
- aumenta consistencia.

No todo aprendizaje necesita modificar un SOP.

---

## Mantenimiento

Los SOPs deben revisarse cuando:

- cambia una Integration;
- cambia un Framework crítico;
- cambia Governance;
- cambia un proceso real;
- aparecen errores repetidos;
- deja de representar la operación;
- existe una mejora validada.

---

## Revisión Periódica

`next_review` puede utilizarse cuando el procedimiento depende de elementos que pueden cambiar.

Ejemplos:

- APIs;
- plataformas;
- herramientas;
- políticas;
- procesos externos.

Los SOPs estables pueden necesitar revisiones menos frecuentes.

---

## Cambios Materiales

Son ejemplos de cambios materiales:

- agregar o eliminar pasos obligatorios;
- modificar criterios de decisión;
- cambiar permisos;
- cambiar responsable;
- cambiar Integration crítica;
- modificar validaciones;
- cambiar Definition of Done;
- cambiar outputs obligatorios.

Estos cambios deben respetar Governance.

---

## Cambios Editoriales

Pueden incluir:

- ortografía;
- formato;
- claridad;
- jerarquía Markdown;
- correcciones que no cambien significado.

Deben mantenerse trazables según Documentation Standards cuando corresponda.

---

## Deprecación

Cuando un SOP deje de utilizarse:

```yaml
status: Deprecated
```

Debe indicarse, cuando corresponda:

- motivo;
- reemplazo;
- fecha.

No debe eliminarse inmediatamente si su conservación aporta trazabilidad.

---

## Archivado

Un SOP puede pasar a:

```yaml
status: Archived
```

cuando solo deba conservarse por historia o auditoría.

---

## SOP Específico de Cliente

Cuando un cliente requiera un procedimiento realmente particular puede crearse dentro de su espacio.

Debe:

- respetar este estándar;
- mantenerse aislado;
- referenciar capacidades globales;
- evitar duplicar SOPs globales.

---

## Promoción de SOP Específico

Si un procedimiento específico demuestra valor general:

```text
Client SOP
   │
   ▼
Reusable Candidate
   │
   ▼
Review
   │
   ▼
Approved
   │
   ▼
Global SOP
```

La promoción nunca debe ser automática.

---

## Nomenclatura de Archivo

Formato recomendado:

```text
<PROCESS>_SOP.md
```

Ejemplos:

```text
RESEARCH_SOP.md
MONTHLY_CONTENT_PLANNING_SOP.md
CONTENT_PRODUCTION_SOP.md
REPORTING_SOP.md
```

Utilizar nombres descriptivos y estables.

---

## Tamaño del SOP

No existe una longitud obligatoria.

Debe contener únicamente lo necesario para ejecutar correctamente.

Debe evitarse:

```text
Más detalle
=
Más calidad
```

La regla correcta es:

```text
Sufficient Detail
+
Low Ambiguity
+
Low Redundancy
=
Useful SOP
```

---

## Nivel de Abstracción

Un SOP debe ubicarse entre:

```text
Demasiado abstracto
"Crear buen contenido."

        ↓

Nivel correcto
"Validar objetivo → recuperar contexto → aplicar Framework → producir → validar."

        ↓

Demasiado granular
"Hacer clic exactamente aquí..."
```

Las instrucciones específicas de herramientas deben permanecer principalmente en Integrations cuando corresponda.

---

## Modelo Agnóstico

Los SOPs deben ser interpretables por diferentes modelos de IA.

Evitar instrucciones como:

```text
"Claude debe..."
"ChatGPT debe..."
```

salvo que el SOP sea específicamente dependiente de ese proveedor.

Preferir:

```text
"El Agent debe..."
"Trinity AI debe..."
```

---

## SOP Template

La siguiente estructura funciona como base para nuevos SOPs.

Debe adaptarse al procedimiento y no copiarse mecánicamente cuando una sección no sea aplicable.

```text
---
id:
title:
module: SOPs
version: 1.0.0
status: Draft
owner: Trinity AI
created:
last_updated:
reviewed_by:
approved_by:
next_review:
dependencies: []
tags:
  - sop
---

# [SOP Title]

## Propósito

[Qué procedimiento define y qué problema resuelve.]

## Resultado Esperado

[Qué debe existir al finalizar.]

## Alcance

### Incluye

[...]

### No Incluye

[...]

## Cuándo Utilizar

[...]

## Cuándo No Utilizar

[...]

## Trigger

[...]

## Inputs

### Required

[...]

### Optional

[...]

### Conditional

[...]

## Precondiciones

[...]

## Responsable

[...]

## Capacidades Relacionadas

### Frameworks

[...]

### Knowledge

[...]

### Research

[...]

### Client Context

[...]

### Templates

[...]

### Assets

[...]

### Integrations

[...]

### Automations

[...]

## Procedimiento

### Etapa 1 — [...]

1. [...]
2. [...]

### Etapa 2 — [...]

1. [...]
2. [...]

## Puntos de Decisión

[...]

## Validaciones

### Antes de Ejecutar

[...]

### Durante la Ejecución

[...]

### Validación Final

[...]

## Manejo de Errores

[...]

## Aprobación Humana

[...]

## Output

[...]

## Definition of Done

[...]

## Trazabilidad

[...]

## Escalamiento

[...]

## Mantenimiento

[...]
```

---

## Checklist de Creación

Antes de mover un SOP de `Draft` a `Review` debe verificarse:

```text
[ ] Tiene propósito claro
[ ] Resuelve una tarea repetible
[ ] No duplica otro SOP
[ ] No duplica un Framework
[ ] No almacena Knowledge innecesario
[ ] No contiene Client Context globalizado
[ ] Define inputs
[ ] Define precondiciones cuando corresponda
[ ] Define procedimiento
[ ] Define decisiones relevantes
[ ] Define validaciones
[ ] Define manejo de errores cuando corresponde
[ ] Define aprobación cuando corresponde
[ ] Define output
[ ] Define Definition of Done
[ ] Declara dependencias reales
[ ] No contiene credenciales
[ ] Respeta Documentation Standards
[ ] Puede ser ejecutado por otro Agent o modelo
```

---

## Checklist de Ejecución

Antes de ejecutar:

```text
¿El SOP es aplicable?
        ↓
¿Está vigente?
        ↓
¿Tengo los inputs?
        ↓
¿Se cumplen las precondiciones?
        ↓
¿Tengo las capacidades necesarias?
        ↓
¿Tengo permisos?
        ↓
Execute
```

Antes de finalizar:

```text
¿Se completaron los pasos obligatorios?
        ↓
¿Pasaron las validaciones?
        ↓
¿Se obtuvieron las aprobaciones necesarias?
        ↓
¿Las acciones externas están confirmadas?
        ↓
¿Se produjo el output requerido?
        ↓
Definition of Done
```

---

## Antipatrones

Un SOP no debe:

- duplicar otro SOP;
- convertirse en Framework;
- almacenar Knowledge general;
- almacenar información específica de cliente sin necesidad;
- contener credenciales;
- asumir permisos;
- asumir aprobación;
- describir una Automation como si fuera el procedimiento;
- copiar documentación completa de Integrations;
- marcar acciones fallidas como completadas;
- ocultar errores;
- modificar fuentes oficiales durante la ejecución;
- crecer sin control;
- convertirse en una colección de recomendaciones ambiguas;
- depender de conocimiento implícito no documentado;
- obligar a utilizar capacidades innecesarias.

---

## Criterios de Calidad

Un SOP está correctamente diseñado cuando otra instancia autorizada de Trinity AI puede:

```text
Comprender
   ↓
Preparar
   ↓
Ejecutar
   ↓
Decidir
   ↓
Validar
   ↓
Finalizar
```

sin reconstruir el procedimiento desde cero.

---

## Criterios de Éxito

Este estándar funciona correctamente cuando los SOPs de Trinity AI:

- tienen estructura consistente;
- mantienen responsabilidades claras;
- pueden reutilizarse;
- pueden descubrirse;
- pueden ejecutarse;
- pueden validarse;
- pueden evolucionar;
- respetan permisos;
- escalan correctamente;
- se integran con Agents;
- utilizan Frameworks sin duplicarlos;
- utilizan Knowledge sin absorberlo;
- pueden soportar Automations futuras;
- mantienen Client Context aislado.

---

## Regla de Oro

> Un SOP debe decir exactamente lo necesario para ejecutar correctamente una tarea repetible y demostrar que terminó correctamente.

```text
Clear Entry
    +
Executable Procedure
    +
Controlled Decisions
    +
Validation
    +
Definition of Done
    =
Reliable SOP
```

El estándar existe para hacer que los procedimientos sean reutilizables.

No para convertir cada tarea en burocracia.