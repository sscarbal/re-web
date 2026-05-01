# Feature Specification: Formación Institucional (University B2B Inquiry)

**Feature Branch**: `[005-institutional-training-inquiry]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Feature 5: Formación Institucional (University B2B Inquiry)"

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Solicitud de Colaboración Académica B2B (Priority: P1)

Como Coordinador Académico o Representante de una Universidad/Escuela de Diseño, quiero explorar la oferta de formación institucional de Re\_ para solicitar una colaboración académica (masterclass, taller práctico o ponencia) que integre la realidad de la economía circular y el Método Re\_ en nuestro plan de estudios.

**Why this priority**: Este es un canal B2B fundamental que monetiza el prestigio de Bárbara León y su investigación material. Posiciona a Re\_ como una autoridad académica e industrial, generando ingresos de alto volumen (ticket institucional) y atrayendo a futuros profesionales al ecosistema (retroalimentando la Feature 4). Al ser ventas consultivas complejas, el modelo "Concierge" es la única vía lógica para iniciar la negociación.

**Independent Test**: Puede probarse navegando por la sección orientada a instituciones, evaluando la autoridad del contenido metodológico expuesto y completando exitosamente el envío de una solicitud de propuesta mediante el formulario de conserjería, aportando los datos de la institución académica.

**Acceptance Scenarios**:

1. **Given** que el usuario institucional revisa la propuesta de valor educativo de Re\_, **When** comprende los formatos de colaboración (ponencias, talleres en campus, integración curricular), **Then** el sistema presenta un llamado a la acción enfocado en "Solicitar Propuesta Institucional / Contactar Dirección".
2. **Given** que el usuario institucional decide iniciar el contacto, **When** accede al formulario unificado, **Then** el sistema adapta su contexto para requerir información B2B clave: Nombre de la Institución, Cargo, Volumen estimado de alumnos y Objetivos académicos, iniciando así la venta consultiva.

### Edge Cases

- ¿Qué sucede si la institución requiere un formato digital (E-learning) en lugar de presencial? (El sistema no necesita bifurcar flujos ni cotizar automáticamente; el formulario recoge la necesidad en un campo de observaciones y Bárbara León articula la propuesta técnica —presencial o a distancia— durante el trato de "guante blanco").
- ¿Cómo se manejan las expectativas de presupuesto si no hay precios publicados? (La fricción es intencional. La omisión de un "tarifario" subraya el carácter _bespoke_ y premium del servicio. La respuesta por correo electrónico de la conserjería se encargará de calificar el presupuesto de la universidad antes de emitir una propuesta formal).

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: El sistema DEBE presentar un escaparate narrativo y visual que transmita rigor investigativo, autoridad en la materia y excelencia, respaldando el estatus de Re\_ como referente en el upcycling.
- **FR-002**: El sistema DEBE enumerar de forma clara (pero no restrictiva) los posibles formatos de colaboración institucional (ej. Masterclasses teóricas, Talleres prácticos del Método Re\_, Asesoría curricular).
- **FR-003**: El sistema DEBE canalizar el interés B2B a través del sistema de contacto centralizado, modificando la intención del usuario de "compra de producto" a "solicitud de alianza institucional".

### Key Entities

- **Institutional Offering (Propuesta Institucional)**: Representa los servicios B2B académicos. Atributos clave: Propuesta de valor metodológica, Formatos de colaboración, Perfil de la investigadora (Bárbara León).
- **B2B Academic Inquiry (Solicitud Institucional)**: Representa el lead (prospecto) cualificado. Atributos clave: Institución, Nombre y Cargo del contacto, Objetivos del programa, Fechas estimadas, Modalidad preferida.

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: Número de solicitudes institucionales legítimas generadas por trimestre académico.
- **SC-002**: Tasa de conversión de solicitudes recibidas (leads) a acuerdos académicos cerrados (medido internamente en el CRM o panel de ventas de la marca).

## Assumptions

- Se asume que el usuario (coordinador o director académico) está acostumbrado a procesos de contratación B2B que implican elaboración de propuestas a medida, reuniones posteriores y firmas de convenios, por lo que el formulario inicial sirve puramente como un rompehielos altamente cualificado.
- Se asume que el tono de esta sección será el más didáctico, riguroso y formal de toda la web, apoyándose fuertemente en el manifiesto y los resultados de investigación de la marca.
