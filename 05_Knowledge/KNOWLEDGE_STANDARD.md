---
id: TRI-KNW-001
title: Knowledge Standard
module: Knowledge
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
  - 05_Knowledge/README.md
tags:
  - knowledge
  - standards
  - retrieval
  - evidence
  - freshness
  - validation
---

# Trinity AI — Knowledge Standard

## Propósito

`KNOWLEDGE_STANDARD.md` define el estándar para crear, documentar, validar, mantener, recuperar y deprecar documentos de Knowledge dentro de Trinity AI.

Su función es garantizar que el conocimiento almacenado sea:

- reutilizable;
- claramente delimitado;
- suficientemente confiable;
- recuperable;
- mantenible;
- consciente de su vigencia;
- compatible con diferentes Agents y modelos.

Este documento responde:

> ¿Cómo debe estar construido y mantenido un documento de Knowledge dentro de Trinity AI?

No contiene conocimiento de dominio específico.

Define el estándar que ese conocimiento debe respetar.

---

## Objetivo

Todo documento de Knowledge debe permitir responder:

```text
¿Qué conocimiento contiene?
        ↓
¿Para qué dominio sirve?
        ↓
¿Cuándo es relevante?
        ↓
¿Qué queda fuera de su alcance?
        ↓
¿Qué tan estable es?
        ↓
¿De dónde proviene?
        ↓
¿Qué nivel de confianza tiene?
        ↓
¿Cuándo debe verificarse?
        ↓
¿Cómo debe recuperarse?
        ↓
¿Cuándo debe actualizarse o deprecarse?
```

Si estas preguntas no pueden responderse razonablemente, el documento puede estar insuficientemente definido.

---

## Principio Fundamental

> Knowledge debe almacenar información reutilizable, no convertirse en un depósito general de contexto.

La relación buscada es:

```text
Relevant Information
        +
Clear Scope
        +
Sufficient Reliability
        +
Freshness Awareness
        +
Selective Retrieval
        =
Useful Knowledge
```

Más información no significa automáticamente mejor Knowledge.

---

## Alcance

Este estándar aplica a los documentos almacenados dentro de:

```text
05_Knowledge/
```

Incluye las categorías actuales:

```text
Clientes/
Content/
IA/
Marketing/
Meta Ads/
Notion/
Produccion/
SEO/
Ventas/
```

También aplica a nuevas categorías que sean aprobadas posteriormente.

No aplica al Client Context específico almacenado en `08_Clients`.

---

## Cuándo Crear Knowledge

Debe considerarse crear un documento cuando exista:

```text
Información útil
      +
Valor reutilizable
      +
Dominio identificable
      +
Alcance claro
      +
Confiabilidad suficiente
      =
Knowledge Candidate
```

La información debería tener una probabilidad razonable de volver a ser útil.

---

## Cuándo NO Crear Knowledge

No debe crearse un documento de Knowledge cuando el contenido corresponda principalmente a:

```text
Metodología
→ Framework

Procedimiento
→ SOP

Responsabilidad
→ Agent

Contexto de cliente
→ Client Context

Resultado temporal
→ Research Finding

Acceso técnico
→ Integration

Ejecución automática
→ Automation
```

Tampoco debe crearse para información trivial que pueda recuperarse fácilmente y no tenga valor persistente.

---

## Reutilizar Antes de Crear

Antes de crear Knowledge nuevo:

```text
Search Existing Knowledge
        │
        ▼
Exact Match?
        │
   ┌────┴────┐
   │         │
  Sí        No
   │         │
   ▼         ▼
 Reuse    Partial Match?
               │
          ┌────┴────┐
          │         │
         Sí        No
          │         │
          ▼         ▼
        Extend    Candidate
```

Debe evitarse crear documentos redundantes.

---

## Estructura Recomendada

Un documento de Knowledge debe contemplar, cuando corresponda:

```text
Front Matter
Título
Propósito
Dominio
Alcance
Fuera de Alcance
Cuándo Utilizar
Conceptos Clave
Contenido
Principios
Terminología
Ejemplos
Limitaciones
Fuentes
Freshness
Incertidumbre
Relaciones
Validación
Mantenimiento
```

No todas las secciones son obligatorias.

La estructura debe adaptarse al tipo de conocimiento.

---

## Front Matter

Todo documento debe comenzar con Front Matter YAML válido.

Formato base:

```yaml
---
id: TRI-KNW-XXX
title:
module: Knowledge
category:
version: 1.0.0
status: Draft
owner: Trinity AI
created:
last_updated:
reviewed_by:
approved_by:
next_review:
freshness:
dependencies: []
tags:
  - knowledge
---
```

Debe respetar:

```text
00_Foundation/13_Documentation_Standards.md
```

---

## ID

Cada documento debe utilizar un identificador único.

Formato recomendado:

```text
TRI-KNW-XXX
```

Ejemplos:

```text
TRI-KNW-101
TRI-KNW-102
TRI-KNW-103
```

Un ID no debe reutilizarse para contenidos diferentes.

---

## Title

El título debe describir claramente qué conocimiento contiene.

Correcto:

```text
Meta Ads Metrics
SEO Search Intent
Content Hook Fundamentals
Notion Database Concepts
Sales Objection Fundamentals
```

Evitar:

```text
Notes
Info
Knowledge Final
Document 2
Various Concepts
```

---

## Module

Para Knowledge global:

```yaml
module: Knowledge
```

---

## Category

Debe identificar la categoría principal donde vive el documento.

Ejemplo:

```yaml
category: Meta Ads
```

Debe corresponder a la organización real del módulo.

No deben crearse categorías nuevas arbitrariamente.

---

## Version

Todo documento debe tener versión.

Versión inicial:

```yaml
version: 1.0.0
```

Los cambios deben respetar Documentation Standards y Governance.

---

## Status

Todo documento nuevo comienza como:

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

---

## Freshness

Cuando sea útil debe declararse la sensibilidad temporal del contenido.

Valores conceptuales recomendados:

```text
Stable
Slow-changing
Dynamic
Volatile
```

### Stable

Conocimiento que cambia poco.

Ejemplos:

- fundamentos;
- principios;
- conceptos.

### Slow-changing

Puede evolucionar, pero normalmente no requiere verificación frecuente.

### Dynamic

Puede cambiar por:

- plataformas;
- productos;
- políticas;
- prácticas;
- tecnología.

Debe verificarse periódicamente.

### Volatile

Puede cambiar con frecuencia y no debe utilizarse sin validación reciente cuando el dato sea relevante.

---

## Freshness no es Verdad

Un documento reciente no es automáticamente correcto.

Debe evaluarse:

```text
Freshness
+
Authority
+
Evidence
+
Consistency
```

---

## Dependencies

Debe declarar únicamente dependencias documentales reales.

Ejemplo:

```yaml
dependencies:
  - 05_Knowledge/Marketing/MARKETING_FUNDAMENTALS.md
```

No debe añadirse todo documento relacionado conceptualmente.

Debe evitarse crear ciclos innecesarios.

---

## Título Principal

Después del Front Matter debe existir exactamente un H1.

Ejemplo:

```text
# Meta Ads Metrics
```

Las secciones principales utilizan H2.

Las subsecciones respetan Documentation Standards.

---

## Propósito

Debe explicar brevemente:

- qué conocimiento contiene;
- para qué sirve;
- por qué tiene valor reusable.

Ejemplo:

```text
Este documento contiene las principales métricas utilizadas para interpretar performance dentro de Meta Ads y sus relaciones conceptuales.
```

---

## Dominio

Debe indicar claramente el dominio principal.

Ejemplos:

```text
Marketing
Meta Ads
SEO
Content
IA
Ventas
```

Esto mejora recuperación y clasificación.

---

## Alcance

Debe indicar qué cubre el documento.

Ejemplo:

```text
Incluye:
- definición de métricas;
- relación entre métricas;
- interpretación conceptual.

No incluye:
- performance de clientes específicos;
- procedimiento de optimización;
- configuración de campañas.
```

---

## Fuera de Alcance

Cuando exista riesgo de confusión debe declararse explícitamente qué no pertenece al documento.

Esto ayuda a mantener separación entre módulos.

---

## Cuándo Utilizar

Debe indicar situaciones donde el conocimiento sea relevante.

Ejemplo:

```text
Utilizar cuando:
- se analice performance de Meta Ads;
- sea necesario interpretar métricas;
- un Framework requiera conceptos publicitarios.
```

---

## Conceptos Clave

Puede incluir una lista de conceptos fundamentales necesarios para comprender el dominio.

Ejemplo:

```text
Impressions
Reach
CPM
CTR
CPC
CPA
ROAS
```

No debe convertirse automáticamente en un glosario gigantesco.

---

## Contenido

Esta sección contiene el conocimiento reusable.

Debe ser:

- claro;
- estructurado;
- suficientemente preciso;
- relevante;
- libre de contexto específico innecesario.

Debe evitar acumular información solo porque está relacionada con el tema.

---

## Principios

Cuando el dominio tenga principios relativamente estables pueden documentarse.

Ejemplo conceptual:

```text
Una métrica aislada rara vez explica por sí sola la performance completa de una campaña.
```

Los principios específicos del dominio no deben duplicar Foundation.

---

## Terminología

Cuando existan términos técnicos o ambiguos debe definirse su significado.

Ejemplo:

```text
CTR:
porcentaje de impresiones que generan un clic según la definición utilizada por la plataforma correspondiente.
```

Cuando una plataforma tenga definiciones oficiales debe priorizarse su documentación.

---

## Ejemplos

Los ejemplos pueden utilizarse para mejorar comprensión.

Deben identificarse como ejemplos.

No deben presentarse como reglas universales.

---

## Ejemplos de Cliente

Evitar utilizar datos reales de clientes cuando no sean necesarios.

Preferir ejemplos abstractos o anonimizados.

Client Context no debe globalizarse mediante ejemplos.

---

## Fuentes

Cuando el conocimiento dependa de información externa relevante debe declararse su origen.

Puede utilizarse:

```text
## Fuentes

- Fuente oficial
- Documentación técnica
- Estudio
- Investigación
```

Las referencias deben ser suficientemente identificables.

---

## Jerarquía de Fuentes

Como principio:

```text
Official / Primary
        ↓
Authoritative Secondary
        ↓
Validated Internal Knowledge
        ↓
Community / Anecdotal
        ↓
Unverified
```

La jerarquía puede variar según el dominio.

---

## Fuentes Oficiales

Deben priorizarse cuando se documente:

- funcionamiento de plataformas;
- APIs;
- políticas;
- especificaciones;
- métricas;
- productos;
- características técnicas.

---

## Fuentes Secundarias

Pueden complementar cuando:

- agregan interpretación;
- comparan;
- sintetizan;
- aportan evidencia adicional.

No deben reemplazar una fuente primaria disponible sin razón.

---

## Experiencia Interna

La experiencia obtenida mediante ejecuciones puede aportar Knowledge.

Debe distinguirse de una regla universal.

Ejemplo:

```text
Internal Observation
```

puede convertirse en Candidate si aparece repetidamente.

---

## Research como Fuente

Research puede alimentar Knowledge.

La secuencia correcta es:

```text
Research
   │
   ▼
Finding
   │
   ▼
Validate
   │
   ▼
Reusable?
   │
   ├── No → remain finding
   │
   └── Sí
          │
          ▼
       Candidate
          │
          ▼
        Review
          │
          ▼
       Knowledge
```

No debe copiarse automáticamente todo resultado de Research.

---

## Evidencia

Cuando una afirmación sea importante debe poder diferenciarse entre:

```text
Fact
Observation
Inference
Hypothesis
Unknown
```

La documentación debe evitar falsa certeza.

---

## Nivel de Confianza

Cuando sea relevante puede declararse:

```text
High
Medium
Low
```

Debe utilizarse únicamente cuando aporte información útil.

No es obligatorio puntuar cada afirmación.

---

## Incertidumbre

Cuando exista incertidumbre material debe declararse.

Ejemplo:

```text
Known:
La plataforma utiliza un sistema de subasta.

Dynamic:
Los detalles específicos del algoritmo pueden cambiar.

Unknown:
Criterios internos no publicados.
```

---

## Supuestos

Los supuestos no deben almacenarse como conocimiento confirmado.

Si son necesarios deben identificarse explícitamente.

---

## Información Dinámica

Cuando el documento incluya información dinámica debe indicar qué elementos requieren revisión.

Ejemplo:

```text
Dynamic elements:
- funcionalidades actuales;
- límites;
- políticas;
- nomenclaturas;
- configuración disponible.
```

---

## Información Volátil

Datos altamente volátiles no deberían almacenarse como Knowledge permanente salvo que exista una razón clara.

Ejemplos:

```text
precio actual;
ranking diario;
tipo de cambio;
performance actual de campaña.
```

Normalmente deben recuperarse mediante Research, Integration o Client Context.

---

## Validación de Vigencia

Antes de utilizar Knowledge dinámico en una decisión importante:

```text
Check Last Updated
        ↓
Check Source
        ↓
Check Domain Volatility
        ↓
Still Reliable?
        │
   ┌────┴────┐
   │         │
  Sí        No / Unsure
   │         │
   ▼         ▼
 Use      Verify
```

---

## Contradicciones

Cuando dos documentos se contradigan debe evaluarse:

1. alcance;
2. autoridad;
3. fecha;
4. fuente;
5. contexto;
6. versión.

Si el conflicto continúa siendo material:

```text
Research
or
Review
```

No debe resolverse arbitrariamente.

---

## Duplicación

Debe evitarse almacenar la misma información en múltiples documentos.

Cuando exista superposición:

```text
Exact duplication
→ consolidate

Partial overlap
→ reference

Different scope
→ preserve separation
```

---

## Referencias Cruzadas

Los documentos pueden referenciar otros Knowledge cuando exista una relación real.

Ejemplo:

```text
Para fundamentos generales de marketing:
05_Knowledge/Marketing/MARKETING_FUNDAMENTALS.md
```

No debe copiarse el documento completo.

---

## Relación con Frameworks

Un Framework puede consumir Knowledge.

Knowledge no debe incorporar la metodología completa del Framework.

Ejemplo:

```text
Knowledge
→ principios de audiencia

Framework
→ metodología para definir audiencia estratégica
```

---

## Relación con SOPs

Un SOP puede consultar Knowledge.

Knowledge no debe describir el procedimiento operativo completo.

---

## Relación con Agents

Los Agents pueden recuperar Knowledge según necesidad.

Knowledge no pertenece exclusivamente a un Agent.

---

## Relación con Client Context

Esta separación es obligatoria.

Knowledge global:

```text
Cómo funciona un funnel de ventas
```

Client Context:

```text
El funnel actual del Cliente X
```

La segunda información no debe almacenarse globalmente.

---

## Relación con Integrations

Knowledge puede explicar una plataforma.

Integration define interacción técnica.

Ejemplo:

```text
Knowledge:
conceptos de Notion Databases

Integration:
operaciones autorizadas contra Notion
```

---

## Relación con Architecture

Knowledge puede explicar conceptos técnicos generales.

No debe duplicar la arquitectura interna de Trinity AI definida en `01_Architecture`.

---

## Categoría Clientes

`05_Knowledge/Clientes/` requiere especial control.

Solo debe almacenar conocimiento general sobre:

- onboarding;
- relación;
- comunicación;
- gestión;
- expectativas;
- experiencia;
- procesos generales de clientes.

Cualquier información identificable de un cliente concreto debe permanecer fuera de esta categoría y migrarse a `08_Clients` cuando corresponda.

---

## Clasificación

Antes de guardar Knowledge:

```text
What is this?
     │
     ▼
Domain
     │
     ▼
Existing Category?
     │
 ┌───┴────┐
 │        │
Sí       No
 │        │
 ▼        ▼
Store   Is new category justified?
             │
        ┌────┴────┐
        │         │
       No        Sí
        │         │
        ▼         ▼
Reclassify    Candidate Category
```

---

## Nuevas Categorías

Una nueva categoría debería existir únicamente cuando:

- existe volumen suficiente;
- mejora descubrimiento;
- representa un dominio diferenciado;
- no duplica categorías existentes.

No deben crearse carpetas por anticipación.

---

## Granularidad

Un documento debe ser suficientemente específico para recuperarse con precisión y suficientemente amplio para evitar fragmentación inútil.

La regla es:

```text
Retrievable
+
Coherent
+
Reusable
=
Correct Granularity
```

---

## Recuperación Selectiva

Los documentos deben diseñarse pensando en recuperación.

Un Agent debería poder encontrar:

```text
Domain
   ↓
Topic
   ↓
Document
   ↓
Relevant Section
```

sin cargar todo `05_Knowledge`.

---

## Metadata para Recuperación

Los siguientes campos ayudan al descubrimiento:

```text
title
category
tags
dependencies
status
freshness
```

Deben utilizarse consistentemente.

---

## Tags

Los tags deben representar conceptos útiles para búsqueda.

Ejemplo:

```yaml
tags:
  - meta-ads
  - metrics
  - performance
  - advertising
```

Evitar tags excesivamente genéricos o redundantes.

---

## Estado Draft

Utilizar cuando:

- el contenido está incompleto;
- falta validación;
- las fuentes necesitan revisión;
- todavía está siendo estructurado.

---

## Estado Review

Utilizar cuando:

- el documento está completo;
- las fuentes principales fueron revisadas;
- el alcance está definido;
- está listo para evaluación.

---

## Estado Approved

Utilizar únicamente después del proceso de aprobación correspondiente.

Representa la fuente interna preferida dentro de su alcance.

---

## Estado Deprecated

Utilizar cuando el conocimiento:

- quedó obsoleto;
- fue reemplazado;
- dejó de ser confiable;
- ya no debe utilizarse como referencia principal.

Debe indicarse el reemplazo cuando exista.

---

## Estado Archived

Utilizar cuando:

- ya no participa en recuperación normal;
- se conserva por historia;
- se conserva por auditoría;
- se necesita trazabilidad.

---

## Actualización

Un documento debe revisarse cuando:

- cambia una fuente principal;
- cambia una plataforma;
- aparece evidencia superior;
- se detecta un error;
- existe contradicción;
- se supera `next_review`;
- cambia materialmente el dominio.

---

## Actualización Proporcional

No todo documento necesita la misma frecuencia.

```text
Stable
→ revisión baja

Slow-changing
→ revisión periódica

Dynamic
→ revisión frecuente

Volatile
→ verificar antes de uso relevante
```

---

## Cambios Materiales

Ejemplos:

- cambiar una definición importante;
- modificar principios;
- reemplazar fuentes;
- cambiar alcance;
- incorporar evidencia contradictoria;
- cambiar conclusiones conceptuales.

Deben respetar Governance.

---

## Cambios Editoriales

Ejemplos:

- ortografía;
- formato;
- claridad;
- jerarquía Markdown;
- correcciones sin cambio conceptual.

Deben respetar Documentation Standards.

---

## Corrección de Errores

Cuando se detecte un error material:

```text
Identify
   │
   ▼
Assess Impact
   │
   ▼
Correct
   │
   ▼
Validate
   │
   ▼
Review Dependencies
```

No debe mantenerse información incorrecta únicamente por preservar versiones.

---

## Mantenimiento

Cada documento debe ser mantenible.

Debe evitar depender de:

- cientos de enlaces frágiles;
- información sin fuente;
- contexto implícito;
- conocimiento de una sola persona;
- estructura excesivamente compleja.

---

## Deprecación

Cuando un documento sea reemplazado debe preferirse deprecar antes que eliminar si aporta trazabilidad.

Puede indicarse:

```text
Deprecated because:
[...]

Replacement:
[...]
```

---

## Knowledge Candidate

Un Candidate puede originarse desde:

- Research;
- ejecución;
- aprendizaje;
- documentación externa;
- experiencia;
- nueva necesidad de dominio.

Debe evaluarse antes de promoverse.

---

## Criterios de Promoción

Antes de convertir un Candidate en Knowledge:

```text
[ ] Tiene valor reutilizable
[ ] Tiene alcance claro
[ ] Pertenece realmente a Knowledge
[ ] No duplica contenido existente
[ ] Tiene confiabilidad suficiente
[ ] Tiene fuentes cuando son necesarias
[ ] Su vigencia puede gestionarse
[ ] Puede recuperarse fácilmente
```

---

## Modelo Agnóstico

Los documentos deben poder utilizarse con diferentes modelos.

No deben incluir instrucciones innecesariamente específicas como:

```text
Claude debe interpretar...
ChatGPT debe hacer...
```

salvo que el conocimiento trate específicamente sobre ese modelo.

---

## Seguridad

Knowledge global nunca debe almacenar:

```text
Passwords
API Keys
Tokens
Secrets
Private Credentials
Sensitive Client Information
```

La facilidad de recuperación no debe comprometer seguridad.

---

## Template Base

La siguiente estructura puede utilizarse como base para documentos nuevos:

```text
---
id:
title:
module: Knowledge
category:
version: 1.0.0
status: Draft
owner: Trinity AI
created:
last_updated:
reviewed_by:
approved_by:
next_review:
freshness:
dependencies: []
tags:
  - knowledge
---

# [Knowledge Title]

## Propósito

[...]

## Dominio

[...]

## Alcance

### Incluye

[...]

### No Incluye

[...]

## Cuándo Utilizar

[...]

## Conceptos Clave

[...]

## Contenido

[...]

## Principios

[...]

## Terminología

[...]

## Ejemplos

[...]

## Limitaciones

[...]

## Fuentes

[...]

## Freshness

[...]

## Incertidumbre

[...]

## Relaciones

[...]

## Validación

[...]

## Mantenimiento

[...]
```

La plantilla debe adaptarse al tipo de conocimiento.

No deben añadirse secciones vacías únicamente para cumplir formato.

---

## Checklist de Creación

Antes de mover Knowledge de `Draft` a `Review`:

```text
[ ] Tiene propósito claro
[ ] Tiene dominio definido
[ ] Está en la categoría correcta
[ ] Tiene alcance claro
[ ] No pertenece a Frameworks
[ ] No pertenece a SOPs
[ ] No contiene Client Context específico
[ ] No duplica Architecture
[ ] No duplica Foundation
[ ] No duplica Knowledge existente
[ ] Tiene fuentes cuando son necesarias
[ ] Declara incertidumbre relevante
[ ] Considera freshness
[ ] Tiene granularidad razonable
[ ] Puede recuperarse selectivamente
[ ] No contiene credenciales
[ ] Respeta Documentation Standards
```

---

## Checklist de Uso

Antes de utilizar un documento:

```text
¿Es relevante?
      ↓
¿Es aplicable?
      ↓
¿Está vigente?
      ↓
¿Su fuente es suficientemente confiable?
      ↓
¿Existe contradicción relevante?
      ↓
¿Necesita verificación externa?
      ↓
Use
```

---

## Checklist de Auditoría

Durante una auditoría de Knowledge:

```text
[ ] Categoría correcta
[ ] Scope correcto
[ ] Sin Client Context globalizado
[ ] Sin duplicación significativa
[ ] Sin procedimientos disfrazados
[ ] Sin Frameworks disfrazados
[ ] Fuentes adecuadas
[ ] Freshness coherente
[ ] Estado correcto
[ ] Dependencias válidas
[ ] Sin información sensible
[ ] Sin contenido claramente obsoleto presentado como vigente
```

---

## Antipatrones

Un documento de Knowledge no debe:

- convertirse en una wiki infinita;
- almacenar información porque "puede servir algún día";
- duplicar Frameworks;
- duplicar SOPs;
- globalizar Client Context;
- copiar Research sin validación;
- presentar hipótesis como hechos;
- ignorar freshness;
- depender de fuentes débiles cuando existen fuentes oficiales;
- almacenar información volátil como permanente sin advertencia;
- duplicarse entre categorías;
- contener credenciales;
- crecer sin alcance;
- convertirse en notas personales;
- cargarse automáticamente para todas las solicitudes.

---

## Criterios de Calidad

Knowledge de calidad debe ser:

```text
Relevant
+
Reusable
+
Scoped
+
Reliable
+
Fresh Enough
+
Retrievable
+
Maintainable
```

No necesita contener todo lo que existe sobre un tema.

Debe contener lo necesario para mejorar futuras resoluciones.

---

## Criterios de Éxito

Este estándar funciona correctamente cuando:

- Knowledge puede descubrirse fácilmente;
- los Agents recuperan información relevante;
- el contexto cargado se mantiene reducido;
- las fuentes importantes son identificables;
- información dinámica se revisa;
- Knowledge obsoleto se depreca;
- Research puede alimentar la base sin contaminarla;
- Client Context permanece separado;
- Frameworks consumen Knowledge sin duplicarlo;
- SOPs consumen Knowledge sin absorberlo;
- la base puede crecer sin convertirse en un depósito caótico.

---

## Regla de Oro

> Guardar menos conocimiento, pero mejor clasificado, validado y recuperable, es preferible a guardar todo.

```text
Useful
  +
Reusable
  +
Reliable
  +
Scoped
  +
Fresh Enough
  +
Retrievable
  =
Operational Knowledge
```

Knowledge debe reducir la necesidad de volver a aprender lo mismo.

No aumentar el costo de encontrar lo que importa.