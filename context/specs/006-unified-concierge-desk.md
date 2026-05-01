# Feature Specification: Sistema Centralizado de Contacto (Unified Concierge Desk)

**Feature Branch**: `[006-unified-concierge-desk]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Feature 6: Sistema Centralizado de Contacto (Unified Concierge Desk)"

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Experiencia de Conserjería Adaptativa y Envío de Solicitud (Priority: P1)

Como Prospecto (independientemente de si soy cliente B2C, alumno o institución), quiero utilizar un único punto de contacto que entienda el contexto de mi visita, para enviar mi solicitud de forma clara, elegante y directa al taller de Re\_, iniciando así un diálogo personalizado.

**Why this priority**: Este es el "embudo" definitivo y el motor de conversión del MVP. Al carecer de automatizaciones transaccionales (carritos de compra), toda la viabilidad comercial del ecosistema digital depende de que este sistema centralizado funcione sin fricciones técnicas, pero manteniendo la "fricción intencional" a nivel de negocio para cualificar al lead.

**Independent Test**: Puede probarse accediendo a este sistema desde distintos puntos de origen de la web (un zapato, un bolso, una formación institucional) y verificando que el entorno de contacto asimila el contexto de procedencia, solicita la información precisa para ese caso de uso y emite un acuse de recibo elegante tras su envío.

**Acceptance Scenarios**:

1. **Given** que el usuario hace clic en el botón de "Iniciar Encargo" desde el modelo 'Manuela', **When** el sistema despliega la interfaz de conserjería, **Then** el entorno reconoce visual o estructuralmente que la consulta es sobre el modelo 'Manuela' y adapta los campos solicitados (ej. pidiendo talla habitual).
2. **Given** que un usuario navega directamente a la sección genérica de contacto sin un producto específico en mente, **When** visualiza la interfaz, **Then** el sistema le permite seleccionar de forma intuitiva el motivo de su consulta (Encargo, Formación, Prensa/B2B) para enrutar correctamente su petición.
3. **Given** que el usuario ha completado y enviado su solicitud, **When** el envío es exitoso, **Then** la interfaz transita hacia un estado de confirmación de "guante blanco" que agradece el contacto y establece expectativas claras y honestas sobre el tiempo de respuesta artesanal del taller.

### Edge Cases

- ¿Qué ocurre si el usuario olvida rellenar un dato vital para poder responderle (ej. su correo electrónico)? (El sistema debe guiar al usuario mediante validaciones visuales elegantes e integradas en el diseño minimalista, evitando mensajes de error agresivos que rompan la estética de lujo silencioso).
- ¿Cómo manejamos mensajes excesivamente largos o complejos? (El campo de texto libre debe fomentar la expresividad del usuario, ya que buscamos un diálogo humano. No deben existir límites de caracteres estrictos que coarten la narrativa o las dudas detalladas de un cliente o institución).

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: El sistema DEBE proveer una única interfaz de entrada de datos (formulario maestro) capaz de gestionar todas las intenciones del ecosistema Re\_.
- **FR-002**: El sistema DEBE heredar el contexto de la intención del usuario (si proviene de una Feature específica) para pre-configurar el motivo del contacto y minimizar el esfuerzo cognitivo.
- **FR-003**: El sistema DEBE aplicar la "fricción intencional", requiriendo que el usuario articule explícitamente sus necesidades o dudas a través de campos de texto libre, filtrando así intenciones de baja calidad.
- **FR-004**: El sistema DEBE estructurar la información recopilada en un formato ordenado y legible (Lead unificado) para facilitar la posterior respuesta humana.
- **FR-005**: El sistema DEBE presentar un estado de confirmación post-envío que refuerce los valores de la marca y gestione la expectativa temporal de respuesta.

### Key Entities

- **Unified Lead (Solicitud Estructurada)**: Representa el paquete de información que llega al taller. Atributos clave:
  - Contexto/Origen (Calzado, Bolso, Taller Presencial, Estancia, Institucional, General).
  - Datos de Identificación (Nombre, Institución -si aplica-).
  - Vía de Retorno (Correo electrónico).
  - Datos Específicos del Contexto (Talla, Fechas, Producto exacto).
  - Narrativa del Usuario (Mensaje abierto).

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: 100% de tasa de entrega exitosa de las solicitudes originadas en la web a la bandeja de entrada central del taller.
- **SC-002**: Reducción drástica del número de correos de "ida y vuelta" necesarios para clarificar la intención inicial del cliente, gracias a que el sistema centralizado captura el contexto exacto desde el primer momento.

## Assumptions

- Se asume que detrás de este sistema digital existe un proceso operativo (manual y humano) por parte del equipo de Re\_ para clasificar mentalmente estas solicitudes estructuradas y responderlas en un plazo coherente con el servicio premium que se promete.
- Se asume que el diseño visual de esta área transmitirá la misma calma y minimalismo que el resto del catálogo, sintiéndose como una prolongación del servicio de asesoría que Bárbara León ofrecería en su propio espacio físico.
