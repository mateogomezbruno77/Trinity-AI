# 13 - Documentation Standards

---
id: TRI-FND-013
title: Documentation Standards
module: Foundation
version: 1.0.0
status: Draft
owner: Trinity AI
created:
last_updated:
reviewed_by:
approved_by:
next_review:
dependencies:
tags:
---

# Propósito

Este documento define los estándares oficiales para toda la documentación de Trinity AI.

Su objetivo es garantizar que todos los documentos del sistema mantengan la misma estructura, calidad, consistencia y facilidad de mantenimiento.

Toda documentación creada dentro de Trinity AI debe cumplir estas reglas.

---

# Objetivos

La documentación debe permitir que cualquier persona o agente de IA pueda:

- comprender rápidamente el propósito del documento;
- reutilizar el conocimiento existente;
- evitar contradicciones;
- mantener el sistema organizado;
- evolucionar la documentación sin perder consistencia.

---

# Estructura obligatoria

Todo documento deberá seguir una estructura clara y consistente.

Como mínimo deberá incluir:

1. Front Matter (Metadatos)
2. Propósito
3. Objetivo
4. Desarrollo
5. Reglas (si aplica)
6. Ejemplos (si aplica)
7. Notas adicionales (opcional)

---

# Front Matter

Todos los documentos deberán comenzar con el siguiente bloque.

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

Estos metadatos permiten que Trinity AI y otros agentes identifiquen automáticamente el documento y su estado.

---

# Convención de nombres

Todos los archivos utilizarán el siguiente formato.

## Foundation

00_Nombre_Documento.md

Ejemplo

11_Communication_Guidelines.md

---

## Architecture

01_Nombre_Documento.md

---

## Skills

Skill_Name.md

---

## Frameworks

Framework_Name.md

---

Todos los nombres deben utilizar:

- Inglés
- Pascal Case
- Guiones bajos (_)
- Sin espacios
- Sin caracteres especiales

---

# Versionado

Todos los documentos utilizarán versionado semántico.

Ejemplo:

1.0.0

Primera versión estable.

---

1.0.1

Corrección menor.

---

1.1.0

Nueva sección o mejora compatible.

---

2.0.0

Cambio importante que modifica la estructura o el funcionamiento del documento.

---

# Workflow de documentación

Todo documento debe seguir el siguiente ciclo de vida.

```text
Planned
   ↓
Draft
   ↓
Review
   ↓
Approved
   ↓
Deprecated
   ↓
Archived
```

---

## Planned

El documento existe dentro del roadmap.

Todavía no comenzó su desarrollo.

No puede utilizarse como referencia.

---

## Draft

El documento está siendo desarrollado.

Puede modificarse libremente.

No representa conocimiento oficial.

---

## Review

El contenido está completo.

Debe revisarse buscando:

- inconsistencias;
- redundancias;
- mejoras;
- dependencias;
- oportunidades de automatización.

Todavía no puede utilizarse como documentación oficial.

---

## Approved

El documento pasa a ser la fuente oficial de conocimiento.

Todos los agentes del sistema pueden utilizarlo.

Claude Code deberá priorizar únicamente documentos con estado **Approved**.

---

## Deprecated

Existe una versión más reciente.

El documento se mantiene únicamente por compatibilidad e historial.

No debe utilizarse en desarrollos nuevos.

---

## Archived

El documento deja de formar parte del sistema activo.

Se conserva únicamente como referencia histórica.

---

# Regla para modificar documentos

Un documento aprobado nunca debe modificarse directamente.

Todo cambio deberá seguir nuevamente el flujo oficial.

```text
Approved
      ↓
Draft
      ↓
Review
      ↓
Approved
```

Esto garantiza trazabilidad y consistencia.

---

# Regla para Trinity AI

Trinity AI siempre deberá consultar documentación oficial antes de generar conocimiento nuevo.

La reutilización tiene prioridad sobre la generación.

---

# Regla para Claude Code

Claude Code únicamente utilizará documentos con estado **Approved** como fuente oficial de conocimiento.

Los documentos en estado Draft, Review o Planned nunca deberán utilizarse para tomar decisiones.

---

# Checklist de aprobación

Antes de aprobar un documento deberá verificarse que:

- El propósito sea claro.
- No contradiga otros documentos.
- Tenga metadatos completos.
- Utilice la estructura oficial.
- Esté actualizado.
- Sea reutilizable.
- Contenga únicamente información validada.
- Esté alineado con PROJECT_CHARTER.md.
- Esté alineado con README.md.
- Pueda ser comprendido por otra IA sin contexto adicional.

---

# Regla de oro

La documentación existe para preservar conocimiento.

Cada documento debe reducir la necesidad de volver a explicar un proceso.

Si un documento obliga a repetir instrucciones, todavía no está terminado.