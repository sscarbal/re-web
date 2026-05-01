# Feature Specification: Digital Passport & Traceability

**Feature Branch**: `[003-digital-passport-traceability]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Trazabilidad & Pasaporte Digital: La experiencia de la landing page dinámica a la que se accede vía QR para ver la historia del producto, materiales y opciones de upselling/reparación."

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Descubrir el origen y la historia del producto único (Priority: P1)

Como cliente que acaba de recibir su encargo (B2C) o que está probándose el zapato en una tienda física (B2B), quiero poder escanear el código QR que acompaña al producto para descubrir qué piezas de calzado o textil desechado se utilizaron específicamente para fabricar este par, comprobando así el valor real del _upcycling_.

**Why this priority**: Es el núcleo de la promesa de marca (transparencia y cero _greenwashing_). Añade una capa narrativa de "lujo consciente" que justifica el ticket alto y el tiempo de espera.

**Independent Test**: Generar un código URL/QR único de prueba, escanearlo con un móvil y verificar que la _landing page_ muestra correctamente los datos específicos asociados a ese identificador (ej. "Tus Sandal fueron creadas a partir de lona de tienda Koopera y restos de cuero de tapicería").

**Acceptance Scenarios**:

1. **Given** que tengo un par de zapatos Re\_ físicos, **When** escaneo el QR con mi teléfono móvil, **Then** accedo directamente a una página optimizada para móviles que cuenta la historia de mi par exacto, sin tener que iniciar sesión.
2. **Given** que estoy visualizando el pasaporte digital, **When** hago _scroll_ por la página, **Then** puedo ver fotos o infografías de los materiales originales antes de ser transformados por el método _patchwork_ de Re\_.

---

### User Story 2 - Solicitar la reparación o restauración del producto (Priority: P2)

Como cliente que ha usado sus zapatos Re\_ durante años, quiero utilizar el Pasaporte Digital para acceder a un servicio de reparación o mantenimiento (_resoling_, limpieza de materiales), para extender la vida útil de mi producto dentro de la economía circular.

**Why this priority**: Convierte una venta puntual en una relación de por vida. Refuerza el compromiso de circularidad y genera un flujo de ingresos secundario por servicios de mantenimiento.

**Independent Test**: Acceder a un pasaporte activo, pulsar el botón "Solicitar Reparación" y verificar que el formulario pre-rellena automáticamente el modelo y número de serie del producto.

**Acceptance Scenarios**:

1. **Given** que estoy en el Pasaporte Digital de mi producto, **When** hago clic en "Cuidados y Reparación", **Then** veo instrucciones de mantenimiento y un formulario directo para enviar el zapato al taller.
2. **Given** que envío la solicitud de reparación, **When** se procesa en el sistema, **Then** Bárbara recibe un email con el modelo exacto y el cliente recibe las instrucciones de envío.

---

### User Story 3 - Acceder a ofertas exclusivas de fidelización (_Upselling_) (Priority: P3)

Como dueño de un artículo Re\_ (y por tanto, cliente VIP), quiero encontrar recomendaciones de productos complementarios (ej. la línea de bolsos Zurda) o descuentos exclusivos a través del Pasaporte Digital, premiando mi fidelidad a la marca.

**Why this priority**: Capitaliza la emoción de recibir el pedido (el momento en el que el cliente escanea el QR por primera vez) para incentivar una segunda compra sin costes de adquisición de cliente (CAC).

**Independent Test**: Añadir un bloque promocional dinámico a la plantilla del Pasaporte y comprobar que el código de descuento mostrado (ej. `RE-VIP-10`) aplica correctamente en el _checkout_ global.

**Acceptance Scenarios**:

1. **Given** que estoy explorando mi Pasaporte Digital, **When** llego al final de la historia de mi producto, **Then** veo un acceso anticipado o un código promocional único para adquirir un bolso Zurda a juego.

### Edge Cases

- What happens when la etiqueta física con el QR se pierde, se rompe o se vuelve ilegible tras años de uso? ¿Existe un código alfanumérico grabado en el producto para acceder manualmente a la URL?
- How does system handle que un segundo propietario (mercado de segunda mano) escanee el código QR? ¿Debe la plataforma permitir "transferir la propiedad" del pasaporte digital?
- What happens when se escanea el QR de un producto que aún está marcado como "En fabricación" en la base de datos interna?

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: System MUST generar un identificador único global (UUID) y un enlace asociado por cada artículo individual fabricado (no a nivel de modelo genérico, sino a nivel de par fabricado).
- **FR-002**: System MUST permitir a Bárbara o al asistente de taller asignar rápidamente (vía panel de administración) qué materiales/lote se han usado para un identificador único en un máximo de 3 clics o escaneos.
- **FR-003**: System MUST presentar la información en una interfaz estrictamente diseñada bajo enfoque _mobile-first_ (dado que el 100% de los accesos iniciales serán escaneos desde un smartphone).
- **FR-004**: System MUST incluir un formulario de contacto específico en la _landing_ del QR que vincule automáticamente la consulta al identificador del producto.
- **FR-005**: System MUST recopilar analíticas de escaneo [NEEDS CLARIFICATION: ¿Queremos medir geolocalización básica de los escaneos para saber hasta qué países están viajando los zapatos desde las tiendas B2B?].

### Key Entities

- **DigitalTwin (Gemelo Digital)**: La entidad principal. Representa la versión digital de un objeto físico. Contiene el UUID, el enlace de la _landing page_, y el estado actual (Recién creado, En propiedad, Reparado).
- **MaterialOrigin**: Metadatos asociados al _DigitalTwin_ (ej. "Cuero de sofá", "Cordones de excedente deportivo", "Suela reciclada").
- **PhysicalItem**: El par de zapatos o bolso físico que lleva adherido el soporte del QR.

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: Tasa de interacción (_Scan Rate_): Al menos el **70%** de los productos entregados (B2C y B2B) son escaneados por el cliente final en los primeros 30 días.
- **SC-002**: Tasa de conversión de retención: Al menos un **10%** de los clientes que acceden al pasaporte utilizan el código promocional para una compra cruzada en los siguientes 6 meses.
- **SC-003**: Carga administrativa neta de creación: Crear y vincular un nuevo Pasaporte Digital durante la fase final de empaquetado en el taller no debe sumar más de **1 minuto** por pedido al flujo de trabajo de Bárbara.

## Assumptions

- Se asume que el soporte físico del QR (etiqueta de papel semilla, grabado láser en la suela, o tarjeta en la caja) será técnicamente viable, duradero y proporcionado por un proveedor de imprenta/grabado ajeno al software web.
- Se asume que los clientes saben cómo usar la cámara de su teléfono inteligente para leer códigos QR sin necesidad de descargar aplicaciones de terceros.
- Se asume que en la Fase I, el ingreso de datos sobre los materiales de origen será un proceso manual que Bárbara realizará al terminar la lámina de _patchwork_, asociando la lámina a los pares resultantes.
