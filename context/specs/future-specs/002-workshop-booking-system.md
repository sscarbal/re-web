# Feature Specification: Workshop & Residency Booking System

**Feature Branch**: `[002-workshop-booking-system]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Sistema de Reservas de Formación (Workshops & Estancias): El motor de reservas para los talleres presenciales, controlando aforos, calendarios y pagos."

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Inscribirse en un curso presencial recurrente (Priority: P1)

Como habitante de Sevilla o alrededores interesado en el _DIY_ y la artesanía, quiero poder ver los horarios disponibles para los cursos recurrentes del taller, consultar si quedan plazas en un grupo específico y asegurar mi inscripción mediante el pago de la mensualidad o trimestre.

**Why this priority**: Es la base de la inyección de liquidez recurrente que financiará las demás fases del proyecto (objetivo: 1.000 € netos mensuales con 12-15 alumnos).

**Independent Test**: Puede probarse configurando un grupo ficticio con límite de 8 plazas, completando una inscripción exitosa que descuente el inventario a 7, y generando el recibo de pago correspondiente.

**Acceptance Scenarios**:

1. **Given** que estoy en la página de formación, **When** selecciono el "Grupo de Martes por la tarde", **Then** veo cuántas plazas quedan disponibles.
2. **Given** que selecciono un grupo con plazas, **When** completo el proceso de pago, **Then** mi plaza queda asegurada, el inventario del grupo disminuye en 1, y recibo un email de bienvenida con la dirección del taller y materiales necesarios.

---

### User Story 2 - Comprar una plaza para un Taller Intensivo de Fin de Semana (Priority: P2)

Como persona interesada en el upcycling que dispone de poco tiempo o viene de fuera de Sevilla, quiero poder consultar el calendario de talleres intensivos (fines de semana), comprar mi entrada y recibir toda la logística necesaria para el evento puntual.

**Why this priority**: Representa un pico importante de facturación puntual (2.160 € extra al trimestre) y un formato atractivo para regalos o turismo creativo.

**Independent Test**: Crear un evento de fecha cerrada (ej. 15-16 de octubre), realizar la compra de una plaza y verificar que el sistema envía la confirmación con las fechas y horarios correctos.

**Acceptance Scenarios**:

1. **Given** que visito la sección de Intensivos, **When** elijo una fecha específica, **Then** puedo comprar mi entrada (ticket medio 180 €) mediante un proceso de _checkout_ rápido.
2. **Given** que el taller intensivo está lleno (6/6 plazas), **When** intento comprar, **Then** se me ofrece apuntarme a una lista de espera prioritaria para la siguiente edición.

---

### User Story 3 - Solicitar una Estancia Formativa para Profesionales (Priority: P3)

Como profesional del diseño o estudiante avanzado, quiero poder rellenar una solicitud para realizar una residencia en el taller de Re\_, detallando mi proyecto y disponibilidad, para que Bárbara evalúe mi candidatura antes de proceder a cualquier pago.

**Why this priority**: Es un servicio B2B educativo de alto valor (facturado a 35 €/hora), pero requiere filtro de calidad y coordinación manual de agendas, por lo que no debe tener pago directo inmediato.

**Independent Test**: Envío de un formulario de solicitud complejo (con subida de portfolio/ideas y fechas deseadas) y comprobación de que llega al panel de administración para su revisión.

**Acceptance Scenarios**:

1. **Given** que estoy en la página de Estancias, **When** envío mi candidatura, **Then** veo un mensaje de confirmación explicando que la solicitud será evaluada y recibiré respuesta en X días.
2. **Given** que mi candidatura ha sido aprobada por el taller, **When** recibo el email de aceptación, **Then** este contiene un enlace privado para formalizar el pago y confirmar las fechas.

### Edge Cases

- What happens when un alumno cancela su plaza en un taller intensivo a 48 horas del evento? (Política de reembolsos vs. cesión de plaza a alguien de la lista de espera).
- How does system handle un curso recurrente que no alcanza el quórum mínimo (ej. mínimo 4 personas para ser rentable) llegado el día de inicio?
- What happens when un pago recurrente (si se opta por suscripción mensual automática para alumnos regulares) falla por tarjeta caducada?

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: System MUST gestionar el control de aforo (inventario) de forma independiente para cada fecha y grupo (ej. Grupo A: max 8 plazas, Taller Intensivo B: max 6 plazas).
- **FR-002**: System MUST automatizar el envío de comunicaciones transaccionales clave: confirmación de compra, recordatorios a 48h del inicio y solicitud de feedback post-taller.
- **FR-003**: System MUST permitir la captura de _leads_ (lista de espera) a nivel de evento específico cuando el aforo esté completo.
- **FR-004**: System MUST capturar y almacenar la información de los asistentes (nombres, nivel de experiencia, necesidades especiales) durante el _checkout_ de formación.
- **FR-005**: System MUST gestionar pagos recurrentes para los grupos mensuales [NEEDS CLARIFICATION: ¿El alumno debe entrar a pagar cada mes manualmente o se automatizará el cobro tipo suscripción mediante tarjeta guardada?].

### Key Entities

- **Workshop**: El "molde" del curso (ej. "Taller Crea tu Sandalia"). Almacena la descripción, el temario, el precio y las imágenes.
- **Cohort/Session**: La instancia temporal del _Workshop_ (ej. "Edición Fin de Semana 15-16 Octubre"). Almacena las fechas concretas, el aforo máximo, el aforo actual y el estado (Abierto, Completo, Cancelado).
- **Enrollment**: La inscripción. Relaciona a un Usuario con un _Cohort_, almacena el estado de pago y los datos del asistente.

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: Ocupación media de las plazas locales: Mantener de forma estable entre 12 y 15 alumnos activos mensuales en las clases recurrentes.
- **SC-002**: _Sell-out rate_: Lograr colgar el cartel de "Completo" en los 2 talleres intensivos trimestrales estipulados en la hoja de ruta.
- **SC-003**: Reducción de fricción administrativa: Cero horas de Bárbara invertidas en cuadrar pagos, enviar direcciones o gestionar inscripciones manuales por WhatsApp/Email para alumnos estándar.

## Assumptions

- Los alumnos asumen su propio transporte y alojamiento para llegar al taller físico en Sevilla; la web solo cobra la experiencia formativa.
- El taller cuenta con un calendario base predefinido por Bárbara a X meses vista para que el usuario siempre tenga fechas futuras disponibles para reservar.
- Las políticas de cancelación serán estrictas para proteger la compra de materiales y la preparación de los kits, y el usuario deberá aceptarlas obligatoriamente antes del pago.
