# Feature Specification: Catálogo de Bolsos Zurda (Pre-order Inquiry)

**Feature Branch**: `[002-zurda-bags-preorder]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Catálogo B2C de la línea de bolsos Zurda, operando bajo un modelo estricto de pre-order y servicio de conserjería digital, destacando la versatilidad del Método Re\_."

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Descubrimiento y Solicitud de Encargo de Bolso (Priority: P1)

Como Consumidor Premium Consciente, quiero explorar visualmente la línea de bolsos Zurda y comprender cómo se aplica el Método Re\_ en estos accesorios, para poder solicitar un encargo personalizado que complemente mi estilo de vida bajo los valores del lujo silencioso y la economía circular.

**Why this priority**: La línea Zurda representa la diversificación del catálogo B2C de la marca. Es vital para demostrar la versatilidad del Método Re\_ más allá del calzado y captar a un segmento de clientes interesados en accesorios de alta gama sostenibles, asegurando el modelo de producción bajo demanda.

**Independent Test**: Puede probarse navegando por la exposición visual del modelo Zurda, revisando sus especificaciones físicas (dimensiones, capacidad) y su narrativa de suprareciclaje, y enviando exitosamente el formulario de conserjería para solicitar la confección de una pieza.

**Acceptance Scenarios**:

1. **Given** que el usuario está explorando la página de la línea Zurda, **When** interactúa con las fotografías de detalle y la información sobre los materiales recuperados, **Then** el sistema le ofrece una vía directa y elegante para "Consultar disponibilidad / Iniciar Encargo".
2. **Given** que el usuario hace clic para iniciar un encargo, **When** se le presenta el formulario de conserjería, **Then** se le solicita información de contacto y un espacio para dudas (sin requerir talla, pero permitiendo especificar preferencias de tonalidad o uso), iniciando así el trato personalizado.

### Edge Cases

- ¿Qué ocurre si el usuario tiene dudas sobre las dimensiones exactas, el peso o la capacidad interior del bolso? (La interfaz debe proporcionar especificaciones técnicas claras y precisas, como medidas y distribución interior, mitigando fricciones negativas antes del contacto).
- ¿Cómo se manejan las solicitudes para regalos con fechas límite inamovibles? (El sistema debe comunicar proactivamente los tiempos de creación artesanal. El formulario puede incluir una casilla opcional de "¿Es para un regalo?", permitiendo a Bárbara León gestionar las expectativas de tiempo de forma empática durante el diálogo por correo).

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: El sistema DEBE presentar una galería visual inmersiva y minimalista centrada en los detalles, texturas y acabados de la línea de bolsos Zurda.
- **FR-002**: El sistema DEBE exponer claramente las características físicas del bolso (dimensiones, compartimentos, tipo de cierre) para suplir la falta de interacción física.
- **FR-003**: El sistema DEBE articular la historia de trazabilidad de los materiales utilizados en la línea Zurda y su vínculo con el Método Re\_.
- **FR-004**: El sistema DEBE informar de manera transparente sobre el modelo _pre-order_ y los tiempos de espera para la confección del bolso.
- **FR-005**: El sistema DEBE canalizar la intención de compra a través del sistema de conserjería unificado, capturando el interés específico por la línea Zurda.

### Key Entities

- **Bag Model (Modelo de Bolso)**: Representa el producto. Atributos clave: Nombre (Zurda), Galería Visual, Especificaciones Físicas (dimensiones), Narrativa de Trazabilidad, Tiempos de Creación.
- **Pre-order Inquiry (Solicitud de Encargo)**: Representa la intención de compra. Atributos clave: Modelo deseado (Zurda), Información de contacto del usuario, Petición especial/Dudas sobre uso o regalo.

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: Número de solicitudes de encargo (inquiries) específicamente para la línea Zurda recibidas mensualmente.
- **SC-002**: Ratio de conversión de consultas a ventas finalizadas gestionadas a través del servicio de "guante blanco" del taller.

## Assumptions

- Se asume que el público objetivo comprende que, al ser piezas elaboradas mediante _patchwork_ y suprareciclaje, cada bolso Zurda será único y presentará ligeras variaciones estéticas respecto a las fotografías de muestra, lo cual es parte de su valor exclusivo.
