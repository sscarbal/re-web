# Feature Specification: B2B Portal & Fit Kit Management

**Feature Branch**: `[004-b2b-portal-fitkit]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Portal B2B & Fit Kit Management: El espacio exclusivo para que las concept stores soliciten paquetes de descubrimiento, registren medidas y hagan pedidos de reposición."

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Solicitud de Paquete de Descubrimiento (Priority: P1)

Como dueño de una _Concept Store_ de lujo silencioso, quiero enviar una solicitud formal a Re\_ para evaluar la marca, solicitar el "Paquete Físico de Descubrimiento" (que incluye muestrarios y el Fit Kit) y conocer las condiciones del modelo _wholesale_ sin riesgo de stock.

**Why this priority**: Es el embudo de entrada (Onboarding) para la expansión B2B. Automatizar este primer contacto profesionaliza la marca frente a boutiques europeas y filtra a los prospectos cualificados.

**Independent Test**: Rellenar el formulario de solicitud B2B público, verificar que se envía correctamente al panel de administración de Re\_ y que el prospecto recibe un dossier digital automatizado (PDF) con las condiciones generales.

**Acceptance Scenarios**:

1. **Given** que visito la página de "Partners / B2B", **When** completo el formulario con los datos de mi tienda y envío la solicitud, **Then** visualizo una pantalla de confirmación indicando que mi perfil será evaluado por el equipo de Re\_.
2. **Given** que Bárbara aprueba mi solicitud en el panel de administración, **When** mi perfil se activa, **Then** recibo un email con las credenciales de acceso a mi portal privado B2B y las instrucciones para recibir el Paquete de Descubrimiento.

---

### User Story 2 - Realizar un encargo de cliente final utilizando el Fit Kit (Priority: P1)

Como dependiente de una tienda asociada, quiero acceder rápidamente al portal B2B mientras atiendo a un cliente en la tienda física, seleccionar la talla base que el cliente se ha probado del Fit Kit físico, y anotar las modificaciones necesarias (ej. "empeine un poco más ancho") para formalizar el pedido con cero margen de error.

**Why this priority**: Es la operativa diaria del modelo B2B. El Fit Kit es el diferenciador que elimina las devoluciones por problemas de talla. Este flujo debe ser tan ágil que el dependiente pueda hacerlo frente al cliente.

**Independent Test**: Iniciar sesión con un usuario B2B activo, abrir el formulario rápido de "Nuevo Encargo Fit Kit", rellenar los datos de ajuste y verificar que el pedido se crea aplicando automáticamente el descuento de tienda (margen _wholesale_).

**Acceptance Scenarios**:

1. **Given** que estoy logueado en el portal privado de mi tienda, **When** inicio un "Nuevo Encargo Fit Kit" y selecciono el modelo, talla base y variaciones, **Then** el sistema calcula el coste final descontando mi comisión del 40-50% sobre el PVP.
2. **Given** que confirmo el pedido del cliente, **When** el pago se procesa o se anota en cuenta, **Then** el sistema genera un identificador de pedido único y lo añade a mi lista de pedidos en fabricación.

---

### User Story 3 - Panel de seguimiento y reposición para la tienda (Priority: P2)

Como _buyer_ o dueño de la tienda física, quiero un panel de control (_dashboard_) centralizado donde pueda ver el estado de fabricación de todos los encargos de mis clientes, y realizar reposiciones de mi inventario base de Fit Kits o muestrarios de forma autónoma.

**Why this priority**: Reduce drásticamente la carga de atención al cliente B2B (emails y llamadas de tiendas preguntando "cuándo llega el zapato de mi cliente"). Otorga independencia operativa a las _concept stores_.

**Independent Test**: Acceder al portal B2B y comprobar que se listan los pedidos activos con su estado actualizado (ej. "En corte", "En ensamblaje", "Enviado a tienda").

**Acceptance Scenarios**:

1. **Given** que accedo a mi portal B2B, **When** voy a la sección "Mis Pedidos", **Then** veo una lista clara con el nombre del cliente final, el modelo, la fecha estimada de entrega y el estado actual de producción en el taller.

### Edge Cases

- What happens when una tienda B2B acumula facturas impagadas o rechaza el envío del producto final tras haberlo encargado?
- How does system handle la gestión del Paquete de Descubrimiento físico si la tienda decide no trabajar con Re\_ y debe devolver el muestrario? (Gestión de fianzas o etiquetas de retorno).
- What happens when el cupo de producción del taller (6-8 pares/mes) se llena con ventas B2C? ¿Se reservan cupos exclusivos para los encargos B2B para asegurar un tiempo de entrega rápido a las tiendas?

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: System MUST proveer un formulario de aplicación B2B público con campos específicos de negocio (Nombre comercial, CIF/VAT, enlace a Instagram/Web, marcas con las que trabajan).
- **FR-002**: System MUST soportar un sistema de autenticación (Login) exclusivo para cuentas con rol "B2B Partner", dándoles acceso a un área restringida de la web.
- **FR-003**: System MUST aplicar automáticamente la estructura de precios B2B (descuento del 40-50% sobre PVP) en todos los flujos de compra iniciados desde una sesión B2B.
- **FR-004**: System MUST incluir un formulario específico de "Fit Kit" que obligue a referenciar una talla base de prueba antes de permitir anotaciones de modificación (para estandarizar el proceso del taller).
- **FR-005**: System MUST [NEEDS CLARIFICATION: ¿El pago de los pedidos B2B se realizará al momento con tarjeta de crédito corporativa, o el sistema debe permitir facturación a 30/60 días (Net-30)?].

### Key Entities

- **B2BPartner**: Extensión de la entidad usuario. Representa a la tienda. Almacena su nivel de comisión (margen _wholesale_), dirección de facturación, dirección de envío y estado de asociación (Pendiente, Activo, Inactivo).
- **FitKitMeasurement**: Los datos estructurados enviados por el dependiente de la tienda (Talla Base de Prueba, Ancho de Empeine, Notas Adicionales). Va adjunto al `PreOrderTicket`.
- **DiscoveryPackageAllocation**: Entidad para rastrear qué muestrario físico tiene cada tienda, fecha de envío, y fecha límite de devolución o firma de contrato.

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: Tasa de conversión de prospección: Alcanzar una tasa mínima del 25% (1 tienda asociada activa por cada 4 Paquetes Físicos de Descubrimiento enviados).
- **SC-002**: Tasa de devoluciones por talla B2B: Mantener un **0% de devoluciones** o quejas por mal ajuste gracias al rigor del formulario Fit Kit digital.
- **SC-003**: Frecuencia de pedido: Consolidar un mínimo de 2 encargos mensuales gestionados de forma autónoma a través del portal por cada boutique asociada a la marca.

## Assumptions

- Se asume que el envío de los pedidos B2B siempre se realiza a la dirección de la _Concept Store_ (para que el cliente final vaya a recogerlo allí), y no directamente a la casa del cliente final.
- Se asume que la firma del contrato legal para regular la custodia de los Paquetes de Descubrimiento y Muestrarios se gestionará externamente (ej. vía DocuSign) y no dentro de esta funcionalidad en su Fase I.
- Se asume que los empleados de la tienda utilizarán sus propias tablets, móviles o TPVs para acceder al portal de Re\_ mediante el navegador web (no requiere una app nativa en la App Store).
