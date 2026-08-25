# 13 - Documentation Standards

---

id: TRI-FND-013
title: Documentation Standards
module: Foundation
version: 1.1.0
status: Draft
owner: Trinity AI
created:
last_updated:
reviewed_by:
approved_by:
next_review:
dependencies:

* CORE.md
* CLAUDE.md
  tags:
* documentation
* governance
* standards

---

# Propósito

Este documento define los estándares oficiales para crear, modificar, revisar, aprobar y mantener documentación dentro de Trinity AI.

Su objetivo es garantizar:

* consistencia;
* trazabilidad;
* reutilización;
* claridad;
* mantenimiento;
* interoperabilidad entre diferentes modelos de IA;
* control sobre la evolución del sistema.

---

# Principio Fundamental

La documentación debe reducir trabajo futuro.

```text
Documentar
    │
    ▼
Preservar conocimiento
    │
    ▼
Permitir reutilización
    │
    ▼
Evitar reconstrucción
```

No todo trabajo necesita convertirse en documentación.

Solo debe documentarse aquello que tenga valor operativo, estructural, histórico o reutilizable.

---

# Fuente Única de Verdad

Cada responsabilidad debe tener una ubicación oficial.

Cuando una información ya exista, otros documentos deben referenciarla en lugar de duplicarla.

Antes de crear documentación nueva:

```text
Buscar
  ↓
Reutilizar
  ↓
Adaptar
  ↓
Crear solo si es necesario
```

---

# Front Matter

Todo documento estructural debe utilizar:

```yaml
---
id:
title:
module:
version:
status:
owner:
created:
last_updated:
reviewed_by:
approved_by:
next_review:
dependencies:
tags:
---
```

Los campos que todavía no posean valor pueden permanecer vacíos durante `Draft`.

Antes de pasar a `Approved`, los metadatos relevantes deben estar completos.

---

# Estados Documentales

Los estados oficiales son:

```text
Planned
Draft
Review
Approved
Deprecated
Archived
```

## Planned

Documento identificado como necesario pero todavía no desarrollado.

No constituye fuente operativa.

## Draft

Documento en construcción.

Puede modificarse libremente.

Durante desarrollo puede utilizarse para trabajar sobre el propio sistema, pero no constituye fuente oficial.

## Review

Documento suficientemente desarrollado para revisión.

Puede utilizarse como referencia durante la construcción y auditoría de Trinity AI.

No constituye todavía una fuente oficial de producción.

## Approved

Documento validado y vigente.

Constituye fuente oficial dentro de su alcance.

## Deprecated

Documento reemplazado o en proceso de retiro.

No debe utilizarse para nuevos desarrollos salvo por compatibilidad o análisis histórico.

## Archived

Documento fuera del sistema activo.

Se conserva únicamente como referencia histórica.

---

# Desarrollo vs Producción

Trinity AI diferencia entre uso documental durante desarrollo y producción.

## Desarrollo

Puede utilizar:

```text
Approved
→ fuente oficial

Review
→ referencia de desarrollo

Draft
→ material de construcción
```

Un `Draft` no debe presentarse como regla definitiva.

## Producción

Debe priorizar:

```text
Approved
```

`Review` puede consultarse como referencia no autoritativa cuando sea necesario.

`Draft` no debe gobernar decisiones operativas de producción.

---

# Versionado

Trinity AI utiliza versionado semántico:

```text
MAJOR.MINOR.PATCH
```

## PATCH

Ejemplo:

```text
1.0.0 → 1.0.1
```

Para:

* correcciones;
* errores tipográficos;
* aclaraciones;
* ajustes sin cambio de comportamiento.

## MINOR

Ejemplo:

```text
1.0.0 → 1.1.0
```

Para:

* nuevas secciones;
* mejoras compatibles;
* ampliaciones;
* nuevas reglas que no rompen el funcionamiento existente.

## MAJOR

Ejemplo:

```text
1.0.0 → 2.0.0
```

Para:

* cambios estructurales;
* cambios de responsabilidad;
* cambios incompatibles;
* modificaciones importantes del comportamiento esperado.

---

# Modificación de Draft

Los documentos `Draft` pueden modificarse directamente mientras se encuentren en desarrollo.

Debe actualizarse la versión cuando el cambio sea suficientemente significativo para justificarlo.

---

# Modificación de Review

Un documento `Review` puede recibir correcciones derivadas del proceso de revisión.

Si el cambio altera significativamente su alcance o arquitectura, puede volver a `Draft`.

---

# Modificación de Approved

Un documento `Approved` no debe modificarse silenciosamente.

El proceso debe seguir:

```text
Approved
    │
    ▼
Change Proposal
    │
    ▼
Draft / Review
    │
    ▼
Validation
    │
    ▼
Approved
```

Cuando corresponda debe:

* incrementarse versión;
* registrarse el cambio;
* conservarse trazabilidad;
* actualizarse documentación dependiente.

---

# Convención de Nombres

Los archivos deben utilizar nombres claros, consistentes y estables.

Formato recomendado:

```text
Pascal_Case.md
```

Ejemplos:

```text
Communication_Guidelines.md
Data_Flow.md
Content_Planning_Framework.md
Monthly_Content_Planning_SOP.md
```

Cuando un módulo utilice numeración estructural, debe mantenerse la convención existente.

Ejemplo:

```text
00_Foundation/
01_Architecture/
02_SOPs/
03_Agents/
04_Frameworks/
05_Knowledge/
06_Integrations/
07_Automations/
08_Clients/
09_Templates/
10_Assets/
11_Examples/
12_Research/
13_Governance/
```

No debe introducirse una convención diferente dentro del mismo módulo sin necesidad.

---

# Idioma

Los nombres técnicos de archivos pueden utilizar inglés para mantener interoperabilidad.

La documentación interna de Trinity AI debe escribirse principalmente en español salvo que exista una razón concreta para utilizar otro idioma.

---

# Dependencias

Todo documento debe declarar dependencias relevantes cuando existan.

Ejemplo:

```yaml
dependencies:
  - CORE.md
  - 04_Frameworks/Content_Planning_Framework.md
  - 05_Knowledge/Marketing/Content_Strategy.md
```

No deben declararse dependencias únicamente porque otro archivo exista.

Solo deben incluirse relaciones reales.

---

# Estructura del Documento

No todos los documentos necesitan exactamente las mismas secciones.

Como mínimo deben permitir comprender:

1. qué es;
2. para qué existe;
3. cuándo aplica;
4. qué reglas establece;
5. cómo se relaciona con otros componentes.

Debe utilizarse la Template correspondiente cuando exista.

La claridad tiene prioridad sobre mantener secciones vacías únicamente por cumplir una estructura.

---

# Referencias

Cuando un documento dependa de una regla existente debe referenciarla.

No debe copiar grandes bloques de otra fuente únicamente para hacer el archivo autocontenido.

Esto reduce:

* duplicación;
* contradicciones;
* mantenimiento;
* versiones divergentes.

---

# Documentación de Clientes

La documentación específica debe permanecer dentro de:

```text
08_Clients/
└── Cliente/
```

No debe trasladarse automáticamente a documentación global.

Los aprendizajes reutilizables deben convertirse primero en Candidates y seguir Governance.

---

# Research

Research debe conservar:

* fuente cuando corresponda;
* fecha;
* contexto;
* alcance;
* vigencia;
* nivel de confianza cuando sea relevante.

Research no constituye automáticamente documentación oficial de Knowledge.

---

# Documentación Generada por IA

Claude, ChatGPT, Gemini u otros modelos pueden:

* crear Drafts;
* detectar inconsistencias;
* proponer modificaciones;
* realizar auditorías;
* preparar Change Proposals;
* actualizar documentación cuando estén autorizados.

No deben:

* autoaprobar cambios que requieran validación humana;
* convertir Draft en Approved unilateralmente;
* eliminar trazabilidad;
* inventar fuentes;
* crear documentación duplicada;
* modificar reglas superiores por conveniencia local.

---

# Checklist de Review

Antes de pasar un documento a `Review` verificar:

* propósito claro;
* responsabilidad definida;
* ausencia de duplicación evidente;
* estructura comprensible;
* naming correcto;
* dependencias relevantes;
* alineación con CORE;
* alineación con Foundation;
* coherencia con Architecture;
* ausencia de contradicciones conocidas.

---

# Checklist de Approval

Antes de pasar a `Approved` verificar:

* contenido validado;
* metadatos relevantes completos;
* versión correcta;
* dependencias revisadas;
* contradicciones resueltas;
* impacto evaluado;
* documentación relacionada actualizada cuando corresponda;
* comprensión independiente por otra IA;
* aprobación humana cuando sea requerida.

---

# Deprecation

Cuando un documento sea reemplazado:

```text
Approved
    │
    ▼
Replacement Approved
    │
    ▼
Deprecated
```

Debe quedar claro cuál es su reemplazo cuando corresponda.

---

# Archive

Un documento puede archivarse cuando:

* ya no participa del sistema activo;
* no posee dependencias vigentes;
* solo conserva valor histórico.

Archivar no significa eliminar.

---

# Trazabilidad

Los cambios relevantes deben poder responder:

```text
qué cambió
por qué cambió
cuándo cambió
qué versión lo introdujo
qué componentes afecta
quién lo aprobó cuando corresponda
```

La profundidad de trazabilidad debe ser proporcional al impacto del documento.

---

# Regla para Claude Code

Claude Code debe interpretar los estados según el contexto.

Durante desarrollo puede trabajar con `Draft` y `Review`.

En producción debe utilizar `Approved` como fuente oficial.

Nunca debe presentar un documento no aprobado como regla oficial sin indicarlo.

---

# Regla de Oro

La documentación no existe para producir más documentación.

Existe para hacer que Trinity AI sea más fácil de operar, mantener y escalar.

```text
Claridad
   +
Fuente única
   +
Reutilización
   +
Trazabilidad
   -
Burocracia innecesaria
   =
Documentación útil
```

Si mantener un documento genera más trabajo del que evita, debe revisarse su diseño o necesidad.
