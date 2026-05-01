# Feature Specification: E-learning Hub (LMS Platform)

**Feature Branch**: `[005-elearning-hub]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "E-learning Hub: La plataforma de consumo de cursos online (LMS) para cuando lances tu formación digital."

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Comprar y acceder automáticamente a un curso online (Priority: P1)

Como estudiante de diseño o aficionado internacional que no puede viajar a Sevilla, quiero comprar el curso de "Introducción al upcycling y patronaje circular", pagar online y recibir acceso inmediato al contenido en video, para poder empezar a aprender a mi propio ritmo al instante.

**Why this priority**: Es la base de la monetización de la línea de E-learning. El objetivo principal es generar un flujo de ingresos totalmente pasivo (2-3 ventas/mes en su lanzamiento) con cero fricción administrativa para Bárbara.

**Independent Test**: Configurar un curso de prueba con precio real, realizar el proceso de compra (pago con tarjeta), y verificar que el sistema crea la cuenta de usuario, le asigna el curso y le redirige al panel de estudiante sin intervención manual.

**Acceptance Scenarios**:

1. **Given** que estoy en la _landing page_ del curso online, **When** hago clic en "Comprar curso" y completo el pago, **Then** mi cuenta se crea automáticamente y recibo un email con mis credenciales de acceso.
2. **Given** que he iniciado sesión por primera vez, **When** accedo a mi "Panel de Estudiante", **Then** veo el curso desbloqueado y listo para ser reproducido.

---

### User Story 2 - Consumir contenido estructurado y hacer seguimiento del progreso (Priority: P1)

Como alumno inscrito, quiero poder navegar por un temario estructurado en módulos y lecciones, ver videos de alta calidad de los procesos en el taller de Re\_, descargar plantillas de patronaje (PDFs) y ver mi barra de progreso para saber exactamente por dónde me quedé en mi última sesión.

**Why this priority**: Garantiza una experiencia de usuario (UX) _premium_ acorde a la marca. Un aprendizaje intuitivo y de alta calidad reduce las peticiones de reembolso y fomenta excelentes reseñas (prueba social).

**Independent Test**: Acceder a un curso activo, ver un video completo, marcar la lección como "Completada" y verificar que la barra de progreso general aumenta y se desbloquea la siguiente lección.

**Acceptance Scenarios**:

1. **Given** que estoy dentro de una lección, **When** termino de ver el video y hago clic en "Completar y Continuar", **Then** el sistema guarda mi progreso y me lleva a la siguiente lección del módulo.
2. **Given** que una lección requiere material de apoyo, **When** reviso la parte inferior del reproductor de video, **Then** encuentro un botón claro para descargar los archivos de patronaje asociados.

---

### User Story 3 - Acceso masivo para B2B Educativo (Universidades/Escuelas) (Priority: P2)

Como coordinador de una Universidad o Escuela de Diseño que ha contratado los servicios de Re\_, quiero poder distribuir un código de acceso o enlace privado a mis alumnos para que puedan registrarse en el E-learning de forma gratuita (ya que la institución ha pagado el paquete previamente).

**Why this priority**: Responde al objetivo de "Formación institucional (B2B Educativo)" de la hoja de ruta. Permite paquetizar el E-learning como un producto B2B de alto ticket para instituciones.

**Independent Test**: Generar un cupón de 100% de descuento limitado a 30 usos. Realizar el registro como alumno usando ese cupón y verificar que el _checkout_ se salta la pasarela de pago y da acceso directo.

**Acceptance Scenarios**:

1. **Given** que tengo un código proporcionado por mi universidad, **When** lo aplico en el carrito de compra del curso, **Then** el total se reduce a 0€ y puedo completar el registro sin introducir tarjeta de crédito.

### Edge Cases

- What happens when un usuario comparte sus credenciales de inicio de sesión con 10 compañeros de clase para no pagar licencias adicionales? (Necesidad de control de sesiones concurrentes).
- How does system handle la protección del contenido en video contra descargas no autorizadas (piratería del método Re\_)?
- What happens when un usuario solicita un reembolso bajo la política de garantía de 14 días, pero el sistema detecta que ya ha consumido el 100% del contenido y descargado todos los patrones?

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: System MUST gestionar el acceso restringido (_paywall_) al contenido de video y documentos, permitiendo el acceso solo a usuarios con una inscripción (`Enrollment`) activa y pagada.
- **FR-002**: System MUST rastrear y persistir el progreso de visualización del usuario a nivel de lección (Completado / No completado) y mostrarlo visualmente (ej. "Progreso: 45%").
- **FR-003**: System MUST soportar la incrustación de videos de alta calidad alojados en plataformas de _streaming_ externas seguras (para no sobrecargar el servidor principal de la web).
- **FR-004**: System MUST permitir la subida y descarga segura de archivos adjuntos (PDFs, imágenes de esquemas de _patchwork_, guías de materiales) por cada lección.
- **FR-005**: System MUST generar automáticamente un certificado digital [NEEDS CLARIFICATION: ¿Es relevante para nuestro público objetivo generar un PDF con su nombre y el logo de Re_ al completar el 100% del curso, o es innecesario para este nicho artesanal?].

### Key Entities

- **Course**: El contenedor principal del producto educativo (ej. "Introducción al Upcycling de Calzado"). Tiene precio, descripción y un temario asociado.
- **Module / Lesson**: La estructura jerárquica del contenido. Una _Lesson_ contiene un ID de video externo, texto explicativo y archivos adjuntos.
- **CourseEnrollment**: La relación entre un `User` (Alumno) y un `Course`. Almacena el progreso total, la fecha de compra y el historial de lecciones completadas.

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: Ventas pasivas: Alcanzar el objetivo de la hoja de ruta de **2 a 3 ventas mensuales** de forma completamente automatizada en el trimestre de lanzamiento.
- **SC-002**: _Zero-touch onboarding_: El **100%** de los alumnos online pueden comprar, crear su cuenta y empezar a ver el curso sin requerir asistencia por email o WhatsApp por parte del taller.
- **SC-003**: Finalización del curso: Mantener una tasa de finalización (_completion rate_) superior al **30%** (indicador de que el contenido es valioso, digerible y está bien estructurado en la plataforma).

## Assumptions

- Se asume que los videos pesados del curso no se alojarán en el propio servidor web, sino que se utilizará una plataforma de alojamiento de video profesional (como Vimeo Pro, Mux o similar) con restricciones de dominio para evitar que los videos se reproduzcan fuera de la web de Re\_.
- Se asume que el E-learning es un formato 100% asíncrono (grabado). Las correcciones en vivo, el _feedback_ personalizado sobre los proyectos de los alumnos o las tutorías 1 a 1 no están incluidas en esta funcionalidad base.
- Se asume que el público objetivo tiene una conexión a internet de banda ancha suficiente para consumir contenido en video de alta resolución sin problemas de carga continuos.
