# Versatech Ingeniería — Sitio Web Oficial

Landing page interactiva para **Versatech Ingeniería**: soluciones de electrónica a medida, automatización industrial, diseño de PCB, domótica, robótica educativa, desarrollo web y soporte técnico.

## Estructura del Proyecto

| Archivo / Carpeta | Descripción |
| --- | --- |
| `index.html` | Página principal de producción con metadatos SEO, Open Graph y soporte responsive completo. |
| `Versatech Ingeniería.dc.html` | Documento fuente editable en el canvas de diseño (`.dc.html`). |
| `support.js` | Runtime interactivo (`dc-runtime`) que monta la plantilla reactiva. |
| `image-slot.js` | Componente de soporte para ranuras y persistencia visual de imágenes. |
| `assets/` | Videos optimizados en bucle (`.mp4`) e isotipo/logotipo oficial (`versatech-logo.jpeg`). |
| `uploads/` | Material multimedia original sin procesar (excluido en `.vercelignore`). |
| `cambios/` | Carpeta local para respaldos, pruebas o nuevos borradores de diseño. |
| `vercel.json` | Configuración de Vercel con rutas limpias y caché estático optimizado. |

## Desarrollo Local

Para probarlo localmente, sirve el directorio con un servidor HTTP:

```bash
npx serve .
# Abrir http://localhost:3000
```

## Despliegue en Vercel

Sitio estático sin etapa de compilación pesada:

```bash
vercel --prod
```
