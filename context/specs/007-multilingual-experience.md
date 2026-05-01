# Feature Specification: Experiencia Multilingüe (Bilingual Catalog)

**Feature Branch**: `[007-multilingual-experience]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Implementar soporte multiidioma (Español e Inglés) para todo el ecosistema digital, asegurando que la narrativa del Método Re\_ y el servicio de conserjería sean accesibles para el mercado internacional."

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Navegación y Lectura en Idioma Preferido (Priority: P1)

Como usuario internacional (B2C o Institucional), quiero poder acceder a toda la narrativa de la marca, catálogos de producto y detalles del Método Re\_ en inglés, para comprender el valor artesanal y técnico sin barreras lingüísticas antes de iniciar un contacto[cite: 6, 11, 12].

**Why this priority**: Es fundamental para la expansión europea definida en la hoja de ruta. Sin una versión en inglés, el servicio de conserjería para clientes fuera de España pierde efectividad y confianza.

**Independent Test**: Navegar por la web, cambiar el selector de idioma y verificar que el 100% del contenido (descripciones, etiquetas y menús) se traduce correctamente sin perder la estética minimalista.

**Acceptance Scenarios**:

1. **Given** que el usuario entra en la web desde un navegador configurado en inglés, **When** la página carga, **Then** se muestra preferentemente la versión en inglés.
2. **Given** que el usuario cambia de idioma manualmente, **When** hace clic en el selector, **Then** permanece en la misma página/producto que estaba visualizando pero en el nuevo idioma.

---

### User Story 2 - Solicitud de Contacto en Contexto Lingüístico (Priority: P2)

Como cliente internacional, quiero que el sistema de contacto unificado refleje mi preferencia de idioma, para sentirme cómodo expresando mis dudas en inglés y recibir una respuesta en el mismo idioma por parte del taller.

**Why this priority**: Mantiene la coherencia del trato de "guante blanco". Si el cliente solicita información en inglés, la estructura de la consulta recibida por el taller debe indicar este contexto para facilitar la respuesta personalizada.

**Independent Test**: Enviar una solicitud desde la versión en inglés y verificar que el "Unified Lead" recibido por el taller identifica el idioma de origen.

**Acceptance Scenarios**:

1. **Given** que el usuario envía un formulario desde la versión en inglés, **When** el taller recibe el email, **Then** el asunto o metadatos del correo indican claramente "English Inquiry".

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: El sistema DEBE ofrecer una traducción completa y profesional (no automática por defecto) de la narrativa del **Método Re\_**, descripciones de productos y formaciones.
- **FR-002**: El sistema DEBE incluir un selector de idioma intuitivo y minimalista que no rompa la estética de portafolio.
- **FR-003**: El sistema DEBE persistir la elección de idioma del usuario durante toda la sesión de navegación.
- **FR-004**: El sistema DEBE adaptar las etiquetas y campos del formulario de conserjería al idioma seleccionado.
- **FR-005**: El sistema DEBE indexar ambas versiones (SEO) para permitir que clientes internacionales encuentren a **Re\_** mediante términos de búsqueda en inglés.

### Key Entities

- **Content Translation**: Representa cada fragmento de texto (copy) de la web. Atributos: Clave identificadora, Texto ES, Texto EN.
- **Language Selector**: Componente de interfaz para la alternancia de idiomas.

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: El 100% de las páginas estáticas del catálogo y formación cuentan con su versión equivalente en inglés.
- **SC-002**: Incremento en la recepción de solicitudes (leads) provenientes de fuera de España en la bandeja de entrada del taller.

## Assumptions

- Se asume que Bárbara León o el equipo de Re\_ gestionarán la comunicación manual (correos de respuesta) en inglés para los clientes internacionales.
- Se asume que las traducciones serán revisadas manualmente para asegurar que el tono "didáctico pero sofisticado" se mantiene en ambos idiomas.
