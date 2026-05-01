# Feature Specification: Catálogo de Calzado Bajo Demanda (Pre-order Inquiry)

**Feature Branch**: `[001-b2c-footwear-inquiry]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Catálogo digital de calzado icónico bajo modelo pre-order, canalizando el interés hacia un servicio de conserjería para gestión personalizada de tallas y pedidos."

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Consulta para Encargo de Calzado (Priority: P1)

Como consumidor consciente, quiero explorar los modelos de calzado (ej. Sandal, Manuela), conocer la historia de sus materiales y solicitar un encargo proporcionando mis datos básicos, para que el taller me contacte personalmente y definamos los detalles técnicos (talla, ajustes) y el pago.

**Why this priority**: Es la base del negocio. Valida el interés en el calzado artesanal y permite un control total sobre la lista de espera de forma manual.

**Independent Test**: Navegar por el catálogo de calzado, seleccionar un modelo y enviar con éxito el formulario de contacto con el contexto del producto seleccionado.

**Acceptance Scenarios**:

1. **Given** que estoy en la página de un modelo de zapato, **When** hago clic en "Iniciar Encargo", **Then** el sistema me dirige al formulario de contacto con el modelo pre-seleccionado.
2. **Given** que envío mi consulta, **When** el sistema confirma el envío, **Then** recibo un mensaje agradeciendo mi interés y asegurando una respuesta humana para gestionar mi pedido.

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: El sistema DEBE presentar una galería visual inmersiva de cada modelo de calzado, destacando la aplicación del **Método Re\_**.
- **FR-002**: El sistema DEBE mostrar claramente la naturaleza del modelo _pre-order_ y los tiempos estimados de artesanía para gestionar expectativas antes del contacto.
- **FR-003**: El sistema DEBE incluir especificaciones sobre la trazabilidad y los materiales de origen del modelo consultado.
- **FR-004**: El sistema DEBE canalizar toda intención de compra hacia el **Unified Concierge Desk** (Feature 6), enviando el contexto del modelo de interés.

### Key Entities

- **Footwear Model**: Atributos: Nombre, Galería de imágenes, Historia del material, Guía de tallas de referencia.
- **Inquiry Lead**: Atributos: Modelo de interés, Nombre del cliente, Email, Talla aproximada, Mensaje/Dudas.

## Success Criteria _(mandatory)_

- **SC-001**: El 100% de las consultas de calzado llegan a la bandeja de entrada del taller con el modelo correctamente identificado.
- **SC-002**: Se mantiene el valor de trato personalizado, respondiendo a cada solicitud con un asesoramiento técnico sobre la talla y materiales.
