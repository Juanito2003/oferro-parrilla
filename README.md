# O Ferro Parrilla — web

[![Validar HTML](https://github.com/Juanito2003/oferro-parrilla/actions/workflows/validar-html.yml/badge.svg)](https://github.com/Juanito2003/oferro-parrilla/actions/workflows/validar-html.yml)

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
- HTML validado con `html-validate` (reglas en `.htmlvalidate.json`) en cada push y pull request con GitHub Actions.
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

Cada foto está en JPEG (respaldo) y en WebP en varios anchos, y la página usa `<picture>` para que cada móvil u ordenador descargue solo el tamaño que necesita:

```html
<picture>
  <source type="image/webp"
          srcset="foto-400.webp 400w, foto-800.webp 800w, foto.webp 1200w"
          sizes="(max-width: 600px) 92vw, 380px">
  <img src="foto.jpg" width="1200" height="900" alt="Qué se ve en la foto" loading="lazy">
</picture>
```

Para una foto nueva:

1. Guárdala en JPEG con el lado largo de **1200 px como máximo** y calidad en torno a **80**.
2. Genera las versiones WebP de 400 y 800 px de ancho y la de tamaño completo (`cwebp -q 78 -resize 400 0 foto.jpg -o foto-400.webp`; la de 800 igual, y la completa sin `-resize`). Si la foto mide menos de 800 px de ancho, sáltate esa versión.
3. En `sizes`, pon el ancho al que se ve la foto en la página. Copia el de otra foto del mismo bloque.
4. En el `<img>`, indica `width` y `height` con la proporción de la foto (evita saltos al cargar), un `alt` que describa lo que se ve y `loading="lazy"` si no está en la portada.

## Vista previa

Cada push a `main` actualiza la vista previa en GitHub Pages en uno o dos minutos.
