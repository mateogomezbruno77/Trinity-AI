---
id: TRI-FND-013
title: Documentation Standards
module: Foundation
version: 1.2.0
status: Draft
owner: Trinity AI
created:
last_updated:
reviewed_by:
approved_by:
next_review:
dependencies:
  - CORE.md
tags:
  - documentation
  - standards
  - governance
  - metadata
  - lifecycle
---

# 13 - Documentation Standards

# Propósito

Este documento define los estándares oficiales para crear, estructurar, nombrar, clasificar, mantener, revisar y evolucionar la documentación de Trinity AI.

Su objetivo es garantizar que el sistema pueda crecer sin convertirse en una colección desordenada de archivos, instrucciones duplicadas o conocimiento contradictorio.

Este documento define cómo debe documentarse Trinity AI.

No define:

- comportamiento general de la IA;
- razonamiento;
- toma de decisiones;
- arquitectura operativa;
- procedimientos específicos;
- responsabilidades de Agents;
- conocimiento de clientes.

---

# Objetivo

La documentación de Trinity AI debe ser:

- clara;
- modular;
- reutilizable;
- trazable;
- mantenible;
- consistente;
- identificable;
- versionable;
- auditable;
- comprensible por humanos y modelos de IA.

Cada documento debe tener una responsabilidad clara.

---

# Principio Rector

> Una pieza de documentación debe existir únicamente cuando tenga una responsabilidad clara y aporte valor futuro al sistema.

Documentar más no significa documentar mejor.

La documentación debe reducir incertidumbre y trabajo repetitivo.

Nunca debe convertirse en burocracia innecesaria.

---

# Principios de Documentación

Toda documentación debe respetar los siguientes principios:

1. una responsabilidad principal por documento;
2. reutilización antes de duplicación;
3. referencias antes que copias;
4. contexto específico separado del conocimiento global;
5. estado documental explícito;
6. dependencias explícitas;
7. cambios trazables;
8. promoción controlada;
9. estructura consistente;
10. mínima complejidad suficiente.

---

# Documentación como sistema

La documentación de Trinity AI no debe entenderse como archivos aislados.

Debe funcionar como una red de fuentes relacionadas.

```text
CORE
   │
   ▼
Foundation
   │
   ▼
Architecture
   │
   ├── SOPs
   ├── Agents
   ├── Frameworks
   ├── Knowledge
   ├── Integrations
   ├── Automations
   ├── Clients
   ├── Templates
   ├── Assets
   ├── Examples
   ├── Research
   └── Governance
```

Cada documento debe saber:

- qué responsabilidad tiene;
- qué módulo lo contiene;
- qué fuentes necesita;
- qué fuentes pueden depender de él;
- cuál es su estado.

---

# Estructura oficial del repositorio

La estructura principal de Trinity AI es:

```text
Trinity-AI/
│
├── CORE.md
│
├── CLAUDE.md
│
├── 00_Foundation/
├── 01_Architecture/
├── 02_SOPs/
├── 03_Agents/
├── 04_Frameworks/
├── 05_Knowledge/
├── 06_Integrations/
├── 07_Automations/
├── 08_Clients/
├── 09_Templates/
├── 10_Assets/
├── 11_Examples/
├── 12_Research/
└── 13_Governance/
```

La incorporación de nuevos módulos raíz debe tratarse como un cambio arquitectónico.

No debe crearse una nueva carpeta principal únicamente porque un documento no encaje inmediatamente en la estructura existente.

Primero debe evaluarse si pertenece a un módulo actual.

---

# Responsabilidades por módulo

## CORE

Contiene la referencia operativa principal del sistema.

No debe convertirse en repositorio general de conocimiento.

---

## 00_Foundation

Contiene reglas fundamentales y protocolos globales.

Ejemplos:

- comunicación;
- comportamiento;
- pensamiento;
- decisiones;
- documentación;
- diseño.

---

## 01_Architecture

Documenta la estructura del sistema y relaciones entre componentes.

No debe contener conocimiento de negocio.

---

## 02_SOPs

Contiene procedimientos operativos repetibles.

Responde:

> ¿Cómo se ejecuta esta tarea paso a paso?

---

## 03_Agents

Contiene definiciones de especialistas.

Responde:

> ¿Quién es responsable de este tipo de trabajo y cuál es su alcance?

---

## 04_Frameworks

Contiene metodologías reutilizables.

Responde:

> ¿Cómo debe abordarse y estructurarse este tipo de problema?

---

## 05_Knowledge

Contiene conocimiento global validado.

Responde:

> ¿Qué necesita saber Trinity AI?

---

## 06_Integrations

Documenta cómo Trinity AI interactúa con herramientas externas.

---

## 07_Automations

Documenta procesos automatizados autorizados.

---

## 08_Clients

Contiene contexto específico de clientes y proyectos.

---

## 09_Templates

Contiene estructuras reutilizables para crear nuevos documentos o entregables.

---

## 10_Assets

Contiene recursos y materiales reutilizables.

---

## 11_Examples

Contiene implementaciones de referencia.

---

## 12_Research

Contiene investigación, evidencia, benchmarking y análisis.

---

## 13_Governance

Controla evolución, aprobación, versionado, cambios y calidad del sistema.

---

# Regla de ubicación

Antes de crear un documento debe determinarse:

```text
¿Qué contiene?
      │
      ▼
¿Qué responsabilidad cumple?
      │
      ▼
¿Qué módulo posee esa responsabilidad?
      │
      ▼
Guardar allí
```

La ubicación no debe decidirse únicamente por conveniencia.

---

# Separación entre tipos de información

Trinity AI debe mantener explícitamente separadas las siguientes categorías.

```text
Knowledge
→ conocimiento validado

Research
→ evidencia e investigación

Framework
→ metodología

SOP
→ procedimiento

Agent
→ responsabilidad especializada

Client Context
→ información específica de cliente

Template
→ estructura reutilizable

Example
→ implementación de referencia

Automation
→ proceso automático

Integration
→ acceso a herramienta

Decision
→ decisión relevante del sistema
```

Una misma información no debe copiarse en múltiples categorías.

---

# Fuente única de verdad

Cuando exista información oficial, debe existir una fuente principal responsable.

Otros documentos deben referenciarla.

Debe evitarse:

```text
Archivo A
→ regla X

Archivo B
→ copia de regla X

Archivo C
→ otra versión de regla X
```

Debe favorecerse:

```text
Archivo A
→ fuente oficial de regla X

Archivo B
→ referencia Archivo A

Archivo C
→ referencia Archivo A
```

---

# Duplicación

La duplicación documental aumenta:

- contradicciones;
- mantenimiento;
- contexto innecesario;
- riesgo de utilizar versiones obsoletas.

Antes de agregar contenido debe evaluarse:

> ¿Esta información ya tiene una fuente responsable?

Si existe, debe referenciarse.

---

# Repetición intencional

Puede repetirse una regla breve cuando sea necesaria para comprensión local.

La repetición no debe convertirse en una segunda definición oficial.

Ejemplo válido:

```text
Este Agent requiere aprobación para acciones externas.

Referencia:
14_AI_Behavior.md
```

Ejemplo inválido:

copiar dentro del Agent todo el sistema de clasificación de riesgo y mantenerlo independientemente.

---

# Tipos de documentos

Trinity AI puede contener, entre otros:

- Protocol;
- Architecture Document;
- Framework;
- SOP;
- Agent Definition;
- Knowledge Document;
- Integration Specification;
- Automation Specification;
- Client Document;
- Template;
- Example;
- Research Document;
- Governance Document;
- Decision Record.

Cada tipo debe mantenerse dentro del módulo correspondiente.

---

# Front Matter

Los documentos estructurales y operativos deben utilizar metadata cuando corresponda.

Formato recomendado:

```yaml
---
id: TRI-MOD-001
title: Document Title
module: Module
version: 1.0.0
status: Draft
owner: Trinity AI
created:
last_updated:
reviewed_by:
approved_by:
next_review:
dependencies:
  - path/to/dependency.md
tags:
  - example
---
```

---

# Regla del Front Matter

El Front Matter debe comenzar en la primera línea del archivo.

Formato:

```text
---
metadata
---
```

No debe colocarse un título Markdown antes del bloque YAML.

Ejemplo incorrecto:

```text
# Documento

---
id: ...
---
```

Ejemplo correcto:

```text
---
id: ...
---

# Documento
```

Esta regla permite que herramientas automáticas puedan interpretar correctamente la metadata.

---

# ID documental

Cada documento estructural debe poseer un identificador estable cuando corresponda.

Formato recomendado:

```text
TRI-[MODULE]-[NUMBER]
```

Ejemplos:

```text
TRI-CORE-001
TRI-FND-013
TRI-ARCH-001
TRI-SOP-001
TRI-AGT-001
TRI-FWK-001
TRI-KNW-001
```

El ID no debe modificarse simplemente porque cambie el nombre visible del archivo.

---

# IDs de módulos

Convenciones recomendadas:

```text
CORE → CORE
Foundation → FND
Architecture → ARCH
SOPs → SOP
Agents → AGT
Frameworks → FWK
Knowledge → KNW
Integrations → INT
Automations → AUT
Clients → CLT
Templates → TPL
Assets → AST
Examples → EX
Research → RES
Governance → GOV
```

Estas convenciones deben mantenerse consistentes.

---

# Title

`title` debe describir claramente el contenido.

Debe evitar nombres ambiguos como:

```text
Notes
Ideas
New Document
General
Various
```

Debe preferir nombres específicos.

---

# Module

`module` identifica el módulo responsable del documento.

Ejemplos:

```yaml
module: Foundation
```

```yaml
module: Architecture
```

```yaml
module: SOPs
```

---

# Version

Los documentos versionados deben utilizar:

```text
MAJOR.MINOR.PATCH
```

Ejemplo:

```text
1.2.0
```

---

# Versionado semántico

## PATCH

Correcciones menores que no cambian comportamiento o significado principal.

Ejemplo:

```text
1.2.0 → 1.2.1
```

Puede incluir:

- ortografía;
- formato;
- aclaraciones menores;
- enlaces corregidos.

---

## MINOR

Cambios compatibles que agregan o mejoran capacidad sin romper la lógica anterior.

Ejemplo:

```text
1.2.0 → 1.3.0
```

Puede incluir:

- nueva sección;
- nueva regla compatible;
- mayor precisión;
- nuevo criterio.

---

## MAJOR

Cambios que modifican significativamente comportamiento, responsabilidades o compatibilidad.

Ejemplo:

```text
1.2.0 → 2.0.0
```

Puede incluir:

- cambio de responsabilidad;
- eliminación de reglas importantes;
- cambio arquitectónico;
- modificación incompatible.

---

# Estado documental

Todo documento gobernado debe poseer un estado explícito.

Estados oficiales:

```text
Draft
Review
Approved
Deprecated
Archived
```

---

# Draft

Significa:

- documento en construcción;
- puede cambiar;
- no constituye fuente oficial;
- puede utilizarse para desarrollo.

---

# Review

Significa:

- contenido suficientemente maduro;
- pendiente de revisión;
- puede utilizarse como referencia controlada;
- todavía no es fuente oficial de producción.

---

# Approved

Significa:

- revisado;
- aprobado;
- vigente;
- fuente oficial dentro de su alcance.

En producción, la documentación operativa debe priorizar `Approved`.

---

# Deprecated

Significa:

- todavía existe por compatibilidad o referencia;
- no debe utilizarse para nuevas implementaciones;
- debe indicar su reemplazo cuando exista.

---

# Archived

Significa:

- histórico;
- fuera de operación;
- conservado únicamente por trazabilidad.

No debe utilizarse para nuevas decisiones.

---

# Ciclo de vida documental

El ciclo recomendado es:

```text
Draft
  │
  ▼
Review
  │
  ▼
Approved
  │
  ├──────────────┐
  ▼              ▼
Update       Deprecated
  │              │
  ▼              ▼
Review        Archived
```

No todos los documentos necesitan llegar a `Approved`.

---

# Creación

Un documento nuevo debe crearse únicamente cuando:

- exista una responsabilidad clara;
- no haya una fuente adecuada existente;
- tenga valor futuro;
- pueda mantenerse;
- tenga una ubicación correcta.

---

# Revisión

Antes de pasar a `Review` debe comprobarse:

- propósito claro;
- responsabilidad única;
- estructura válida;
- metadata correcta;
- dependencias correctas;
- ausencia de duplicación innecesaria;
- consistencia terminológica;
- referencias válidas;
- compatibilidad arquitectónica.

---

# Aprobación

Antes de pasar a `Approved` debe comprobarse:

- revisión completada;
- contradicciones resueltas;
- dependencias verificadas;
- impacto evaluado;
- responsable identificado;
- aprobación registrada;
- versión correcta.

---

# Actualización

Cuando un documento `Approved` necesite cambiar, debe evitarse modificar silenciosamente su comportamiento.

Debe evaluarse:

```text
Cambio
  │
  ▼
Impacto
  │
  ▼
Versión
  │
  ▼
Review
  │
  ▼
Approval
```

---

# Dependencias

`dependencies` debe contener únicamente documentos que sean necesarios para interpretar o aplicar correctamente el documento actual.

No debe convertirse en una lista de todas las referencias mencionadas.

Ejemplo:

```yaml
dependencies:
  - CORE.md
  - 14_AI_Behavior.md
```

---

# Referencia vs dependencia

Debe distinguirse:

```text
Dependency
→ necesaria para funcionamiento o interpretación

Reference
→ relacionada pero no necesaria
```

Mencionar un documento no crea automáticamente una dependencia.

Esto es fundamental para evitar dependencias circulares.

---

# Dependencias circulares

Debe evitarse:

```text
A depende de B
B depende de A
```

Cuando dos documentos necesiten relacionarse, debe determinarse cuál posee la responsabilidad superior.

Ejemplo:

```text
AI Behavior
→ define comportamiento base

Thinking Framework
→ depende de AI Behavior

Decision Framework
→ depende de Thinking Framework
```

Un documento superior puede referenciar conceptualmente uno inferior sin declararlo como dependencia formal.

---

# Dirección de dependencias

Las dependencias deben seguir una dirección lógica.

Ejemplo:

```text
CORE
   ↓
Foundation Base
   ↓
Behavior
   ↓
Thinking
   ↓
Decision
```

Debe evitarse que una capa inferior gobierne una capa superior.

---

# Referencias internas

Las referencias deben utilizar rutas suficientemente claras.

Ejemplo:

```text
01_Architecture/ORCHESTRATOR.md
```

Cuando el archivo se encuentre en el mismo directorio puede utilizarse:

```text
14_AI_Behavior.md
```

Debe favorecerse consistencia en todo el repositorio.

---

# Enlaces rotos

Durante auditorías deben verificarse:

- archivos inexistentes;
- rutas renombradas;
- referencias obsoletas;
- documentos Deprecated;
- dependencias eliminadas.

Una referencia rota debe corregirse.

---

# Nombres de archivos

Los nombres deben ser:

- claros;
- predecibles;
- estables;
- descriptivos.

Ejemplos:

```text
14_AI_Behavior.md
15_Thinking_Framework.md
16_Decision_Framework.md
ORCHESTRATOR.md
AGENT_INTERACTION.md
```

Debe evitarse:

```text
final.md
final_v2.md
final_final.md
new.md
copy.md
```

El versionado pertenece al Front Matter y al historial de Git.

---

# Convenciones de nombres

Dentro de módulos numerados puede utilizarse:

```text
NN_Name.md
```

Para documentos arquitectónicos con identidad propia puede utilizarse:

```text
UPPER_SNAKE_CASE.md
```

La convención debe mantenerse consistente dentro de cada categoría.

---

# Encabezados

Debe existir un único título principal `#` por documento.

Las secciones principales deben utilizar:

```text
# Título
## Sección
### Subsección
```

Debe evitarse utilizar niveles de encabezado únicamente por estilo visual.

---

# Separadores

Puede utilizarse:

```text
---
```

para separar bloques conceptuales.

No debe abusarse de separadores cuando los encabezados ya aporten estructura suficiente.

---

# Listas

Las listas deben utilizarse cuando mejoren:

- escaneabilidad;
- claridad;
- comparación;
- ejecución.

No debe convertirse todo el documento en listas si la explicación requiere contexto.

---

# Diagramas textuales

Los diagramas `text` pueden utilizarse para representar:

- flujos;
- jerarquías;
- dependencias;
- estados;
- decisiones.

Ejemplo:

```text
Input
  │
  ▼
Process
  │
  ▼
Output
```

Deben utilizarse para simplificar conceptos, no para decorar.

---

# Bloques de código

Los bloques deben especificar lenguaje cuando sea posible.

Ejemplos:

````text
```yaml
status: Draft
```