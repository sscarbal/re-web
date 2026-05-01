# Feature Specification: Catálogo de Calzado Bajo Demanda (Pre-order Inquiry)

**Feature Branch**: `[001-footwear-preorder]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Catálogo B2C de los modelos icónicos de calzado (Sandal, Manuela, Costura, Saco) operando bajo un modelo estricto de pre-order y servicio de conserjería digital."

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Exploración y Solicitud de Encargo Personalizado (Priority: P1)

Como Consumidor Premium Consciente, quiero explorar visualmente los modelos icónicos de calzado de Re\_ y conocer la historia detrás de sus materiales, para poder iniciar una solicitud de encargo personalizado (pre-order) que respete mis valores de sostenibilidad y exclusividad.

**Why this priority**: La venta directa (B2C) es el primer pilar de negocio de la marca. Educar al usuario sobre el Método Re\_ y guiarlo hacia el modelo _made-to-order_ es fundamental para garantizar el flujo de ingresos sin generar sobreproducción (riesgo cero de stock).

**Independent Test**: Puede probarse completamente navegando por la galería visual de un modelo específico de calzado, leyendo su narrativa de trazabilidad y tiempos de espera, y completando el formulario de solicitud de encargo, lo que entrega un prospecto (lead) altamente cualificado directamente al taller.

**Acceptance Scenarios**:

1. **Given** que el usuario se encuentra en la página de un modelo icónico (ej. "Manuela"), **When** revisa las imágenes de alta calidad y la explicación del modelo pre-order, **Then** el sistema le presenta una opción clara para "Consultar disponibilidad / Iniciar Encargo".
2. **Given** que el usuario ha decidido iniciar un encargo, **When** accede al punto de contacto, **Then** se le solicita información básica (nombre, talla habitual, preferencias o dudas) para iniciar un diálogo humano y personalizado con el taller.

### Edge Cases

- ¿Qué ocurre cuando el usuario busca envíos inmediatos o entregas exprés? (La interfaz debe comunicar proactivamente y con elegancia los tiempos de creación artesanal antes de que el usuario inicie el contacto, gestionando las expectativas mediante la fricción intencional).
- ¿Cómo gestiona el sistema las solicitudes de tallas fuera del estándar o peticiones de personalización extrema? (El formulario de solicitud debe incluir un espacio de texto abierto para que el cliente exprese sus necesidades particulares, las cuales serán evaluadas manualmente por Bárbara León o su equipo).

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: El sistema DEBE mostrar un catálogo visual minimalista enfocado en la fotografía de alta calidad de los modelos icónicos de calzado.
- **FR-002**: El sistema DEBE comunicar claramente la narrativa de cada modelo, incluyendo el origen de los materiales (trazabilidad) y la filosofía del Método Re\_.
- **FR-003**: El sistema DEBE informar de manera explícita y elegante sobre los tiempos estimados de confección del modelo Pre-order.
- **FR-004**: El sistema DEBE proveer un mecanismo intencional (formulario de conserjería) para que el usuario envíe su intención de compra, capturando su interés por un modelo específico, su talla de referencia y sus comentarios.

### Key Entities

- **Footwear Model (Modelo de Calzado)**: Representa el producto base. Atributos clave: Nombre (ej. Saco, Costura), Galería Visual (imágenes de lujo silencioso), Narrativa de Trazabilidad, Tiempos de Creación Estimados.
- **Pre-order Inquiry (Solicitud de Encargo)**: Representa la intención de compra del usuario. Atributos clave: Modelo deseado, Talla habitual, Información de contacto del usuario, Mensaje/Petición especial.

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: Número de solicitudes de encargo (inquiries) cualificadas recibidas mensualmente en la bandeja de entrada del taller.
- **SC-002**: Tasa de conversión de solicitudes de contacto a encargos de calzado confirmados (medido internamente por el equipo tras el diálogo de conserjería).

## Assumptions

- Se asume que el usuario objetivo valora la exclusividad y la sostenibilidad por encima de la inmediatez, y percibe el proceso de "solicitud" y la espera como parte del valor premium del producto (fricción positiva).
- Se asume que el taller cuenta con la capacidad de respuesta necesaria para atender estas solicitudes de forma ágil y con un trato de "guante blanco" vía correo electrónico.
