# Feature Specification: Estancias Formativas para Profesionales (Residency Inquiry)

**Feature Branch**: `[004-professional-residency-inquiry]`  
**Created**: 2026-05-01  
**Status**: Draft  
**Input**: User description: "Feature 4: Estancias Formativas para Profesionales (Residency Inquiry)"

## User Scenarios & Testing _(mandatory)_

### User Story 1 - Exploración y Solicitud de Inmersión Técnica (Priority: P1)

Como Profesional o Estudiante de Diseño de Moda/Calzado, quiero explorar el programa de estancias formativas en el taller de Re\_ para poder solicitar una inmersión técnica personalizada que me permita dominar el patronaje circular, el suprareciclaje y la aplicación práctica del Método Re\_.

**Why this priority**: Este servicio monetiza el alto nivel técnico de Bárbara León y el espacio del taller para un nicho muy específico (profesionales B2B o sector académico avanzado). Posiciona a la marca como líder e innovadora en el sector. Al ser un servicio de muy alto valor (ticket alto), requiere un proceso de evaluación mutua (vetting) que encaja perfectamente con el modelo de conserjería.

**Independent Test**: Puede probarse navegando por la información dedicada a las estancias para profesionales, revisando las áreas de especialización ofrecidas (desmontaje, patronaje circular, ensamblaje) y enviando una solicitud formal a través del sistema de contacto que incluya el perfil profesional del solicitante.

**Acceptance Scenarios**:

1. **Given** que el usuario profesional se encuentra en la sección de estancias formativas, **When** lee la propuesta de valor centrada en el aprendizaje técnico avanzado, **Then** el sistema le presenta una opción clara para "Solicitar Estancia / Iniciar Evaluación".
2. **Given** que el usuario accede a iniciar la solicitud, **When** se le presenta el formulario de conserjería, **Then** se le solicita, además de sus datos de contacto, información sobre su perfil (ej. enlace a portafolio o motivación) y fechas deseadas, iniciando un diálogo de evaluación directamente con Bárbara León.

### Edge Cases

- ¿Qué ocurre si un usuario sin la base técnica necesaria solicita esta estancia profesional? (La fricción intencional de requerir un portafolio o motivación en el formulario actúa como un filtro natural. Durante el contacto humano posterior, el equipo puede redirigir con elegancia a este perfil hacia los talleres de ocio creativo de la Feature 3).
- ¿Cómo se abordan las necesidades logísticas de estudiantes internacionales (alojamiento, visados para Sevilla)? (La web no necesita automatizar esto. El sistema de conserjería permite que, una vez validado el perfil por correo, el taller envíe un dosier PDF en formato "guante blanco" con recomendaciones locales y detalles logísticos).

## Requirements _(mandatory)_

### Functional Requirements

- **FR-001**: El sistema DEBE mostrar un enfoque visual más técnico y metodológico, destacando el proceso de deconstrucción, el caos del residuo y la estandarización del Método Re\_, manteniendo la estética de lujo silencioso.
- **FR-002**: El sistema DEBE exponer las competencias clave que se adquieren durante la estancia (ej. nicho del upcycling textil, metodologías de economía circular aplicada).
- **FR-003**: El sistema DEBE dejar claro que se trata de un programa de mentoría altamente personalizado, presencial (Sevilla) y sujeto a disponibilidad y evaluación del perfil.
- **FR-004**: El sistema DEBE canalizar la intención hacia el contacto unificado, adaptando la solicitud para capturar el _background_ profesional del usuario y sus objetivos de aprendizaje específicos.

### Key Entities

- **Residency Program (Programa de Estancia)**: Representa el servicio de inmersión. Atributos clave: Propuesta de valor técnico, Áreas de especialización, Metodología (Método Re\_).
- **Residency Inquiry (Solicitud de Estancia)**: Representa la candidatura del profesional. Atributos clave: Información de contacto, Perfil profesional (portafolio/CV), Objetivos de aprendizaje, Fechas tentativas.

## Success Criteria _(mandatory)_

### Measurable Outcomes

- **SC-001**: Número de solicitudes cualificadas (candidaturas viables con portafolio/perfil técnico) recibidas por trimestre.
- **SC-002**: Tasa de conversión de solicitudes iniciales a estancias formativas confirmadas y agendadas.

## Assumptions

- Se asume que el usuario objetivo comprende que no está comprando un "curso enlatado", sino aplicando para una mentoría técnica exclusiva que requiere una validación humana previa.
- Se asume que la comunicación posterior vía correo electrónico será altamente personalizada y enfocada en diseñar un plan de estudios a medida para el profesional aceptado.
