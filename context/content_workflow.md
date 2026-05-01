# Guía de Gestión de Contenidos y Assets (Workflow)

**Última actualización:** 2026-05-01  
**Propósito:** Definir el flujo de trabajo estándar para trasladar el material visual (fotografías y vídeos) desde las sesiones en el taller (Google Drive) hasta el catálogo en vivo (Astro), manteniendo el repositorio de código ligero y asegurando tiempos de carga ultrarrápidos mediante Cloudinary.

## 1. La Arquitectura Visual (Por qué lo hacemos así)

Para mantener el principio de "Rendimiento y Estética de Lujo Silencioso", nuestro repositorio de código en GitHub/Vercel **NO debe almacenar imágenes ni vídeos de alta resolución**.
Todo el material de producto o del taller debe servirse a través de **Cloudinary** (nuestro CDN). Cloudinary optimiza automáticamente el peso, la resolución y el formato del archivo multimedia en milisegundos según el dispositivo del cliente.

## 2. Flujo de Trabajo (Step-by-Step Workflow)

### Paso A: Selección y Nomenclatura (Google Drive -> Local)

1. Selecciona las fotos y clips de vídeo definitivos desde tu Google Drive.
2. Descárgalos a tu ordenador y **renómbralos** antes de subirlos a la nube.
3. **Regla de Nomenclatura (Naming Convention):**
   - Usar solo minúsculas.
   - Separar palabras con guiones medios (`-`), nunca espacios ni guiones bajos.
   - Incluir la palabra clave del producto y el tipo de plano por motivos de SEO.
   - _Ejemplo Fotografía:_ `sandal-upcycling-cuero-detalle-01.jpg`
   - _Ejemplo Vídeo:_ `metodo-costura-proceso-taller.mp4`

### Paso B: Subida a Cloudinary

1. Inicia sesión en el panel de Cloudinary (Media Library).
2. Navega a la carpeta correspondiente para mantener el orden. Estructura de carpetas recomendada basada en el **Método Re\_**:
   - `/productos/calzado/metodo-sandal/`
   - `/productos/calzado/metodo-manuela/`
   - `/productos/calzado/metodo-costura/`
   - `/productos/calzado/metodo-saco/`
   - `/productos/bolsos/zurda/`
   - `/taller-y-procesos/fotografia/`
   - `/taller-y-procesos/videos/`
   - `/ui-elements/` (Para logos o fondos de la web).
3. Arrastra y suelta los archivos renombrados en la carpeta correspondiente.

### Paso C: Extracción del Enlace Optimizado (El "Truco" de Rendimiento)

1. Una vez subido el archivo a Cloudinary, haz clic en el icono de copiar URL (Copy URL).
2. **Para Fotografías:**
   - La URL base será `/image/upload/`.
   - **CRÍTICO:** Asegúrate de insertar los parámetros `f_auto,q_auto` para que Cloudinary reduzca el peso automáticamente.
   - _Enlace final:_ `[https://res.cloudinary.com/tu-usuario/image/upload/f_auto,q_auto/v168000000/productos/calzado/metodo-sandal/sandal-01.jpg](https://res.cloudinary.com/tu-usuario/image/upload/f_auto,q_auto/v168000000/productos/calzado/metodo-sandal/sandal-01.jpg)`
3. **Para Vídeos:**
   - La URL base será `/video/upload/`.
   - **CRÍTICO:** Los vídeos también usan la magia de `f_auto,q_auto` para adaptarse a la conexión del usuario sin tirones.
   - _Enlace final:_ `[https://res.cloudinary.com/tu-usuario/video/upload/f_auto,q_auto/v168000000/taller-y-procesos/videos/cosido-manual.mp4](https://res.cloudinary.com/tu-usuario/video/upload/f_auto,q_auto/v168000000/taller-y-procesos/videos/cosido-manual.mp4)`

### Paso D: Integración en la Plantilla de Astro

Dependiendo de si es foto o vídeo, la integración en tus archivos Markdown (`.md` / `.mdx`) o HTML varía:

**1. Insertar Fotografías (en el Frontmatter o cuerpo):**

```markdown
---
title: "Modelo Sandal"
description: "Calzado artesanal suprareciclado mediante patronaje circular."
coverImage: "https://res.cloudinary.com/tu-usuario/image/upload/f_auto,q_auto/v168000000/productos/calzado/metodo-sandal/sandal-portada.jpg"
---
```

**2. Insertar Vídeos (en el cuerpo del contenido):**
Para vídeos de fondo o clips de proceso que quieras que se reproduzcan solos y sin sonido (estilo GIF pero con calidad HD), usa la etiqueta estándar de HTML5 dentro de Astro:

```html
<video width="100%" autoplay loop muted playsinline>
  <source
    src="https://res.cloudinary.com/tu-usuario/video/upload/f_auto,q_auto/v168000000/taller-y-procesos/videos/cosido-manual.mp4"
    type="video/mp4"
  />
  Tu navegador no soporta la reproducción de vídeo.
</video>
```

## 3. Límites y Buenas Prácticas

- **Nunca subas RAWs o TIFFs:** Exporta desde tu editor (Lightroom/Photoshop) en JPG o PNG de alta calidad a un máximo de 2500px de ancho antes de subir a Cloudinary.
- **Optimización en Origen para Vídeos:** Aunque Cloudinary comprime los vídeos, no subas un archivo original de 2GB grabado en 4K sin comprimir. Exporta tus vídeos desde Premiere/CapCut en formato MP4 (H.264), resolución 1080p, para no agotar tu límite de almacenamiento gratuito en la nube rápidamente.
- **Evita los GIFs:** Si tienes un clip corto del taller, súbelo siempre como `.mp4` y reprodúcelo en bucle (`loop muted`) como en el ejemplo anterior. Los GIFs son muy pesados, consumen muchos datos y arruinan la percepción de "lujo silencioso" por su baja calidad de color.
