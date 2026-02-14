# Florencia Rojas - Portfolio

Sitio estático para GitHub Pages con dominio propio.

## Deploy en GitHub Pages

1. Sube el repo a GitHub (si no está ya).
2. **Settings** del repo → **Pages**.
3. **Source**: Deploy from a branch.
4. **Branch**: `main` (o `master`), carpeta **/ (root)**.
5. Guarda. En unos minutos el sitio estará en `https://tu-usuario.github.io/florojas/`.

## Dominio propio

1. En **Settings → Pages → Custom domain** escribe tu dominio (ej: `florenciarojas.com` o `www.florenciarojas.com`).
2. Crea el archivo **CNAME** en la raíz con solo el dominio (una línea):
   ```
   florenciarojas.com
   ```
   (Sustituye por tu dominio real.)
3. En tu proveedor de dominio (DonWeb, GoDaddy, Cloudflare, etc.):
   - Para **dominio apex** (ej: `florenciarojas.com`): añade registros **A** apuntando a:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - Para **subdominio www** (ej: `www.florenciarojas.com`): crea un **CNAME** de `www` a `tu-usuario.github.io`.
4. Espera la propagación DNS (puede tardar hasta 24 h). En Pages verás “DNS check successful” cuando esté bien.

## Reemplazar el dominio en el proyecto

Antes o después del deploy, sustituye **`tudominio.com`** por tu dominio real en:

- **index.html**: `canonical`, `og:url`, `og:image`, `twitter:image`.
- **sitemap.xml**: la URL dentro de `<loc>`.
- **robots.txt**: la URL del `Sitemap:`.
- **CNAME**: solo debe contener tu dominio (ej: `florenciarojas.com`).

## SEO y sitemap

- **index.html**: incluye meta description, canonical, Open Graph y Twitter Card.
- **sitemap.xml**: para un sitio de una sola página solo hace falta la URL de la home; ya está configurada.
- **robots.txt**: permite todo e indica la ruta del sitemap.

Opcional: añade una imagen **og-image.jpg** (recomendado 1200×630 px) en la raíz y usa su URL en las meta `og:image` y `twitter:image` para la vista previa en redes.

## Estructura recomendada en la raíz

```
florojas/
├── index.html      ← página principal (obligatorio para GitHub Pages)
├── sitemap.xml
├── robots.txt
├── CNAME           ← tu dominio (ej: florenciarojas.com)
├── .nojekyll       ← evita que Jekyll procese el repo
└── README.md
```

`home.html` puede eliminarse si solo quieres servir `index.html`.
