---
id: TRI-KNW-000
title: Knowledge Module
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
tags:
  - knowledge
  - retrieval
  - information
  - evidence
  - learning
---

# Trinity AI — Knowledge

## Propósito

`05_Knowledge` contiene conocimiento reutilizable que Trinity AI puede recuperar para comprender dominios, conceptos, herramientas, prácticas y principios relevantes para resolver solicitudes.

Un documento de Knowledge responde principalmente:

> ¿Qué necesita saber Trinity AI sobre este tema?

Knowledge aporta información y contexto conceptual.

No define quién ejecuta una tarea, cómo debe ejecutarse paso a paso ni qué metodología debe utilizarse para resolver un problema.

---

## Objetivo

El módulo existe para:

- centralizar conocimiento reutilizable;
- reducir reconstrucción innecesaria de información;
- mejorar consistencia entre Agents;
- facilitar recuperación selectiva;
- separar conocimiento de metodología y ejecución;
- conservar conocimiento validado;
- identificar vigencia y confiabilidad;
- permitir actualización controlada;
- convertir aprendizajes reutilizables en conocimiento mantenible;
- evitar duplicación entre proyectos y clientes.

---

## Principio Fundamental

> Knowledge almacena lo que Trinity AI necesita saber, no lo que necesita hacer.

La separación conceptual es:

```text
Knowledge
│
└── qué necesita saber Trinity AI

Framework
│
└── cómo estructurar un tipo de problema

SOP
│
└── cómo ejecutar una tarea

Agent
│
└── quién tiene responsabilidad especializada

Research
│
└── cómo obtener información que todavía falta

Client Context
│
└── qué necesita saber Trinity AI sobre un cliente específico
```

Estas responsabilidades deben permanecer separadas.

---

## Responsabilidad del Módulo

`05_Knowledge` es responsable de:

- almacenar conocimiento reutilizable;
- organizar conocimiento por dominio;
- facilitar descubrimiento;
- permitir recuperación selectiva;
- distinguir conocimiento estable de información temporal;
- identificar fuentes cuando sean necesarias;
- declarar vigencia;
- declarar incertidumbre relevante;
- mantener trazabilidad cuando corresponda;
- permitir actualización y deprecación;
- recibir conocimiento promovido desde Research o aprendizaje validado.

No es responsable de:

- definir procedimientos operativos;
- definir metodologías;
- definir Agents;
- coordinar Agents;
- almacenar contexto operativo de clientes específicos;
- realizar Research por sí mismo;
- otorgar permisos;
- ejecutar Integrations;
- ejecutar Automations;
- almacenar credenciales;
- gobernar cambios del sistema.

---

## Qué es Knowledge

Knowledge es información reusable que mejora la capacidad de Trinity AI para comprender o resolver problemas dentro de un dominio.

Puede incluir:

- conceptos;
- principios;
- definiciones;
- modelos conceptuales;
- terminología;
- buenas prácticas;
- restricciones conocidas;
- funcionamiento de plataformas;
- conocimiento técnico;
- conocimiento de dominio;
- patrones validados;
- referencias;
- información relativamente estable.

Ejemplos:

```text
Principios de marketing digital
→ Knowledge

Conceptos fundamentales de Meta Ads
→ Knowledge

Funcionamiento conceptual de SEO
→ Knowledge

Principios de producción audiovisual
→ Knowledge

Conceptos de automatización con IA
→ Knowledge
```

---

## Qué NO es Knowledge

No debe utilizarse Knowledge para almacenar principalmente:

```text
Cómo ejecutar una tarea
→ SOP

Cómo estructurar un problema
→ Framework

Quién debe resolverlo
→ Agent

Datos particulares de un cliente
→ Client Context

Resultados temporales de una investigación
→ Research

Configuración técnica de una conexión
→ Integration

Ejecución programada o automática
→ Automation
```

---

## Knowledge vs Framework

Knowledge aporta información.

Framework aporta metodología.

Ejemplo:

```text
Knowledge:
principios de comportamiento del consumidor

Framework:
metodología para construir una estrategia creativa
```

Un Framework puede recuperar Knowledge.

No debe copiarlo completamente dentro de su definición.

---

## Knowledge vs SOP

Knowledge explica información necesaria para ejecutar correctamente.

SOP define el procedimiento.

Ejemplo:

```text
Knowledge:
principios de planificación de contenidos

SOP:
procedimiento para crear un calendario mensual
```

Un SOP puede declarar qué Knowledge necesita consultar.

---

## Knowledge vs Agent

Un Agent puede especializarse en un dominio y recuperar Knowledge relacionado.

```text
Agent
  │
  ▼
Identify Knowledge Need
  │
  ▼
Retrieve Relevant Knowledge
  │
  ▼
Apply
```

Los Agents no deben almacenar copias completas del Knowledge dentro de su definición.

---

## Knowledge vs Research

Esta separación es crítica.

### Knowledge

Contiene información reutilizable suficientemente estable o validada para formar parte de la base de conocimiento.

### Research

Obtiene información cuando:

- no existe;
- falta;
- puede haber cambiado;
- necesita verificarse;
- depende del contexto actual.

La relación es:

```text
Information Need
      │
      ▼
Knowledge Available?
      │
 ┌────┴────┐
 │         │
Sí        No
 │         │
 ▼         ▼
Use      Research
           │
           ▼
        Findings
```

Los resultados de Research no deben convertirse automáticamente en Knowledge permanente.

---

## Promoción desde Research

Cuando Research produce información con valor reutilizable:

```text
Research
   │
   ▼
Finding
   │
   ▼
Reusable?
   │
 ┌─┴───────┐
 │         │
No        Sí
 │         │
 ▼         ▼
Finish   Candidate
            │
            ▼
          Review
            │
            ▼
         Knowledge
```

La promoción debe ser controlada.

Un resultado temporal, una noticia o un dato puntual no debe globalizarse automáticamente.

---

## Knowledge vs Client Context

Knowledge global debe ser reutilizable entre diferentes clientes.

Client Context contiene información específica de una organización, proyecto o cliente.

Ejemplo:

```text
"Cómo funciona una estrategia de contenidos"
→ Knowledge

"Líneas Rectas utiliza negro, blanco y gris"
→ Client Context

"Principios de e-commerce"
→ Knowledge

"El producto más vendido de un cliente es X"
→ Client Context
```

Esta separación evita contaminación entre clientes.

---

## Knowledge Global

El conocimiento reutilizable vive dentro de:

```text
05_Knowledge/
```

Debe poder ser utilizado potencialmente por más de un cliente, proyecto o Agent.

---

## Knowledge Específico de Cliente

La información específica de clientes debe vivir principalmente dentro de:

```text
08_Clients/
```

Ejemplos:

- branding;
- productos;
- precios;
- audiencia específica;
- objetivos;
- campañas;
- performance;
- decisiones;
- restricciones;
- contactos;
- historial.

No debe duplicarse dentro de Knowledge global.

---

## Carpeta Clientes

Actualmente existe:

```text
05_Knowledge/Clientes/
```

Esta carpeta solo debe contener conocimiento general y reutilizable relacionado con la gestión o comprensión de clientes.

Ejemplos válidos:

```text
principios de onboarding;
gestión de expectativas;
clasificación de necesidades;
principios de comunicación con clientes.
```

No debe contener:

```text
datos de Líneas Rectas;
datos de Municipalidad de Villa María;
datos de Pampa;
datos de cualquier cliente concreto.
```

Ese contenido pertenece a `08_Clients`.

Si durante una auditoría se detecta Client Context dentro de esta carpeta, debe proponerse su migración.

---

## Knowledge vs Integration

Knowledge puede explicar conceptos generales de una herramienta.

Integration define cómo Trinity AI interactúa técnicamente con ella.

Ejemplo:

```text
Cómo funciona conceptualmente Notion
→ Knowledge

Cómo autenticarse y ejecutar operaciones en Notion
→ Integration
```

Knowledge no debe almacenar:

- API keys;
- tokens;
- secrets;
- credenciales;
- configuraciones sensibles.

---

## Knowledge vs Automation

Knowledge puede explicar conceptos de automatización.

Automation define procesos automáticos concretos.

Ejemplo:

```text
Principios de automatización
→ Knowledge

Automatización que genera un reporte semanal
→ Automation
```

---

## Relación con CORE

CORE puede determinar que una solicitud necesita información especializada.

La secuencia conceptual es:

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
Knowledge Need
    │
    ▼
Selective Retrieval
```

CORE no debe cargar toda la base de Knowledge.

Debe recuperarse únicamente lo relevante.

---

## Relación con Orchestrator

El Orchestrator coordina Agents.

Normalmente el Agent especializado determina qué Knowledge necesita recuperar.

```text
Orchestrator
      │
      ▼
Agent
      │
      ▼
Knowledge Need
      │
      ▼
Selective Retrieval
```

El Orchestrator no debe cargar conocimiento innecesario de forma centralizada.

---

## Relación con Frameworks

Un Framework puede declarar Knowledge necesario.

```text
Framework
    │
    ▼
Relevant Knowledge
    │
    ▼
Methodology Application
```

El Framework no debe duplicar el contenido recuperado.

---

## Relación con SOPs

Un SOP puede declarar qué Knowledge necesita para ejecutar correctamente.

```text
SOP
 │
 ▼
Knowledge Retrieval
 │
 ▼
Execution
```

El SOP define la ejecución.

Knowledge aporta información.

---

## Recuperación Selectiva

Trinity AI no debe cargar toda la base de Knowledge para cada solicitud.

La secuencia correcta es:

```text
Request
   │
   ▼
Identify Domain
   │
   ▼
Identify Knowledge Need
   │
   ▼
Retrieve Relevant Documents
   │
   ▼
Evaluate Relevance
   │
   ▼
Use
```

Esto reduce:

- ruido;
- costo de contexto;
- contradicciones;
- interferencia entre dominios.

---

## Recuperación por Capas

Cuando sea útil, Knowledge puede recuperarse progresivamente:

```text
Domain
  │
  ▼
Topic
  │
  ▼
Specific Document
  │
  ▼
Relevant Section
```

Debe preferirse la menor cantidad de contexto suficiente para resolver correctamente.

---

## Organización Actual

La estructura existente es:

```text
05_Knowledge/
├── README.md
├── KNOWLEDGE_STANDARD.md
│
├── Clientes/
├── Content/
├── IA/
├── Marketing/
├── Meta Ads/
├── Notion/
├── Produccion/
├── SEO/
└── Ventas/
```

Estas categorías se conservan inicialmente.

Su contenido deberá auditarse progresivamente contra este estándar.

---

## Clientes

Debe contener únicamente conocimiento reutilizable relacionado con:

- relación con clientes;
- onboarding;
- gestión;
- comunicación;
- necesidades;
- expectativas;
- experiencia del cliente.

No debe almacenar Client Context específico.

---

## Content

Puede contener conocimiento relacionado con:

- contenido digital;
- formatos;
- plataformas;
- narrativa;
- hooks;
- copy;
- distribución;
- engagement;
- contenido orgánico.

Las metodologías de planificación pertenecen a Frameworks.

Los procedimientos pertenecen a SOPs.

---

## IA

Puede contener conocimiento relacionado con:

- inteligencia artificial;
- modelos;
- prompting;
- capacidades;
- limitaciones;
- context windows;
- multimodalidad;
- agentes;
- evaluación;
- conceptos técnicos relevantes.

La arquitectura interna de Trinity AI no debe duplicarse aquí.

---

## Marketing

Puede contener conocimiento general sobre:

- marketing;
- posicionamiento;
- segmentación;
- propuesta de valor;
- comportamiento del consumidor;
- funnel;
- adquisición;
- retención;
- estrategia comercial.

Las metodologías concretas pertenecen a Frameworks.

---

## Meta Ads

Puede contener conocimiento reutilizable relacionado con:

- estructura publicitaria;
- campañas;
- conjuntos;
- anuncios;
- objetivos;
- atribución;
- métricas;
- creatividades;
- conceptos de optimización;
- funcionamiento de la plataforma.

Los datos de campañas específicas pertenecen al Client Context o a sus resultados operativos.

---

## Notion

Puede contener conocimiento conceptual y funcional sobre Notion.

Ejemplos:

- databases;
- properties;
- relations;
- rollups;
- views;
- organización conceptual.

La autenticación o interacción técnica automatizada pertenece a Integrations.

---

## Produccion

Puede contener conocimiento sobre:

- producción audiovisual;
- fotografía;
- video;
- audio;
- iluminación;
- encuadre;
- grabación;
- edición;
- recursos de producción.

Los procedimientos concretos de producción pertenecen a SOPs.

---

## SEO

Puede contener conocimiento sobre:

- búsqueda;
- indexación;
- crawling;
- intención de búsqueda;
- keywords;
- SEO técnico;
- contenido;
- autoridad;
- métricas.

Las metodologías de auditoría o estrategia pueden pertenecer a Frameworks.

---

## Ventas

Puede contener conocimiento reutilizable sobre:

- procesos comerciales;
- persuasión;
- objeciones;
- conversión;
- seguimiento;
- negociación;
- customer journey;
- cierre;
- retención.

Los procedimientos operativos pertenecen a SOPs.

---

## Nuevas Categorías

No debe crearse una categoría nueva únicamente porque apareció un documento nuevo.

Debe evaluarse:

```text
¿Existe categoría aplicable?
        ↓
¿El contenido puede convivir allí?
        ↓
¿Existe suficiente volumen para justificar otra categoría?
        ↓
¿La nueva categoría mejora descubrimiento?
```

Solo entonces debe crearse.

---

## Granularidad

Los documentos deben tener una responsabilidad suficientemente clara.

Evitar:

```text
MARKETING_ALL.md
```

si mezcla decenas de temas sin relación operativa.

También debe evitarse fragmentación extrema:

```text
ONE_TINY_CONCEPT_PER_FILE
```

La granularidad correcta depende de:

- reutilización;
- descubrimiento;
- mantenimiento;
- frecuencia de actualización.

---

## Fuentes

Cuando una afirmación dependa de información externa relevante debe poder identificarse su origen.

Las fuentes pueden ser:

- documentación oficial;
- documentación técnica;
- investigaciones;
- libros;
- estudios;
- datasets;
- fuentes institucionales;
- experiencia validada;
- Research aprobada.

No todo conocimiento conceptual necesita una cita en cada línea.

La profundidad de trazabilidad debe ser proporcional al impacto y volatilidad.

---

## Autoridad de Fuentes

Debe priorizarse:

```text
Primary / Official Source
        ↓
High-quality Secondary Source
        ↓
Validated Internal Knowledge
        ↓
Unverified Information
```

Una fuente popular no necesariamente es una fuente autoritativa.

---

## Vigencia

Knowledge debe considerar cuánto puede cambiar la información.

Puede clasificarse conceptualmente como:

```text
Stable
Slow-changing
Dynamic
Volatile
```

Ejemplos:

```text
principio de marketing
→ relativamente estable

funcionamiento actual de una plataforma
→ dinámico

precio actual de una herramienta
→ volátil
```

La volatilidad debe influir en validación y revisión.

---

## Información Dinámica

Knowledge que depende de plataformas, políticas, APIs o herramientas debe verificarse cuando pueda haber cambiado.

No debe asumirse que un documento histórico sigue vigente únicamente porque existe en la base.

---

## Freshness

Cuando la vigencia sea crítica debe considerarse:

```text
Document Date
+
Last Review
+
Source Freshness
+
Domain Volatility
```

Si la información puede estar desactualizada, debe verificarse antes de utilizarse en decisiones importantes.

---

## Conocimiento Estable

El conocimiento estable puede reutilizarse durante períodos más largos.

Ejemplos:

- principios;
- definiciones;
- modelos conceptuales;
- fundamentos.

Aun así puede revisarse cuando exista nueva evidencia relevante.

---

## Incertidumbre

Knowledge debe diferenciar cuando corresponda:

```text
Known
Inferred
Unknown
Candidate
```

No debe convertir inferencias en hechos.

---

## Contradicciones

Cuando dos documentos de Knowledge se contradigan:

```text
Conflict
   │
   ▼
Evaluate Authority
   │
   ▼
Evaluate Freshness
   │
   ▼
Material Conflict?
   │
 ┌─┴───────┐
 │         │
No        Sí
 │         │
 ▼         ▼
Resolve   Research / Review
```

No debe seleccionarse arbitrariamente una versión.

---

## Duplicación

Antes de crear un documento debe buscarse conocimiento existente.

```text
Need
 │
 ▼
Search Knowledge
 │
 ├── Exact Match → Reuse
 │
 ├── Partial Match → Extend
 │
 └── No Match → Candidate
```

La duplicación aumenta contradicciones y costo de mantenimiento.

---

## Knowledge Candidate

Nuevo conocimiento reusable debe comenzar como Candidate o documento `Draft` según el proceso documental aplicable.

No debe convertirse automáticamente en fuente oficial.

---

## Estados

Los documentos de Knowledge utilizan:

```text
Draft
Review
Approved
Deprecated
Archived
```

### Draft

Contenido en construcción.

### Review

Contenido listo para revisión.

### Approved

Conocimiento validado como fuente oficial dentro de su alcance.

### Deprecated

Contenido que no debe utilizarse como referencia principal.

### Archived

Contenido conservado por trazabilidad.

---

## Uso según Estado

Como principio general:

```text
Approved
→ fuente interna oficial

Review
→ referencia controlada

Draft
→ contenido en construcción

Deprecated
→ evitar para nuevas decisiones

Archived
→ referencia histórica
```

---

## Aprendizaje

Las ejecuciones pueden generar aprendizajes.

Un aprendizaje no debe convertirse automáticamente en Knowledge.

La secuencia es:

```text
Execution
   │
   ▼
Observation
   │
   ▼
Reusable?
   │
 ┌─┴───────┐
 │         │
No        Sí
 │         │
 ▼         ▼
Finish   Candidate
            │
            ▼
          Review
            │
            ▼
         Knowledge
```

---

## Promoción

Un Candidate puede promoverse cuando:

- tiene valor reutilizable;
- existe evidencia suficiente;
- no duplica conocimiento existente;
- pertenece realmente a Knowledge;
- puede mantenerse;
- su alcance está claro.

---

## Corrección

Cuando se detecte conocimiento incorrecto debe:

1. identificarse el problema;
2. evaluar impacto;
3. corregirse mediante el proceso correspondiente;
4. revisar dependencias cuando sea necesario;
5. evitar que versiones incorrectas continúen utilizándose.

---

## Deprecación

Un documento puede deprecarse cuando:

- quedó desactualizado;
- fue reemplazado;
- contiene una metodología superada;
- la plataforma cambió;
- existe una fuente superior;
- dejó de representar conocimiento válido.

Cuando exista reemplazo debe indicarse.

---

## Archivado

Puede utilizarse `Archived` cuando el documento ya no deba participar en recuperación normal pero sea útil conservarlo por historia o auditoría.

---

## Modelo Agnóstico

Knowledge debe ser interpretable por diferentes modelos.

No debe depender innecesariamente de:

- Claude;
- ChatGPT;
- Gemini;
- un proveedor específico.

Cuando el conocimiento sea específicamente sobre un modelo o proveedor, esa dependencia es válida y debe ser explícita.

---

## Sensibilidad

Knowledge global no debe contener:

- passwords;
- API keys;
- tokens;
- secretos;
- credenciales;
- información privada innecesaria;
- información sensible de clientes.

Ese contenido debe manejarse mediante los sistemas correspondientes y nunca globalizarse como Knowledge.

---

## Nomenclatura

Los nombres deben describir claramente el contenido.

Ejemplos:

```text
CONTENT_FUNDAMENTALS.md
META_ADS_METRICS.md
SEO_SEARCH_INTENT.md
NOTION_DATABASE_CONCEPTS.md
SALES_OBJECTIONS.md
```

Evitar:

```text
INFO.md
NOTES.md
NEW.md
FINAL.md
DOCUMENT_2.md
```

---

## KNOWLEDGE_STANDARD.md

`KNOWLEDGE_STANDARD.md` define cómo debe construirse cada documento de Knowledge.

La relación es:

```text
README.md
   │
   └── define cómo funciona el módulo

KNOWLEDGE_STANDARD.md
   │
   └── define cómo debe documentarse Knowledge
```

---

## Recuperación por Agents

Los Agents deben recuperar únicamente Knowledge relevante para su tarea.

Ejemplo:

```text
Content Agent
    │
    ├── Content Knowledge
    ├── Marketing Knowledge
    └── Client Context relevante
```

No significa que el Agent sea propietario de esos documentos.

---

## Uso Interdominio

Una tarea puede necesitar Knowledge de múltiples categorías.

Ejemplo:

```text
Meta Ads
   +
Marketing
   +
Ventas
   +
Client Context
```

Debe recuperarse únicamente lo necesario.

Las categorías organizan Knowledge.

No crean fronteras rígidas de uso.

---

## Validación

Antes de utilizar Knowledge en una decisión relevante debe evaluarse cuando corresponda:

```text
Relevance
+
Authority
+
Freshness
+
Consistency
+
Applicability
```

Cuanto mayor sea el impacto, mayor debe ser la exigencia de validación.

---

## Antipatrones

Knowledge no debe:

- convertirse en SOP;
- convertirse en Framework;
- almacenar Client Context específico;
- copiar resultados temporales de Research sin revisión;
- almacenar credenciales;
- duplicar Architecture;
- duplicar Foundation;
- contener procedimientos completos de Integrations;
- tratar información dinámica como permanente;
- ocultar incertidumbre;
- mantener información obsoleta como oficial;
- duplicarse entre categorías;
- cargarse completamente para cada solicitud;
- crecer sin estructura;
- convertirse en un depósito de notas sin validar.

---

## Criterios de Calidad

Un documento de Knowledge debe ser:

```text
Relevant
+
Reusable
+
Clear
+
Scoped
+
Reliable
+
Current Enough
+
Retrievable
+
Maintainable
```

No necesita ser enciclopédico.

Necesita aportar conocimiento útil y confiable.

---

## Criterios de Éxito del Módulo

`05_Knowledge` funciona correctamente cuando:

- Trinity AI puede encontrar información relevante;
- los Agents recuperan solo lo necesario;
- Knowledge no duplica Frameworks;
- Knowledge no duplica SOPs;
- Client Context permanece aislado;
- Research alimenta Knowledge mediante promoción controlada;
- información dinámica se verifica;
- información obsoleta se depreca;
- las categorías facilitan descubrimiento;
- diferentes modelos pueden interpretar el contenido;
- el conocimiento puede evolucionar sin perder control.

---

## Checklist de Recuperación

Antes de utilizar Knowledge:

```text
¿Qué necesito saber?
        ↓
¿En qué dominio está?
        ↓
¿Existe Knowledge relevante?
        ↓
¿Es suficientemente autoritativo?
        ↓
¿Está suficientemente actualizado?
        ↓
¿Es aplicable al contexto?
        ↓
Use
```

Si falla una condición crítica:

```text
Research
Review
or
Escalate
```

según corresponda.

---

## Regla de Oro

> Almacenar como Knowledge únicamente información reutilizable que Trinity AI necesite saber más de una vez.

```text
Useful Information
       +
Reusable Value
       +
Clear Scope
       +
Sufficient Reliability
       +
Selective Retrieval
       =
Useful Knowledge
```

Knowledge debe aumentar la capacidad de Trinity AI para resolver problemas.

No convertirse en un depósito infinito de información.