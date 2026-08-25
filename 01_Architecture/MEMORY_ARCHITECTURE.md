---
id: TRI-ARCH-005
title: Memory Architecture
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
  - 00_Foundation/13_Documentation_Standards.md
  - 00_Foundation/14_AI_Behavior.md
  - 00_Foundation/15_Thinking_Framework.md
tags:
  - architecture
  - memory
  - context
  - retrieval
  - knowledge
  - governance
---

# Trinity AI - Memory Architecture

# Propósito

Memory Architecture define cómo Trinity AI conserva, clasifica, recupera, valida y reutiliza información a lo largo del tiempo.

Su objetivo es evitar dos problemas:

```text
Olvidar información útil
        +
Recordar como verdad información no validada
```

La memoria debe permitir:

- conservar conocimiento relevante;
- recuperar contexto;
- reducir repetición;
- preservar decisiones;
- mantener coherencia;
- separar información temporal de permanente;
- diferenciar evidencia de conocimiento;
- evitar contaminación entre clientes;
- promover aprendizajes de forma controlada.

Trinity AI no debe intentar recordar todo.

Debe conservar lo correcto y recuperar únicamente lo necesario.

---

# Objetivo

La arquitectura de memoria debe permitir que Trinity AI responda:

```text
¿Qué información existe?
¿Dónde vive?
¿Qué autoridad tiene?
¿Está vigente?
¿Para quién aplica?
¿Puede reutilizarse?
¿Puede modificarse?
¿Necesita validación?
```

---

# Principio Fundamental

> Capturar información no significa convertirla en memoria permanente.

El flujo general es:

```text
Capture
   │
   ▼
Classify
   │
   ▼
Evaluate
   │
   ▼
Validate
when required
   │
   ▼
Store
   │
   ▼
Retrieve
   │
   ▼
Update / Deprecate
when required
```

No toda información debe atravesar todo el flujo.

---

# Memoria como sistema de fuentes

La memoria de Trinity AI no debe entenderse como una única base de datos conceptual.

Está distribuida entre distintas fuentes con responsabilidades específicas.

```text
Core Sources
Knowledge
Frameworks
SOPs
Client Context
Research
Decisions
Session Context
Candidates
```

Cada fuente tiene diferente:

- alcance;
- autoridad;
- vigencia;
- persistencia;
- reutilización.

---

# Tipos de Memoria

Trinity AI distingue principalmente:

```text
Core Memory
Global Knowledge
Framework Memory
SOP Memory
Client Context
Research Memory
Decision Memory
Session Context
Candidate Memory
```

---

# Core Memory

Contiene reglas y estructura fundamentales del sistema.

Incluye principalmente:

```text
CORE.md
00_Foundation/
01_Architecture/
13_Governance/
```

Core Memory posee alta autoridad dentro de su alcance.

No debe cargarse completamente en cada solicitud.

Solo deben recuperarse los componentes relevantes.

---

# Global Knowledge

Contiene conocimiento global validado y reutilizable.

Vive principalmente en:

```text
05_Knowledge/
```

Ejemplos:

- marketing;
- branding;
- Meta Ads;
- contenido;
- SEO;
- producción audiovisual;
- inteligencia artificial;
- automatización.

Responde:

> ¿Qué necesita saber Trinity AI?

---

# Framework Memory

Contiene metodologías reutilizables.

Vive principalmente en:

```text
04_Frameworks/
```

Responde:

> ¿Cómo debería abordar Trinity AI este tipo de problema?

Frameworks son memoria metodológica.

No son procedimientos.

---

# SOP Memory

Contiene procedimientos operativos reutilizables.

Vive principalmente en:

```text
02_SOPs/
```

Responde:

> ¿Cómo debe ejecutarse esta tarea?

SOPs representan memoria procedimental.

---

# Client Context

Contiene información específica de clientes y proyectos.

Vive en:

```text
08_Clients/
```

Puede incluir:

- identidad;
- objetivos;
- productos;
- servicios;
- audiencia;
- decisiones;
- estrategias;
- Research;
- Assets;
- Frameworks específicos;
- historial relevante.

Client Context debe mantenerse aislado.

```text
Client A Context
≠
Client B Context
```

---

# Research Memory

Contiene investigación, evidencia y referencias.

Vive principalmente en:

```text
12_Research/
```

Puede incluir:

- benchmarking;
- tendencias;
- competencia;
- análisis;
- fuentes;
- evidencia;
- datos temporales.

Research no constituye automáticamente Knowledge.

---

# Decision Memory

Conserva decisiones relevantes cuando existe valor futuro o necesidad de trazabilidad.

Debe permitir conocer, cuando corresponda:

```text
qué se decidió
por qué
cuándo
qué alternativas existían
qué evidencia se utilizó
qué riesgo se evaluó
quién aprobó
qué reemplazó
```

No todas las decisiones requieren almacenamiento permanente.

---

# Session Context

Contiene información temporal utilizada durante la interacción actual.

Puede incluir:

- mensajes recientes;
- instrucciones temporales;
- archivos;
- hipótesis;
- contexto operativo;
- información todavía no validada.

Session Context no constituye memoria permanente.

---

# Candidate Memory

Contiene aprendizajes potencialmente reutilizables pendientes de revisión.

Puede incluir:

```text
Knowledge Candidate
Framework Candidate
SOP Candidate
Template Candidate
Automation Candidate
Client Learning Candidate
```

Candidate representa una condición conceptual.

No constituye una fuente oficial.

---

# Diferencia entre memoria y documentación

No toda memoria tiene que convertirse inmediatamente en un documento nuevo.

Puede existir temporalmente como:

- Session Context;
- Candidate;
- Research;
- Client Context;

hasta que exista suficiente valor para documentarla formalmente.

---

# Persistencia

Los diferentes tipos de memoria poseen diferente nivel de persistencia.

```text
Session Context
→ temporal

Research
→ persistente pero sensible a vigencia

Client Context
→ persistente dentro de cliente

Knowledge
→ persistente global

Core Memory
→ altamente persistente

Candidate
→ temporal hasta decisión
```

---

# Autoridad

La persistencia no determina autoridad.

Ejemplo:

```text
Research reciente
≠
regla superior

Client Context
≠
Knowledge global

Candidate
≠
Approved Source
```

---

# Recuperación Selectiva

Trinity AI no debe consultar toda la memoria antes de cada respuesta.

Debe seguir:

```text
Solicitud
    │
    ▼
Identificar necesidad
    │
    ▼
Identificar fuentes potenciales
    │
    ▼
Evaluar relevancia
    │
    ▼
Recuperar mínimo contexto suficiente
```

---

# Principio de Relevancia

Antes de recuperar información debe preguntarse:

> ¿Esta información puede afectar materialmente la solución actual?

Si no, probablemente no debe cargarse.

---

# Flujo de Recuperación

```text
Request
   │
   ▼
Need Identification
   │
   ▼
Source Selection
   │
   ▼
Authority Check
   │
   ▼
Freshness Check
when relevant
   │
   ▼
Retrieve
   │
   ▼
Use
```

---

# Fuentes potenciales

Según la tarea pueden recuperarse:

```text
CORE
Foundation
Architecture
Knowledge
Frameworks
SOPs
Client Context
Research
Decisions
Session Context
Templates
Examples
Assets
```

No existe una obligación de consultar todas.

---

# Prioridad de fuentes

Cuando múltiples fuentes sean relevantes debe evaluarse:

```text
Authority
+
Status
+
Scope
+
Specificity
+
Freshness
```

La prioridad no debe basarse únicamente en recencia.

---

# Autoridad documental

Los documentos pueden tener estados:

```text
Draft
Review
Approved
Deprecated
Archived
```

En producción debe priorizarse `Approved`.

Durante desarrollo pueden utilizarse `Draft` y `Review` como referencia controlada.

---

# Especificidad

Una fuente específica puede complementar una fuente global.

Ejemplo:

```text
Global Knowledge:
los CTAs deben orientar acción

Client Context:
Líneas Rectas prioriza consultas por WhatsApp
```

La información específica complementa.

No modifica automáticamente la regla global.

---

# Vigencia

No toda memoria envejece igual.

```text
CORE
→ baja sensibilidad temporal

Principios de marketing
→ baja / media

Client Pricing
→ alta

Research de tendencias
→ alta

Características de plataformas
→ alta
```

Cuando la vigencia pueda cambiar la decisión, debe verificarse.

---

# Recuperación por Cliente

Cuando una solicitud pertenece a un cliente debe identificarse primero qué cliente está involucrado.

```text
Request
   │
   ▼
Identify Client
   │
   ▼
Recover Relevant Client Context
   │
   ▼
Combine with Global Capabilities
```

Debe evitarse mezclar información entre clientes.

---

# Aislamiento entre clientes

Debe impedirse:

```text
Client A
   │
   ▼
Context
   │
   ▼
Agent trabajando para Client B
```

salvo que esa información se haya convertido correctamente en Knowledge global.

---

# Recuperación de decisiones

Las decisiones anteriores deben recuperarse cuando puedan afectar:

- coherencia;
- estrategia;
- permisos;
- alcance;
- arquitectura;
- Client Context;
- trabajo actual.

No debe cargarse historial completo si no es necesario.

---

# Prevención de Amnesia

Antes de pedir información nuevamente, Trinity AI debe comprobar si ya existe.

Puede buscar:

- Session Context;
- Client Context;
- Knowledge;
- Decisions;
- Research;
- documentación relacionada.

```text
Need Information
      │
      ▼
Search Existing Sources
      │
   ┌──┴───┐
   │      │
Found   Not Found
   │      │
   ▼      ▼
Reuse   Ask / Research
```

---

# Información contradictoria

Si encuentra información incompatible debe:

1. identificar fuentes;
2. evaluar autoridad;
3. evaluar vigencia;
4. evaluar especificidad;
5. resolver cuando sea posible;
6. escalar cuando no pueda.

No debe seleccionar silenciosamente la información más conveniente.

---

# Incertidumbre

Trinity AI debe distinguir:

```text
Known
Inferred
Unknown
Candidate
```

---

# Known

Información suficientemente respaldada por una fuente disponible.

---

# Inferred

Conclusión razonable derivada de fuentes conocidas.

No debe presentarse como hecho confirmado cuando la diferencia sea relevante.

---

# Unknown

Información que Trinity AI no posee.

No debe transformarse silenciosamente en Known mediante suposición.

---

# Candidate

Información potencialmente reutilizable todavía no aprobada como memoria permanente.

---

# Capture

Trinity AI puede detectar nueva información durante:

- conversaciones;
- Research;
- Agent outputs;
- resultados de Automations;
- decisiones;
- ejecución con clientes;
- auditorías.

Detectar información no obliga a almacenarla.

---

# Evaluación de Valor Futuro

Antes de persistir debe evaluarse:

```text
¿Tiene valor futuro?
   │
   ├── No → no persistir
   └── Sí
        │
        ▼
     Clasificar
```

Valor futuro puede significar:

- evitar repetición;
- mejorar consistencia;
- preservar una decisión;
- reutilizar conocimiento;
- reutilizar metodología;
- mantener Client Context;
- registrar evidencia.

---

# Clasificación de Nueva Información

La información puede clasificarse como:

```text
Knowledge
Framework
SOP
Client Context
Research
Decision
Template
Example
Candidate
```

Debe elegirse según responsabilidad.

---

# Nueva información global

Cuando exista conocimiento potencialmente reutilizable para múltiples proyectos debe tratarse como Candidate antes de convertirse en Knowledge oficial.

```text
Learning
   │
   ▼
Knowledge Candidate
   │
   ▼
Review
   │
   ▼
Validation
   │
   ▼
Approval
   │
   ▼
05_Knowledge
```

---

# Research → Knowledge

Research debe permanecer separado de Knowledge.

```text
Research
   │
   ▼
Finding
   │
   ▼
Knowledge Candidate
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

Encontrar información no significa convertirla automáticamente en verdad permanente.

---

# Client → Global

Los aprendizajes obtenidos trabajando con un cliente permanecen inicialmente dentro de Client Context.

Si poseen valor global:

```text
Client Learning
      │
      ▼
Reusable Candidate
      │
      ▼
Review
      │
      ▼
Validation
      │
      ▼
Approval
      │
      ▼
Global Source
```

La promoción nunca debe ser automática.

---

# Session → Permanent

Información de sesión puede convertirse en memoria persistente únicamente cuando exista valor.

```text
Session Context
      │
      ▼
Potential Learning
      │
      ▼
Candidate
      │
      ▼
Review
      │
      ▼
Persistent Source
```

Las conversaciones no deben guardarse automáticamente como memoria oficial.

---

# Candidate Lifecycle

```text
Candidate
   │
   ▼
Review
   │
   ├── Reject
   ├── Needs Changes
   └── Validate
          │
          ▼
       Approval
          │
          ▼
     Official Source
```

La promoción debe respetar Governance.

---

# Rejected Candidate

Un Candidate rechazado no debe seguir utilizándose como conocimiento oficial.

Puede:

- eliminarse;
- conservarse como Research;
- mantenerse como historial cuando exista motivo.

---

# Memoria permanente

Una fuente puede considerarse memoria permanente cuando:

- tiene responsabilidad clara;
- está correctamente clasificada;
- existe valor futuro;
- cumple Documentation Standards;
- posee estado apropiado;
- fue validada cuando corresponde.

---

# Actualización de memoria

Una fuente existente puede necesitar actualización.

Debe evitarse sobrescribir silenciosamente reglas importantes.

El flujo recomendado es:

```text
Existing Source
      │
      ▼
Change Detected
      │
      ▼
Evaluate Impact
      │
      ▼
Update Draft
      │
      ▼
Review
      │
      ▼
Approval
      │
      ▼
New Version
```

---

# Deprecación

Cuando una fuente deja de ser recomendada puede marcarse:

```text
Deprecated
```

Debe mantenerse referencia al reemplazo cuando exista.

---

# Archived

Una fuente puede archivarse cuando ya no tiene uso operativo pero conserva valor histórico.

No debe recuperarse por defecto para nuevas decisiones.

---

# Versiones

El historial de versiones debe mantenerse principalmente mediante Git y metadata documental.

No deben proliferar copias como:

```text
knowledge_v1.md
knowledge_v2.md
knowledge_final.md
```

---

# Duplicación

Antes de almacenar debe buscarse si ya existe una fuente equivalente.

```text
New Information
      │
      ▼
Search Equivalent
      │
   ┌──┴───┐
   │      │
Exists   New
   │      │
   ▼      ▼
Update   Evaluate Creation
```

---

# Fuente única de verdad

Cada responsabilidad debería poseer una fuente principal.

Otros componentes deben referenciarla.

Debe evitarse mantener la misma regla en múltiples archivos independientes.

---

# Duplicación aceptable

Puede existir repetición breve para contexto local.

Pero debe quedar claro cuál es la fuente oficial.

---

# Decision Memory

Una decisión debe persistirse cuando:

- tiene impacto futuro;
- será reutilizada;
- evita repetir discusión;
- afecta arquitectura;
- afecta estrategia;
- tiene valor de trazabilidad.

No toda decisión trivial necesita memoria.

---

# Estructura de Decision Memory

Cuando corresponda puede incluir:

```yaml
decision:
context:
alternatives:
reason:
evidence:
risk:
approved_by:
date:
replaces:
```

---

# Client Decision

Las decisiones específicas de clientes deben vivir dentro del Client Context correspondiente.

No deben convertirse automáticamente en reglas globales.

---

# Global Decision

Las decisiones arquitectónicas o globales pueden registrarse mediante mecanismos definidos por Governance.

---

# Memoria de errores

Los errores no deben convertirse automáticamente en Knowledge.

Puede existir valor en conservar:

- causa;
- impacto;
- corrección;
- prevención;

cuando el aprendizaje sea reutilizable.

Debe pasar por Candidate.

---

# Memoria de resultados

Los outputs rutinarios no necesitan almacenamiento permanente.

Puede ser útil conservar resultados cuando:

- tengan valor futuro;
- sean evidencia;
- formen parte de Client History;
- alimenten decisiones;
- sean necesarios para trazabilidad.

---

# Assets

Assets son recursos persistentes pero no deben confundirse con Knowledge.

Ejemplos:

- imágenes;
- logos;
- PDFs;
- archivos visuales.

Su metadata puede ayudar a recuperación.

---

# Templates

Templates son estructuras persistentes reutilizables.

No contienen necesariamente conocimiento.

Deben recuperarse cuando el formato sea relevante.

---

# Examples

Examples son implementaciones de referencia.

No deben tratarse como reglas.

```text
Example
≠
Official Rule
```

---

# Memory Retrieval y Agents

Un Agent debe recuperar únicamente memoria relevante para su tarea.

No debe recibir automáticamente:

- todo Knowledge;
- todo Client Context;
- todos los Decisions;
- todo Research.

---

# Memory Retrieval y Orchestrator

El Orchestrator puede identificar qué contexto necesita cada Agent.

Puede preparar Context Packages.

No debe cargar toda la memoria para después distribuirla.

---

# Memory Retrieval y Data Flow

`DATA_FLOW.md` define cómo circula la información.

Memory Architecture define:

- dónde vive;
- cómo se clasifica;
- qué autoridad posee;
- cómo se recupera.

```text
Memory Architecture
→ almacenamiento y clasificación

Data Flow
→ circulación
```

---

# Memory y Request Lifecycle

`REQUEST_LIFECYCLE.md` define estado de solicitudes.

Memory Architecture define qué información puede persistir más allá del lifecycle.

Una solicitud `Completed` no implica automáticamente persistencia de todo su contenido.

---

# Memory y Agent Interaction

Los handoffs entre Agents utilizan contexto temporal.

Ese contexto no se convierte automáticamente en memoria permanente.

---

# Seguridad

La memoria debe seguir principio de mínimo acceso.

No toda información almacenada debe ser accesible a todos los componentes.

---

# Credenciales

Nunca deben almacenarse como memoria documental normal:

- passwords;
- API keys;
- tokens;
- private keys;
- secrets.

Deben utilizar mecanismos seguros externos.

---

# Datos sensibles

Los datos sensibles deben almacenarse únicamente cuando:

- sean necesarios;
- exista autorización;
- exista un mecanismo seguro;
- exista una responsabilidad clara.

---

# Aislamiento

La arquitectura debe impedir contaminación entre:

- clientes;
- contextos;
- permisos;
- proyectos.

---

# Trazabilidad

Las fuentes importantes pueden conservar:

- origen;
- fecha;
- estado;
- versión;
- owner;
- evidencia;
- aprobación;
- dependencias;
- reemplazos.

La trazabilidad debe ser proporcional.

---

# Indexación

A medida que Trinity AI crezca, la recuperación puede apoyarse en índices.

Estos índices pueden incluir:

- IDs;
- tags;
- módulos;
- clientes;
- topics;
- status;
- fechas;
- dependencias.

Un índice ayuda a encontrar información.

No se convierte en segunda fuente de verdad.

---

# Búsqueda

La búsqueda debe favorecer:

```text
Relevance
+
Authority
+
Specificity
+
Freshness
```

No solo coincidencia textual.

---

# Recuperación semántica

Puede utilizarse recuperación semántica cuando mejore discovery.

Debe verificarse la fuente original antes de utilizar información crítica.

---

# Cache

Puede utilizarse cache temporal para reducir lecturas repetitivas.

Cache no debe convertirse en fuente oficial.

Debe respetar vigencia.

---

# Invalidación de Cache

Cuando cambie una fuente crítica debe evitarse continuar usando una versión antigua almacenada temporalmente.

La política concreta dependerá de la implementación.

---

# Memory Candidates automáticos

Automations pueden detectar Candidates.

No deben aprobarlos automáticamente.

```text
Automation
   │
   ▼
Candidate
   │
   ▼
Review
```

---

# Integrations y memoria

Una Integration puede servir para almacenar o recuperar información.

Ejemplos:

- Notion;
- Google Drive;
- GitHub.

La herramienta donde vive información no determina automáticamente qué tipo de memoria representa.

---

# Source of Truth vs Storage Tool

Debe diferenciarse:

```text
Conceptual Source
→ Knowledge / Client Context / Research

Storage Tool
→ GitHub / Notion / Drive
```

El almacenamiento físico puede cambiar.

La responsabilidad conceptual debe permanecer estable.

---

# Migración

Si una fuente cambia de herramienta de almacenamiento, Trinity AI debe preservar:

- identidad;
- metadata;
- autoridad;
- relaciones;
- trazabilidad.

La migración de storage no debe cambiar significado.

---

# Lifecycle de Memoria

Puede representarse:

```text
Capture
   │
   ▼
Classify
   │
   ▼
Temporary / Candidate / Persistent
   │
   ▼
Validate
when required
   │
   ▼
Use
   │
   ▼
Update
   │
   ▼
Deprecate / Archive
```

---

# Memory Health

La memoria puede degradarse por:

- duplicación;
- obsolescencia;
- contradicciones;
- falta de metadata;
- exceso de Candidates;
- información sin owner;
- Client Context contaminado;
- referencias rotas.

---

# Auditoría de Memoria

Una auditoría puede revisar:

```text
Duplicate Sources
Stale Knowledge
Broken References
Unreviewed Candidates
Mixed Client Context
Missing Metadata
Conflicting Decisions
Orphaned Documents
```

---

# Limpieza

La limpieza de memoria debe eliminar o reclasificar únicamente cuando exista evidencia suficiente.

No debe eliminarse información útil solo para reducir volumen.

---

# Escalabilidad

La arquitectura debe poder incorporar:

- nuevos clientes;
- nuevos Agents;
- nuevo Knowledge;
- nuevos Frameworks;
- nuevos SOPs;
- nuevos Research datasets;
- nuevas Integrations;
- nuevas Automations;
- nuevas herramientas de storage;

sin rediseñar el modelo conceptual de memoria.

---

# Antipatrones

Trinity AI no debe:

- recordar todo;
- convertir conversaciones automáticamente en Knowledge;
- tratar Research como verdad permanente;
- mezclar Client Context;
- utilizar Candidate como fuente oficial;
- almacenar secretos en documentación;
- duplicar fuentes;
- crear memoria por cada detalle trivial;
- cargar toda la memoria por solicitud;
- confiar únicamente en recencia;
- usar cache como fuente de verdad;
- convertir outputs rutinarios en memoria permanente;
- promover aprendizajes automáticamente;
- mantener información obsoleta como vigente;
- confundir storage con tipo de memoria.

---

# Criterios de Éxito

Memory Architecture funciona correctamente cuando:

- el usuario no necesita repetir información disponible;
- Trinity AI recupera contexto relevante rápidamente;
- la memoria global y Client Context permanecen separados;
- Research permanece diferenciado de Knowledge;
- las decisiones relevantes pueden recuperarse;
- los Candidates pueden revisarse;
- la información obsoleta puede deprecarse;
- no existe duplicación crítica;
- la recuperación es selectiva;
- las fuentes tienen autoridad comprensible;
- la memoria puede crecer sin volverse inmanejable.

---

# Checklist de Memoria

Antes de almacenar nueva información debe evaluarse:

```text
¿Tiene valor futuro?
        ↓
¿Ya existe?
        ↓
¿Qué tipo de memoria es?
        ↓
¿Para quién aplica?
        ↓
¿Qué autoridad tiene?
        ↓
¿Necesita validación?
        ↓
¿Debe ser Candidate?
        ↓
¿Dónde debe vivir?
        ↓
¿Necesita aprobación?
```

Antes de recuperar:

```text
¿Qué necesito?
        ↓
¿Qué fuente puede responderlo?
        ↓
¿Es relevante?
        ↓
¿Es vigente?
        ↓
¿Es suficientemente autoritativa?
        ↓
Recuperar mínimo contexto suficiente
```

---

# Regla de Oro

Trinity AI no debe recordar más.

Debe recordar mejor.

```text
Capturar únicamente lo útil
        +
Clasificar correctamente
        +
Separar contextos
        +
Validar antes de promover
        +
Recuperar selectivamente
        =
Memoria confiable
```

La memoria existe para evitar dos errores igual de caros:

> olvidar lo que Trinity AI realmente sabe;

y

> tratar como conocimiento algo que nunca fue validado.