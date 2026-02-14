# Florencia Rojas - Portfolio

Sitio estático para GitHub Pages con dominio propio.

---

## 1. Deploy en GitHub Pages

1. **Sube el repo** a GitHub (crea el repo en github.com y haz push):
   ```bash
   git add .
   git commit -m "Deploy inicial"
   git branch -M main
   git remote add origin https://github.com/TU-USUARIO/florojas.git
   git push -u origin main
   ```
2. En GitHub: **Settings** del repositorio → **Pages** (menú izquierdo).
3. En **Build and deployment**:
   - **Source**: Deploy from a branch
   - **Branch**: `main` → carpeta **/ (root)** → Save
4. En 1–2 minutos el sitio estará en:  
   `https://TU-USUARIO.github.io/florojas/`

---

## 2. Conectar Namecheap con GitHub Pages

### Paso A — Dominio en GitHub

1. En el repo: **Settings → Pages**.
2. En **Custom domain** escribe tu dominio exacto, por ejemplo:
   - `tudominio.com` (sin www), **o**
   - `www.tudominio.com` (con www)
3. Clic en **Save**.
4. El archivo **CNAME** en la raíz del proyecto debe tener **solo** ese dominio (una línea, sin `https://`). Ejemplo:
   ```
   tudominio.com
   ```
   Si lo cambias, haz commit y push.

### Paso B — DNS en Namecheap

1. Entra en **Namecheap** → **Domain List** → al lado de tu dominio clic en **Manage**.
2. Abre la pestaña **Advanced DNS**.

**Opción A — Usar el dominio sin www** (ej: `tudominio.com`)

- Si hay registros de “URL Redirect” o “Parking” para @ o www, bórralos o desactívalos.
- Añade **4 registros tipo A**:

| Type | Host | Value           | TTL  |
|------|------|-----------------|------|
| A    | @    | 185.199.108.153 | 300  |
| A    | @    | 185.199.109.153 | 300  |
| A    | @    | 185.199.110.153 | 300  |
| A    | @    | 185.199.111.153 | 300  |

- (Opcional) Para que **www** redirija al dominio sin www, añade un CNAME:  
  Host: **www**, Value: **TU-USUARIO.github.io** (tu usuario de GitHub).

**Opción B — Usar www** (ej: `www.tudominio.com`)

- Añade **1 registro CNAME**:
  - Host: **www**
  - Value: **TU-USUARIO.github.io** (tu usuario de GitHub, sin `https://` ni `/florojas`)
- Para que el dominio sin www también funcione, añade los **4 registros A** de la tabla de arriba (Host: `@`).

3. Guarda en Namecheap. La propagación DNS puede tardar **unos minutos hasta 24 horas**.

### Paso C — Comprobar en GitHub

1. Vuelve a **Settings → Pages** en el repo.
2. Cuando el DNS esté bien verás **DNS check successful** y podrás marcar **Enforce HTTPS**.
3. Activa **Enforce HTTPS** para que el sitio cargue con `https://`.

---

## 3. Dominio en el proyecto (SEO)

Sustituye **`tudominio.com`** por tu dominio real en:

- **CNAME**: una línea con el dominio.
- **index.html**: meta `canonical`, `og:url`, `og:image`, `twitter:image`.
- **sitemap.xml**: la URL en `<loc>`.
- **robots.txt**: la línea `Sitemap:`.

---

## SEO y sitemap

- **index.html**: incluye meta description, canonical, Open Graph y Twitter Card.
- **sitemap.xml**: una sola URL (la home); ya está configurada.
- **robots.txt**: permite todo e indica la ruta del sitemap.

Opcional: añade **og-image.jpg** (1200×630 px) en la raíz y usa su URL en las meta `og:image` y `twitter:image` para la vista previa en redes.

## Estructura en la raíz

```
florojas/
├── index.html
├── favicon.ico     ← favicon (pestaña del navegador). Opcional: favicon-32x32.png, favicon-16x16.png, apple-touch-icon.png
├── sitemap.xml
├── robots.txt
├── CNAME           ← tu dominio (ej: florenciarojas.com)
├── .nojekyll
├── images/
│   ├── hero/       ← foto1.jpg, foto2.jpg
│   └── portfolio/  ← 01-growth.jpg, 02-flyers.jpg, etc.
└── README.md
```
