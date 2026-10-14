# O Ferro Parrilla — web

Web del restaurante **O Ferro Parrilla**, asador de carnes a la brasa en Verín (Ourense).

**Estado:** en desarrollo, aún sin publicar oficialmente.

**Vista previa:** <https://juanito2003.github.io/oferro-parrilla/>

## Qué incluye

Una sola página con navegación por secciones:

- **Portada** con valoración y llamada a reservar.
- **Nosotros** y **La parrilla**: historia del local y la brasa.
- **Especialidades**: platos destacados con foto.
- **Carta** por pestañas (entrantes, carnes a la brasa, pescados y postres).
- **Reseñas** de clientes.
- **Reservas** por teléfono, también para grupos y celebraciones.
- **Ubicación** y horario.
- Botón flotante de llamada en móvil.

## Tecnología

- HTML, CSS y JavaScript sin frameworks ni paso de build: todo está en `index.html`.
- SEO: etiquetas Open Graph para compartir en redes, datos estructurados JSON-LD, `sitemap.xml` y `robots.txt`.
- Iconos para navegador y móvil (`favicon.ico`, `favicon-16x16.png`, `favicon-32x32.png`, `apple-touch-icon.png`).
- Accesibilidad: textos alternativos en todas las fotos, menú y pestañas con atributos ARIA, valoraciones con texto para lectores de pantalla.
- Vista previa en GitHub Pages desde la rama `main`.

## Ver en local

Con Node.js 16 o superior:

```bash
npm start      # servidor en http://localhost:3000
npm run dev    # igual, pero recarga la página al guardar cambios
```

Sin Node.js también sirve Python:

```bash
python3 -m http.server 3000
```

## Estructura

```
oferro-parrilla/
├── index.html          La web completa (HTML, CSS y JS)
├── *.jpg               Fotos de platos y comedores
├── logo.jpg            Logo
├── og-image.jpg        Imagen al compartir en redes (1200x630)
├── favicon*, apple-touch-icon.png
├── sitemap.xml, robots.txt
└── package.json        Scripts para el servidor local
```

## Añadir o cambiar fotos

Para que la web cargue rápido en móvil:

- Lado largo de **1200 px como máximo** y calidad JPEG en torno a **80**.
- En la etiqueta `<img>`, indica `width` y `height` con la proporción de la foto (evita saltos al cargar), un `alt` que describa lo que se ve y `loading="lazy"` si no está en la portada.

## Vista previa

Cada push a `main` actualiza la vista previa en GitHub Pages en uno o dos minutos.
