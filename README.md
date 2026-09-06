# Polars Playground

Plataforma web interactiva para aprender Polars de forma práctica. El usuario escribe código Python en el navegador y lo ejecuta contra tests automáticos.

**Versión**: 1.12.0 | **Última actualización**: Septiembre 2026

---

## Tecnologías

| Tecnología | Versión | Función |
|------------|---------|---------|
| HTML5 | - | Estructura |
| CSS3 | - | Estilos y responsive |
| JavaScript vanilla | - | Lógica de la aplicación |
| Bootstrap | v5.3.3 | Responsive mobile nav, tabs y layout |
| Pyodide | v0.27.7 | Python en WebAssembly |
| Monaco Editor | v0.45.0 | Editor de código (el mismo de VS Code) |
| Polars | latest | Librería de análisis de datos |
| Service Worker | v5 | Caché de archivos estáticos con estrategia network-first |

---

## Estructura del Proyecto

```
Polars Playground/
├── index.html                    # Página principal
├── principiante.html             # Grid de lecciones principiante
├── intermedio.html               # Grid de lecciones intermedio
├── avanzado.html                 # Grid de lecciones avanzado
├── desafio.html                  # Desafío final (3 retos)
├── lecciones_principiante.html   # Playground principiante (14 lecciones)
├── lecciones_intermedio.html     # Playground intermedio (13 lecciones)
├── lecciones_avanzado.html       # Playground avanzado (13 lecciones)
├── oso_polar.webp                # Logo del oso polar (header + favicon + OG image)
├── png_polars.svg                # Logo de Polars
├── robots.txt                   # Reglas para motores de búsqueda
├── sitemap.xml                  # Mapa del sitio para indexación
├── sw.js                         # Service Worker v5 (network-first)
├── vercel.json                   # Configuración Vercel (estático)
├── .vercelignore                 # Exclusiones Vercel
├── requirements.txt              # Dependencias Python
└── README.md                     # Esta documentación
```

---

## Niveles de Aprendizaje

### Principiante
- **Color**: Verde (#00d4aa) + Morado (#667eea)
- **Lecciones**: 14
- **Temas**: Importar, DataFrame, CSV, select, filter, expresiones, estadísticas, sort, with_columns, group_by, nulls, write_csv, proyecto final

### Intermedio
- **Color**: Naranja (#f39c12)
- **Lecciones**: 13
- **Temas**: Joins (inner/left/right/outer/cross), join múltiple, concatenación, pivot, pivot con agregación, unpivot, parsear fechas, date_range, componentes .dt, lazy API, optimización lazy, chaining de expresiones

### Avanzado
- **Color**: Rojo (#e74c3c)
- **Lecciones**: 13
- **Temas**: Lazy con collect, collect con filtros, head/slice, window functions (.over), rank, shift/diff, rolling windows, SQL con Polars, CTEs en SQL, expresiones when/then, .str, categorical, explode

### Desafío
- **Color**: Morado (#667eea → #764ba2)
- **Retos**: 3
- **Retos**: Limpieza de Datos, Análisis de Ventas, Pipeline Completo

**Total: 40 lecciones + 3 desafíos**

---

## Funcionalidades

### Editor de Código
- Monaco Editor con syntax highlighting para Python
- Números de línea y autocompletado
- Atajos: Ctrl+Enter (ejecutar), Ctrl+S (solución)

### Panel de Salida (Jupyter-style)
- Tablas HTML generadas desde `df.to_dict()` + constructor JS (evita conflictos de estilos)
- Detección automática de DataFrames en el scope
- Salida de texto para `print()` y errores
- Filtro de warnings (Warning, DeprecationWarning, FutureWarning ignorados)

### Sistema de Tests
- Validación en tiempo real
- **Checklist visual** con tests pasados/fallidos (en vez de tracebacks crudos)
- Error detectado al inicio + lista de tests individuales
- Contador de tests pasados

### Guía Educativa
- **Modal de guía** con contenido por nivel (principiante, intermedio, avanzado)
- Cada guía cubre las funciones y conceptos del nivel correspondiente
- Acceso desde el botón "📖 Guía de Funciones"
- Se cierra con Escape o clic fuera del modal

### Progreso
- Guarda en localStorage
- Indicadores visuales por nivel
- Persiste entre sesiones

### Responsive (Mobile)
- Bootstrap 5.3.3 en todas las páginas de lecciones
- Mobile Nav: 3 tabs (Instrucciones, Editor, Resultado)
- Animación de paneles

### Header
- Logo: oso polar blanco (`oso_polar.webp`) con filtro CSS `brightness(0) invert(1)`
- Barra de progreso por nivel

---

## Almacenamiento Local

| Clave | Contenido |
|-------|-----------|
| `polarsCompleted` | Lecciones principiante completadas |
| `polarsCompletedIntermedio` | Lecciones intermedio completadas |
| `polarsCompletedAvanzado` | Lecciones avanzado completadas |
| `polarsDesafioCompleted` | Desafíos completados |

---

## Instalación

Es un proyecto **100% estático**. Para desarrollo local:

```bash
# Opción 1: Python
python -m http.server 8000

# Opción 2: Node.js
npx serve .
```

Luego abre `http://localhost:8000` en tu navegador.

**Importante**: Pyodide y los Service Workers no funcionan con el protocolo `file://`. Siempre usa un servidor local.

**Para producción**: Sube los archivos a Vercel, Netlify, GitHub Pages o cualquier hosting estático.

---

## Cómo Funciona

1. El usuario selecciona un nivel (o el Desafío)
2. Elige una lección del grid
3. Pyodide + polars se cargan en background (desde CDN)
4. Escribe código en el editor Monaco
5. Puede consultar la **guía educativa** con "📖 Guía de Funciones"
6. Los DataFrames se muestran como tablas HTML (generadas desde `to_dict()`)
7. Los `print()` aparecen como texto
8. Ejecuta tests con Ctrl+Enter
9. Si hay un error, se muestra el checklist de tests (no el traceback crudo)
10. Si pasa, se marca como completada
11. El progreso se guarda automáticamente en localStorage
12. En visitas posteriores, la caché del Service Worker acelera la carga
13. Los motores de búsqueda indexan el sitio mediante meta tags, Open Graph y sitemap.xml

---

## SEO y Optimización para Motores de Búsqueda

### Meta Tags por Página

| Página | Title | Description | robots |
|--------|-------|-------------|--------|
| `index.html` | Polars Playground - Aprende Polars de Forma Interactiva | Aprende Polars... editor en navegador, tests automáticos... | `index, follow` |
| `principiante.html` | Nivel Principiante - Polars Playground | 14 lecciones interactivas... select, filter, group_by... | `index, follow` |
| `intermedio.html` | Nivel Intermedio - Polars Playground | 13 lecciones... joins, pivots, fechas y Lazy API | `index, follow` |
| `avanzado.html` | Nivel Avanzado - Polars Playground | 13 lecciones avanzadas... window functions, SQL... | `index, follow` |
| `desafio.html` | Desafío - Polars Playground | 3 desafíos prácticos... limpieza de datos... | `index, follow` |
| `lecciones_*.html` | Lecciones [Nivel] - Polars Playground | Playground interactivo... | `noindex, nofollow` |

### Open Graph (Redes Sociales)

Todas las páginas principales incluyen:
- `og:title` — Título descriptivo
- `og:description` — Descripción concisa (155 caracteres)
- `og:type` — `website`
- `og:url` — URL canónica
- `og:image` — Logo del oso polar (`oso_polar.webp`)
- `og:site_name` — "Polars Playground"
- `og:locale` — `es_ES`

### Twitter Card

- `twitter:card` — `summary_large_image`
- `twitter:title` — Igual a og:title
- `twitter:description` — Igual a og:description
- `twitter:image` — Logo del oso polar

### JSON-LD (Schema.org)

Estructura de datos en `index.html`:
```json
{
    "@context": "https://schema.org",
    "@type": "WebApplication",
    "name": "Polars Playground",
    "description": "...",
    "applicationCategory": "EducationalApplication",
    "operatingSystem": "Web Browser",
    "offers": { "@type": "Offer", "price": "0", "priceCurrency": "USD" },
    "inLanguage": "es"
}
```

### Archivos SEO

| Archivo | Propósito |
|---------|-----------|
| `robots.txt` | Permite indexación de grid pages, bloquea lecciones |
| `sitemap.xml` | 5 URLs priorizadas con `lastmod` y `changefreq` |
| `oso_polar.webp` | Favicon + imagen para OG/Twitter cards |

### Jerarquía de Prioridad (sitemap.xml)

```
/ (1.0) > principiante (0.9) ≈ intermedio (0.9) ≈ avanzado (0.9) > desafio (0.8)
```

### Accesibilidad (SEO-friendly)

- `lang="es"` en todas las páginas
- `alt` descriptivo en todas las imágenes
- Títulos jerárquicos (`<h1>`, `<h2>`, `<h3>`)
- Contraste de colores WCAG AA
- Responsive design (mobile-first)

### Notas de Implementación

- Las páginas de lecciones (`lecciones_*.html`) usan `noindex` porque son el entorno interactivo, no contenido informativo
- El `canonical` apunta a la URL de producción en Vercel
- El favicon se reutiliza como imagen de OG/Twitter (consistencia visual)
- Los meta descriptions están optimizados a ≤155 caracteres para Google

---

## Notas Técnicas

### DataFrame Rendering
Los DataFrames se renderizan usando `df.to_dict()` en Python + un constructor de tablas HTML en JavaScript. Esto evita conflictos de estilos que causaba `df.write_html()`.

### Pyodide + Polars
- Pyodide v0.27.7 carga Polars desde su lock file
- `pl.scan_csv()` no funciona en WASM (causa panic de Rust) — se usa `df.lazy()` como alternativa
- `pl.date_range()` requiere objetos `date` de Python, no strings
- `str.replace()` usa regex por defecto — caracteres especiales como `$` necesitan escape

### Service Worker
- Estrategia **network-first** (v5)
- Cachea: HTML, CSS, JS, fuentes, CDN de Pyodide y Monaco
- Permite actualizaciones sin limpiar caché manualmente

---

*Versión 1.12.0 - Septiembre 2026*
