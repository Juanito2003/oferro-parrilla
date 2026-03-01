# O Ferro Parrilla — Web

## Requisitos
- Node.js instalado (v16 o superior): https://nodejs.org

## Cómo ejecutar en local

```bash
# 1. Entrar en la carpeta
cd oferro

# 2. Arrancar el servidor (sin instalar nada)
npm start
# → Abre http://localhost:3000 en el navegador

# 3. Alternativa con recarga automática al guardar cambios
npm run dev
# → Abre http://localhost:3000 y se recarga solo al editar
```

## Estructura
```
oferro/
├── index.html       ← La web completa
├── package.json     ← Configuración npm
├── *.jpg / *.png    ← Imágenes del restaurante
└── README.md
```

## Publicar en producción

### Netlify (recomendado, gratis)
Arrastra la carpeta entera a https://app.netlify.com/drop

### Con dominio propio
1. Compra dominio en https://dondominio.com o similar
2. Apunta el dominio a Netlify desde el panel DNS
3. Netlify gestiona el HTTPS automáticamente

### VPS / servidor propio
```bash
# Instalar serve globalmente
npm install -g serve

# Arrancar en producción (puerto 80)
serve . --listen 80
```
