---
id: TRI-FWK-001
title: Framework Standard
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
  - 00_Foundation/14_AI_Behavior.md
  - 00_Foundation/15_Thinking_Framework.md
  - 00_Foundation/16_Decision_Framework.md
  - 04_Frameworks/README.md
tags:
  - frameworks
  - standards
  - methodology
  - reasoning
  - capabilities
---

# Trinity AI — Framework Standard

## Propósito

`FRAMEWORK_STANDARD.md` define el estándar para diseñar, documentar, revisar y mantener Frameworks dentro de Trinity AI.

Su función es garantizar que las metodologías reutilizables del sistema tengan una estructura consistente, sean interpretables por diferentes Agents y modelos de IA, y puedan integrarse correctamente con Knowledge, SOPs, Research y Client Context.

Este documento responde:

> ¿Cómo debe estar construido un Framework dentro de Trinity AI?

No define metodologías específicas.

Define el estándar que esas metodologías deben respetar.

---

## Objetivo

Todo Framework debe permitir responder claramente:

```text
¿Qué problema ayuda a resolver?
        ↓
¿Cuándo debe utilizarse?
        ↓
¿Qué información necesita?
        ↓
¿Qué principios orientan el análisis?
        ↓
¿Cómo estructura el problema?
        ↓
¿Qué etapas metodológicas utiliza?
        ↓
¿Qué criterios permiten decidir?
        ↓
¿Qué resultado metodológico produce?
        ↓
¿Cómo sabemos si fue aplicado correctamente?
```

Un Framework que no pueda responder estas preguntas puede estar insuficientemente definido o pertenecer a otro módulo.

---

## Principio Fundamental

> Un Framework debe proporcionar una metodología reutilizable para estructurar un tipo de problema sin convertirse en un procedimiento operativo.

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

El Framework debe aportar estructura.

No debe eliminar adaptación ni criterio.

---

## Alcance

Este estándar aplica a los Frameworks globales almacenados dentro de:

```text
04_Frameworks/
```

También debe utilizarse como referencia para Frameworks específicos almacenados dentro de:

```text
08_Clients/
└── Cliente/
    └── Frameworks/
```

Las extensiones específicas de cliente pueden adaptar una metodología global cuando exista una necesidad real.

No deben modificar automáticamente la fuente global.

---

## Cuándo Crear un Framework

Debe considerarse un Framework cuando exista:

```text
Problema recurrente
        +
Necesidad metodológica
        +
Estructura reutilizable
        +
Criterios identificables
        +
Valor entre ejecuciones
        =
Framework Candidate
```

Ejemplos de necesidades potenciales:

- estructurar una investigación;
- analizar performance;
- desarrollar estrategia creativa;
- planificar contenido;
- priorizar oportunidades;
- reutilizar contenido;
- estructurar reporting.

---

## Cuándo NO Crear un Framework

No debe crearse un Framework cuando la necesidad corresponde principalmente a:

```text
Procedimiento operativo
→ SOP

Conocimiento
→ Knowledge

Responsabilidad especializada
→ Agent

Información de cliente
→ Client Context

Acceso a herramientas
→ Integration

Proceso automatizado
→ Automation
```

Tampoco debe crearse cuando:

- el problema es único;
- no existe metodología reusable;
- una metodología existente ya cubre suficientemente la necesidad;
- agregar estructura no mejora el resultado.

---

## Reutilizar Antes de Crear

Antes de crear un Framework debe verificarse:

1. si existe uno equivalente;
2. si existe uno parcialmente aplicable;
3. si puede reutilizarse;
4. si puede adaptarse;
5. si puede combinarse con otro;
6. si realmente existe una nueva necesidad metodológica.

La secuencia recomendada es:

```text
Search Existing
      │
      ▼
Exact Match?
      │
 ┌────┴────┐
 │         │
Sí        No
 │         │
 ▼         ▼
Reuse   Partial Match?
             │
        ┌────┴────┐
        │         │
       Sí        No
        │         │
        ▼         ▼
      Adapt     Create Candidate
```

Crear debe ser la última opción.

---

## Estructura del Framework

Todo Framework debe contemplar, cuando sean aplicables:

```text
Front Matter
Título
Propósito
Problema que Resuelve
Resultado Esperado
Alcance
Cuándo Utilizar
Cuándo No Utilizar
Inputs
Knowledge Requerido
Research
Client Context
Principios
Variables o Dimensiones
Metodología
Etapas
Preguntas Guía
Criterios de Decisión
Manejo de Incertidumbre
Validación
Relación con SOPs
Agents Aplicables
Limitaciones
Escalamiento
Mantenimiento
```

No todas las secciones deben existir mecánicamente.

Una sección puede omitirse cuando no aporte valor.

---

## Front Matter

Todo Framework debe comenzar con Front Matter YAML válido.

Formato base:

```yaml
---
id: TRI-FWK-XXX
title:
module: Frameworks
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
  - framework
---
```

Debe respetar:

```text
00_Foundation/13_Documentation_Standards.md
```

---

## ID

Cada Framework debe tener un ID único.

Formato recomendado:

```text
TRI-FWK-XXX
```

Ejemplos:

```text
TRI-FWK-101
TRI-FWK-102
TRI-FWK-103
```

Un ID no debe reutilizarse para otra metodología.

---

## Title

Debe describir claramente la metodología.

Ejemplos:

```text
Research Framework
Content Planning Framework
Creative Strategy Framework
Performance Analysis Framework
```

Evitar:

```text
Framework Final
Framework New
Method 2
Updated Framework
```

---

## Module

Para Frameworks globales:

```yaml
module: Frameworks
```

Los Frameworks específicos de cliente deben seguir la convención documental correspondiente cuando sea definida.

---

## Version

Todo Framework debe tener versión.

Versión inicial recomendada:

```yaml
version: 1.0.0
```

Los cambios posteriores deben respetar Documentation Standards y Governance.

---

## Status

Todo Framework nuevo debe comenzar como:

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

Un Framework no debe declararse `Approved` simplemente porque fue documentado.

---

## Dependencies

Debe declarar únicamente dependencias documentales reales.

Ejemplo:

```yaml
dependencies:
  - CORE.md
  - 05_Knowledge/MARKETING.md
```

No debe agregarse como dependencia todo documento relacionado conceptualmente.

Esto reduce acoplamiento y riesgo de ciclos documentales.

---

## Título Principal

Después del Front Matter debe existir exactamente un H1.

Ejemplo:

```text
# Research Framework
```

Las secciones principales utilizan H2.

Las subsecciones deben respetar Documentation Standards.

---

## Propósito

Debe explicar:

- qué metodología define;
- para qué existe;
- qué mejora dentro de Trinity AI.

Debe ser metodológico, no operativo.

---

## Problema que Resuelve

Debe definir claramente la categoría de problema.

Ejemplo conceptual:

```text
Este Framework resuelve el problema de transformar una necesidad de información ambigua en una investigación estructurada, priorizada y respaldada por evidencia.
```

Debe evitar definiciones excesivamente amplias.

---

## Resultado Esperado

Debe indicar qué resultado metodológico produce.

Ejemplos:

- diagnóstico estructurado;
- estrategia;
- hipótesis priorizadas;
- mapa de oportunidades;
- análisis;
- recomendación;
- clasificación;
- estructura conceptual.

No debe confundirse necesariamente con el entregable operativo final.

---

## Alcance

Debe establecer qué problemas están dentro y fuera de la metodología.

Ejemplo:

```text
Incluye:
- análisis;
- estructuración;
- priorización.

No incluye:
- ejecución operativa;
- publicación;
- modificación de sistemas externos.
```

---

## Cuándo Utilizar

Debe establecer condiciones de aplicabilidad.

Ejemplo:

```text
Utilizar cuando:
- exista un problema de esta categoría;
- sea necesario comparar múltiples variables;
- se necesite consistencia metodológica;
- exista suficiente información mínima.
```

---

## Cuándo No Utilizar

Debe establecer cuándo la metodología agrega complejidad innecesaria o no corresponde.

Ejemplo:

```text
No utilizar cuando:
- la respuesta sea directa;
- la tarea sea puramente operativa;
- otro Framework sea claramente más apropiado.
```

---

## Inputs

Debe identificar la información necesaria para aplicar la metodología.

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

---

## Inputs Faltantes

Cuando falte información debe determinarse:

```text
Missing Input
     │
     ▼
Critical?
     │
 ┌───┴────┐
 │        │
No       Sí
 │        │
 ▼        ▼
Continue  Recover?
             │
        ┌────┴────┐
        │         │
       Sí        No
        │         │
        ▼         ▼
     Retrieve    Ask / Escalate
```

No debe inventarse información.

---

## Knowledge Requerido

Debe indicar qué conocimiento puede ser necesario para aplicar correctamente el Framework.

Ejemplo:

```text
Knowledge:
- marketing;
- consumer behavior;
- advertising;
- social media.
```

El Framework no debe copiar grandes cantidades de Knowledge.

Debe referenciarlo o recuperarlo selectivamente.

---

## Research

Debe indicar cuándo es necesario investigar.

Puede requerirse cuando:

- falta información;
- los datos pueden haber cambiado;
- existe incertidumbre;
- se necesita benchmark;
- una decisión depende de evidencia externa.

Los resultados de Research no deben incorporarse automáticamente al Framework permanente.

---

## Client Context

Cuando se aplica a un cliente puede necesitar:

- objetivos;
- audiencia;
- posicionamiento;
- productos;
- identidad;
- decisiones;
- performance;
- restricciones;
- historial relevante.

Debe recuperarse únicamente el contexto necesario.

---

## Principios

Los principios definen reglas metodológicas propias del Framework.

Deben:

- orientar análisis;
- reducir ambigüedad;
- mantenerse dentro de su dominio;
- evitar duplicar Foundation.

Ejemplo:

```text
Priorizar evidencia sobre intuición cuando exista evidencia suficiente.
```

---

## Variables y Dimensiones

Cuando el problema tenga múltiples dimensiones, el Framework puede identificarlas.

Ejemplo conceptual:

```text
Problem
  │
  ├── Audience
  ├── Offer
  ├── Channel
  ├── Message
  └── Performance
```

Las dimensiones deben representar factores relevantes para la metodología.

---

## Metodología

Esta sección constituye el núcleo del Framework.

Debe explicar cómo estructurar el problema.

Puede utilizar:

- etapas;
- matrices;
- modelos;
- dimensiones;
- criterios;
- preguntas;
- heurísticas;
- secuencias conceptuales.

Debe evitar convertirse en una lista operativa de acciones perteneciente a un SOP.

---

## Etapas Metodológicas

Cuando corresponda puede estructurarse así:

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

Las etapas representan fases de razonamiento.

---

## Etapas Condicionales

No todas las metodologías deben ser lineales.

Puede utilizarse:

```text
Core Stages
+
Conditional Stages
+
Optional Extensions
```

El Framework debe indicar qué elementos son esenciales cuando sea relevante.

---

## Preguntas Guía

Pueden utilizarse preguntas para orientar el análisis.

Ejemplo:

```text
¿Qué objetivo se busca?
¿Qué problema impide alcanzarlo?
¿Qué sabemos?
¿Qué estamos suponiendo?
¿Qué evidencia falta?
¿Qué variables tienen mayor impacto?
¿Qué alternativas existen?
```

Estas preguntas estructuran razonamiento.

No implican que deban formularse todas al usuario.

---

## Heurísticas

Un Framework puede incorporar heurísticas cuando sean útiles.

Las heurísticas deben:

- estar claramente identificadas;
- utilizarse como orientación;
- no presentarse como hechos universales;
- permitir excepción cuando exista mejor evidencia.

---

## Matrices

Puede utilizar matrices cuando ayuden a comparar variables.

Ejemplo:

```text
                Impact
             Low      High

Effort Low   Quick    Priority
             Win

Effort High  Avoid    Strategic
                      Bet
```

Una matriz debe tener criterios suficientemente claros.

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

No todos los Frameworks necesitan los mismos criterios.

---

## Decisiones de Alto Impacto

Cuando una decisión tenga impacto significativo debe utilizarse el sistema correspondiente de Foundation:

```text
00_Foundation/16_Decision_Framework.md
```

El Framework específico no debe duplicarlo.

---

## Priorización

Cuando existan múltiples alternativas debe indicarse cómo priorizar.

Puede utilizar:

- scoring;
- ranking;
- matriz;
- evidencia;
- impacto;
- esfuerzo;
- riesgo;
- alineación estratégica.

La técnica debe ser proporcional al problema.

---

## Scoring

Si se utiliza puntuación debe definirse:

- qué variables se puntúan;
- escala;
- significado;
- pesos cuando existan;
- interpretación.

Debe evitarse falsa precisión.

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

La metodología no debe tratar hipótesis como hechos.

---

## Manejo de Incertidumbre

Debe respetarse:

```text
Known
Inferred
Unknown
Candidate
```

Cuando una incertidumbre pueda cambiar materialmente el resultado debe:

- investigarse;
- declararse;
- validarse;
- o escalarse.

---

## Supuestos

Cuando sea necesario trabajar con supuestos deben ser explícitos.

Ejemplo:

```text
Assumption:
El segmento prioriza precio sobre personalización.

Status:
Unvalidated.
```

Los supuestos críticos deben validarse cuando sea posible.

---

## Contradicciones

Cuando exista evidencia contradictoria:

```text
Conflicting Evidence
        │
        ▼
Evaluate Sources
        │
        ▼
Material Conflict?
        │
   ┌────┴────┐
   │         │
  No        Sí
   │         │
   ▼         ▼
Continue   Research / Escalate
```

No debe ocultarse una contradicción relevante.

---

## Adaptación al Contexto

Un Framework debe poder adaptarse sin perder su propósito.

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

La adaptación durante una ejecución no modifica automáticamente la fuente oficial.

---

## Uso de Múltiples Frameworks

Pueden combinarse cuando resuelvan dimensiones diferentes.

Ejemplo:

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

Debe evitarse combinar Frameworks redundantes.

---

## Orden de Aplicación

Cuando varios Frameworks dependan entre sí debe declararse el orden lógico.

```text
Framework A
    │
    ▼
Intermediate Output
    │
    ▼
Framework B
```

No es necesario crear un Framework nuevo solo para unirlos.

---

## Relación con SOPs

Debe identificarse qué SOPs pueden utilizar el Framework cuando sea relevante.

Ejemplo:

```text
Framework:
Research Framework

Related SOP:
Research SOP
```

El Framework define metodología.

El SOP define ejecución.

---

## Agents Aplicables

Debe indicarse qué Agents pueden utilizar el Framework cuando sea útil para descubrimiento.

Ejemplo:

```text
Applicable Agents:
- Research Agent
- Strategy Agent
```

Esto no significa que el Framework pertenezca exclusivamente a esos Agents.

---

## Resultado Metodológico

Debe ser posible identificar qué produce la aplicación.

Ejemplo:

```text
Inputs
   │
   ▼
Framework
   │
   ▼
Structured Diagnosis
```

Ese resultado puede convertirse después en input de un SOP, Agent u otro Framework.

---

## Validación

Todo Framework debe definir cómo determinar si fue aplicado correctamente.

Puede evaluarse:

- cobertura;
- consistencia;
- evidencia;
- relevancia;
- alineación;
- claridad;
- priorización;
- utilidad.

---

## Validación Metodológica

Ejemplo:

```text
[ ] El objetivo fue identificado.
[ ] Las variables relevantes fueron consideradas.
[ ] Los supuestos están diferenciados de hechos.
[ ] La evidencia relevante fue incorporada.
[ ] La priorización utiliza criterios explícitos.
[ ] La recomendación deriva del análisis.
```

Debe adaptarse a cada Framework.

---

## Validación ≠ SOP

La validación de un Framework comprueba la calidad metodológica.

La validación de un SOP comprueba la correcta ejecución del procedimiento.

Ambas pueden coexistir.

---

## Limitaciones

Todo Framework debería declarar limitaciones relevantes.

Ejemplos:

- depende de calidad de datos;
- no sustituye Research;
- no predice resultados;
- requiere contexto suficiente;
- no aplica a determinados escenarios.

Esto reduce sobreuso.

---

## Escalamiento

Debe indicar cuándo la metodología no puede resolver correctamente el problema.

Ejemplos:

- información crítica inexistente;
- contradicciones materiales;
- problema fuera de alcance;
- decisión de riesgo alto;
- necesidad de especialidad diferente.

Puede escalar hacia:

```text
Research
Specialized Agent
Orchestrator
Human
Governance
```

según corresponda.

---

## Framework Candidate

Un nuevo Framework comienza como:

```yaml
status: Draft
```

Debe validarse antes de convertirse en metodología oficial.

---

## Validación de un Candidate

Antes de promoverlo debe evaluarse:

```text
¿Resuelve un problema real?
        ↓
¿Es reutilizable?
        ↓
¿Es diferente de Frameworks existentes?
        ↓
¿Mejora consistencia o calidad?
        ↓
¿Puede aplicarse en más de una situación?
        ↓
¿Puede validarse?
        ↓
Review Candidate
```

---

## Estados

Los Frameworks utilizan:

```text
Draft
Review
Approved
Deprecated
Archived
```

La promoción debe respetar Governance.

---

## Evolución

Los Frameworks deben evolucionar mediante evidencia y aprendizaje.

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

No deben modificarse silenciosamente durante una ejecución.

---

## Cambios Materiales

Ejemplos:

- cambiar metodología;
- agregar o eliminar etapas centrales;
- modificar criterios;
- cambiar sistema de priorización;
- modificar inputs obligatorios;
- cambiar resultado esperado;
- ampliar sustancialmente alcance.

Estos cambios deben respetar Governance.

---

## Cambios Editoriales

Ejemplos:

- ortografía;
- formato;
- claridad;
- jerarquía Markdown;
- redacción sin cambio conceptual.

Deben manejarse según Documentation Standards.

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

## Archivado

Puede utilizarse:

```yaml
status: Archived
```

cuando el Framework se conserva únicamente por trazabilidad.

---

## Frameworks de Cliente

Un Framework específico de cliente debe utilizarse únicamente cuando exista una diferencia metodológica real.

No debe crearse simplemente porque:

- cambió el branding;
- cambió la audiencia;
- cambió el producto;
- cambió una campaña.

Esos elementos normalmente pertenecen a Client Context.

---

## Promoción a Global

Un Framework específico puede proponerse como global cuando:

```text
Repeated Value
+
Cross-client Applicability
+
Validated Methodology
=
Reusable Candidate
```

Debe pasar por Review y Governance.

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
REPORTING_FRAMEWORK.md
```

---

## Organización

Inicialmente:

```text
04_Frameworks/
├── README.md
└── FRAMEWORK_STANDARD.md
```

Solo cuando exista suficiente volumen deben crearse subcategorías.

No crear arquitectura vacía anticipadamente.

---

## Modelo Agnóstico

Un Framework debe poder utilizarse con diferentes modelos de IA.

Debe evitar dependencias innecesarias hacia un proveedor específico.

Preferir:

```text
Trinity AI debe...
El Agent debe...
```

sobre:

```text
Claude debe...
ChatGPT debe...
Gemini debe...
```

salvo que la metodología sea específicamente dependiente de una tecnología.

---

## Tamaño

No existe una longitud obligatoria.

Debe existir suficiente detalle para:

- comprender;
- aplicar;
- adaptar;
- validar.

Debe evitarse documentación excesiva sin utilidad metodológica.

---

## Nivel Correcto de Abstracción

Demasiado abstracto:

```text
"Analizar bien el problema."
```

Nivel correcto:

```text
"Definir objetivo → identificar variables → evaluar evidencia → comparar alternativas → priorizar."
```

Demasiado operativo:

```text
"Abrir herramienta → hacer clic → copiar resultado..."
```

El último caso normalmente pertenece a SOP o Integration.

---

## Template Base

La siguiente estructura puede utilizarse como base para nuevos Frameworks:

```text
---
id:
title:
module: Frameworks
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
  - framework
---

# [Framework Title]

## Propósito

[...]

## Problema que Resuelve

[...]

## Resultado Esperado

[...]

## Alcance

### Incluye

[...]

### No Incluye

[...]

## Cuándo Utilizar

[...]

## Cuándo No Utilizar

[...]

## Inputs

### Required

[...]

### Optional

[...]

### Conditional

[...]

## Knowledge Requerido

[...]

## Research

[...]

## Client Context

[...]

## Principios

[...]

## Variables o Dimensiones

[...]

## Metodología

### Etapa 1 — [...]

[...]

### Etapa 2 — [...]

[...]

### Etapa 3 — [...]

[...]

## Preguntas Guía

[...]

## Criterios de Decisión

[...]

## Priorización

[...]

## Manejo de Incertidumbre

[...]

## Resultado Metodológico

[...]

## Validación

[...]

## Relación con SOPs

[...]

## Agents Aplicables

[...]

## Limitaciones

[...]

## Escalamiento

[...]

## Mantenimiento

[...]
```

La plantilla debe adaptarse.

No todas las secciones son obligatorias cuando no aplican.

---

## Checklist de Creación

Antes de mover un Framework de `Draft` a `Review`:

```text
[ ] Resuelve un problema claramente definido
[ ] Existe valor reutilizable
[ ] No duplica otro Framework
[ ] No pertenece realmente a un SOP
[ ] No almacena Knowledge innecesariamente
[ ] No contiene Client Context globalizado
[ ] Define cuándo utilizarse
[ ] Define cuándo no utilizarse
[ ] Define inputs
[ ] Define principios cuando corresponde
[ ] Define metodología
[ ] Define criterios cuando corresponde
[ ] Maneja incertidumbre relevante
[ ] Define resultado esperado
[ ] Define validación
[ ] Declara limitaciones
[ ] Declara dependencias reales
[ ] Respeta Documentation Standards
[ ] Es interpretable por diferentes Agents/modelos
```

---

## Checklist de Aplicación

Antes de aplicar:

```text
¿Necesito metodología?
        ↓
¿Este Framework resuelve el problema?
        ↓
¿Está vigente?
        ↓
¿Tengo inputs?
        ↓
¿Necesito Knowledge?
        ↓
¿Necesito Research?
        ↓
¿Necesito Client Context?
        ↓
Apply
```

Antes de finalizar:

```text
¿Se aplicaron las dimensiones relevantes?
        ↓
¿Se distinguieron hechos y supuestos?
        ↓
¿La evidencia es suficiente?
        ↓
¿La priorización es coherente?
        ↓
¿El resultado deriva del análisis?
        ↓
Validate
```

---

## Antipatrones

Un Framework no debe:

- convertirse en un procedimiento operativo;
- duplicar un SOP;
- duplicar Knowledge;
- almacenar Client Context;
- asumir información inexistente;
- contener credenciales;
- definir permisos;
- ejecutar Integrations;
- ejecutar Automations;
- definir Agents completos;
- utilizar scoring sin criterios;
- crear falsa precisión;
- ignorar incertidumbre;
- ocultar evidencia contradictoria;
- convertirse en global automáticamente;
- crecer sin necesidad metodológica;
- utilizarse por obligación.

---

## Criterios de Calidad

Un Framework correctamente diseñado debe ser:

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
+
Maintainable
```

Debe mejorar la calidad de resolución del problema sin reemplazar criterio contextual.

---

## Criterios de Éxito

Este estándar funciona correctamente cuando los Frameworks:

- resuelven categorías claras de problemas;
- pueden reutilizarse entre Agents;
- pueden aplicarse entre clientes;
- permanecen separados de SOPs;
- utilizan Knowledge sin duplicarlo;
- incorporan Research cuando corresponde;
- manejan incertidumbre;
- producen resultados estructurados;
- pueden validarse;
- pueden evolucionar de forma controlada;
- son suficientemente portables entre modelos.

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

Frameworks existe para que Trinity AI no tenga que inventar nuevamente cómo pensar problemas que ya aprendió a estructurar.