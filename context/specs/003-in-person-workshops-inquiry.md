# Feature Specification: Formaciones Presenciales en el Taller (Workshop Inquiry)

**Feature Branch**: `[003-in-person-workshops-inquiry]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Feature 3: Formaciones Presenciales en el Taller (Workshop Inquiry)"

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Exploración y Solicitud de Plaza para Taller Presencial (Priority: P1)

Como Público Creativo Local (o visitante en Sevilla), quiero explorar la oferta de talleres presenciales impartidos en el espacio físico de Re\_ para poder solicitar una plaza, aprender de primera mano el Método Re\_ y vivir una experiencia inmersiva de artesanía contemporánea y upcycling.

**Why this priority**: La monetización del conocimiento técnico y del espacio físico en Sevilla es el tercer pilar del modelo de negocio. Estos talleres (recurrentes o intensivos) representan una vía de ingresos de ticket medio-alto y fomentan una comunidad local alrededor de la marca. Gestionar esto mediante "solicitud de plaza" mantiene el aura de exclusividad y cupo limitado.

**Independent Test**: Puede probarse navegando por la página dedicada a las formaciones físicas, revisando la descripción de la experiencia, lo que incluye (materiales, herramientas, temario) y utilizando el sistema de conserjería para solicitar formalmente una plaza en una edición específica o manifestar interés general.

**Acceptance Scenarios**:

1. **Given** que el usuario revisa la información de un taller presencial de ocio creativo, **When** lee los detalles de la experiencia (duración, ubicación en Sevilla, valor aportado), **Then** el sistema presenta un llamado a la acción claro, enfocado en "Solicitar Plaza / Consultar Próximas Fechas".
2. **Given** que el usuario decide solicitar una plaza, **When** accede al formulario de conserjería, **Then** se le requiere su información de contacto, interés específico en el taller presencial y un espacio para indicar si asiste solo o en grupo, canalizando esta intención hacia el taller para una respuesta humana.

### Edge Cases

- ¿Qué sucede si las plazas para un taller específico ya están llenas? (La fricción intencional de la conserjería convierte esta limitación en una oportunidad: la solicitud de plaza funciona tácitamente como una lista de espera premium, permitiendo a Bárbara León gestionar nuevas fechas directamente con los interesados).
- ¿Cómo se manejan las solicitudes de grupos cerrados (ej. actividades de team building o grupos de amigos)? (El formulario unificado debe contar con un área de texto libre donde el usuario pueda explicar su contexto, permitiendo al taller enviar una propuesta a medida, reforzando el servicio _bespoke_).

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: El sistema DEBE mostrar un escaparate visual que transmita la atmósfera del taller de Sevilla, destacando las herramientas, los materiales y la experiencia artesanal.
- **FR-002**: El sistema DEBE detallar claramente la propuesta de valor de cada modalidad de taller presencial (ej. duración, conocimientos adquiridos, si el usuario se lleva una pieza a casa).
- **FR-003**: El sistema DEBE comunicar que las formaciones se realizan físicamente en el taller ubicado en Sevilla, Andalucía.
- **FR-004**: El sistema DEBE integrar un flujo hacia el contacto unificado, adaptando el contexto para captar intenciones de reserva de plazas (Workshop Inquiry) en lugar de compra de producto.

### Key Entities

- **Workshop Experience (Experiencia Formativa Presencial)**: Representa la oferta educativa. Atributos clave: Título del taller, Descripción/Temario, Atmósfera visual (fotografías del espacio físico), Duración estimada.
- **Workshop Inquiry (Solicitud de Plaza)**: Representa la intención de asistencia del usuario. Atributos clave: Taller de interés, Información de contacto, Número de asistentes, Comentarios/Dudas.

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: Número de solicitudes de plaza (inquiries) para formaciones presenciales recibidas mensualmente.
- **SC-002**: Tasa de conversión desde la solicitud inicial en la web hasta la confirmación y pago (gestionado offline/vía email) de la plaza por parte del usuario.

## Assumptions

- Se asume que el usuario objetivo comprende que está solicitando acceso a una experiencia educativa de cupo muy limitado y que el pago o confirmación de fechas exactas se acordará de manera personalizada con el equipo de Re\_.
- Se asume que la estética visual de esta sección mantendrá el estándar de "lujo silencioso", elevando la percepción del "Hazlo tú mismo" (DIY) a una experiencia de artesanía premium.
