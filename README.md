# DT SPORT — Catálogo Digital

Catálogo digital para una tienda de calzado deportivo, con carrito de compras y envío de pedidos por WhatsApp. Es un sitio **100% estático** (HTML, CSS y JavaScript puro): no necesita servidor, base de datos ni pagos en línea. Funciona directamente en **GitHub Pages**.

> ⚠️ **IMPORTANTE — Datos de demostración**
> Los 8 productos, precios, tallas e imágenes que trae este proyecto son **datos de ejemplo (demo)**, creados solo para que el catálogo funcione desde el primer momento. Marcas como Adidas, Nike, Puma o New Balance se usan **únicamente como ejemplo técnico**: DT Sport **no** vende realmente esas marcas hasta que tú reemplaces la información. Las imágenes son ilustraciones SVG genéricas, no fotografías reales.

---

## 1. ¿Qué contiene el proyecto?

```
DT-Sport-Catalogo/
├── index.html          → Toda la página (HTML + CSS + JavaScript)
├── README.md            → Esta guía
└── assets/
    └── products/
        ├── producto-1.svg
        ├── producto-2.svg
        ├── ... hasta producto-8.svg
```

Todo el sitio vive en **un solo archivo** (`index.html`), lo que lo hace muy fácil de editar: no hay que buscar en varios archivos para cambiar algo.

---

## 2. Cómo cambiar el número de WhatsApp

1. Abre `index.html`.
2. Busca esta línea (cerca del inicio del `<script>`):
   ```js
   const WHATSAPP = "573107896804";
   ```
3. Reemplázala por tu número, **respetando el formato colombiano**.
4. Guarda el archivo. Todos los botones de WhatsApp (flotante, contacto, footer, consulta rápida, carrito) se actualizarán automáticamente porque todos usan esta única variable.

### Formato correcto del número (Colombia)

Se usa: `57` + número de celular, sin símbolos.

- ✅ Correcto: `573107896804`
- ❌ Incorrecto: `+57 3107896804`
- ❌ Incorrecto: `310-789-6804`
- ❌ Incorrecto: `(310) 789 6804`

---

## 3. Cómo cambiar un producto existente

1. Abre `index.html`.
2. Busca el bloque `const PRODUCTS = [ ... ]`.
3. Encuentra el producto por su `name` o `id`.
4. Edita el valor que necesites, por ejemplo:
   ```js
   name: "Campus Street",
   ```
5. Guarda el archivo.

---

## 4. Cómo agregar un producto nuevo

Dentro de `const PRODUCTS = [ ... ]`, copia un producto existente (con su coma final) y pégalo antes del `];`. Cambia sus datos:

```js
{
    id: 9,
    brand: "Marca",
    name: "Nuevo modelo",
    category: "Tenis",
    price: 250000,
    sizes: ["38","39","40"],
    tag: "NUEVO",
    image: "assets/products/producto-9.svg",
    description: "Descripción del producto.",
    available: true,
    featured: false
}
```

- El `id` debe ser un número que no se repita.
- Guarda una imagen nueva en `assets/products/` con el nombre que pusiste en `image`.
- El producto aparecerá automáticamente en el catálogo, sin tocar el HTML.

---

## 5. Cómo eliminar un producto

1. Ubica el bloque `{ ... }` completo del producto dentro de `PRODUCTS`.
2. Bórralo completo, incluyendo la coma que lo separa del siguiente producto.
3. Guarda el archivo.

---

## 6. Cómo cambiar el precio

Dentro del producto, cambia:

```js
price: 170000,
```

Escribe el número **sin puntos ni signo de pesos** (el sitio los agrega automáticamente en pantalla).

---

## 7. Cómo cambiar las tallas disponibles

Edita la lista `sizes`:

```js
sizes: ["38","39","40","41","42"],
```

Agrega, quita o cambia los números que necesites (siempre entre comillas).

---

## 8. Cómo cambiar una fotografía

1. Sube tu nueva imagen (recomendado: `.jpg`, `.png` o `.webp`) a la carpeta `assets/products/`.
2. En el producto correspondiente, cambia la ruta:
   ```js
   image: "assets/products/mi-foto-nueva.jpg",
   ```
3. Guarda. La imagen SVG de demostración se reemplazará por tu fotografía real.

> Consejo: usa nombres de archivo sin espacios ni tildes (ej. `campus-street.jpg`).

---

## 9. Cómo marcar un producto como oferta

Cambia el campo `tag` del producto a:

```js
tag: "OFERTA",
```

Las etiquetas disponibles son: `"NUEVO"`, `"OFERTA"`, `"DESTACADO"`, `"TOP"` o `""` (vacío, para no mostrar ninguna etiqueta).

---

## 10. Cómo marcar un producto como agotado

Cambia:

```js
available: false,
```

Cuando un producto está agotado:
- Se muestra la etiqueta **AGOTADO**.
- El botón "Agregar al carrito" se desactiva.
- El cliente aún puede **consultar por WhatsApp**.

Para volver a activarlo, cambia el valor a `available: true,`.

---

## 11. Cómo publicar en GitHub Pages (guía completa desde iPhone)

Esta guía asume que usarás el usuario de GitHub **`dtsportcolombia`** y el repositorio **`dtsport`**, todo desde el navegador Safari o Chrome del iPhone (sin apps ni comandos de Git).

### Paso 1 — Crear o iniciar sesión en GitHub
Abre [github.com](https://github.com) en el navegador de tu iPhone e inicia sesión con tu cuenta `dtsportcolombia` (o créala si no existe, tocando "Sign up").

### Paso 2 — Crear el repositorio
1. Toca el ícono `+` en la esquina superior y elige **New repository**.
2. En **Repository name** escribe: `dtsport`.
3. Selecciona **Public**.
4. No marques ninguna otra opción adicional.
5. Toca **Create repository**.

### Paso 3 — Subir los archivos
1. Dentro del repositorio recién creado, toca **Add file → Upload files**.
2. Selecciona desde tu iPhone: `index.html`, `README.md`, y la carpeta `assets` (si tu navegador no permite subir carpetas completas, sube primero los archivos y luego crea la carpeta `assets/products/` arrastrando cada `.svg` — ver nota abajo).
3. Escribe un mensaje de commit, por ejemplo: `Primera versión del catálogo`.
4. Toca **Commit changes**.

> **Nota sobre carpetas en iPhone:** algunos navegadores móviles no permiten subir carpetas completas de una vez. Si eso ocurre, sube los archivos `.svg` uno por uno usando "Upload files" y escribiendo la ruta `assets/products/nombre-archivo.svg` en el nombre al confirmarlo, o usa la app oficial de GitHub para iPhone, que sí permite crear carpetas fácilmente.

### Paso 4 — Verificar la estructura
Al terminar, tu repositorio debe verse así:

```
dtsport/
├── index.html
├── README.md
└── assets/
    └── products/
        ├── producto-1.svg
        ├── producto-2.svg
        └── ... (hasta producto-8.svg)
```

### Paso 5 — Hacer commit
Cada vez que subas o edites un archivo, GitHub te pedirá confirmar con **Commit changes**. Esto guarda los cambios en el repositorio.

### Paso 6 — Activar GitHub Pages
1. Ve a la pestaña **Settings** del repositorio.
2. En el menú lateral, toca **Pages**.
3. En **Source**, selecciona **Deploy from a branch**.
4. En **Branch**, selecciona **main** y la carpeta **/ (root)**.
5. Toca **Save**.

### Paso 7 — Ver tu sitio publicado
Después de unos minutos, tu catálogo estará disponible en:

```
https://dtsportcolombia.github.io/dtsport/
```

---

## 12. Cómo actualizar la página más adelante (desde iPhone)

1. Entra a tu repositorio `dtsport` en GitHub desde el navegador.
2. Abre el archivo que quieres editar (por ejemplo `index.html`).
3. Toca el ícono de lápiz (✏️) para editar directamente en el navegador.
4. Realiza tus cambios (precio, producto, WhatsApp, etc.).
5. Baja hasta el final y toca **Commit changes**.
6. Espera 1-2 minutos: GitHub Pages actualizará automáticamente tu sitio publicado.

Para subir nuevas fotografías, usa **Add file → Upload files** dentro de la carpeta `assets/products/`.

---

## 13. Dominio personalizado (opcional, para más adelante)

Cuando quieras, puedes conectar un dominio propio como `dtsport.co` o `dtsport.com.co` a tu sitio de GitHub Pages, sin reconstruir el proyecto. Esto se hace desde **Settings → Pages → Custom domain**, apuntando los registros DNS de tu dominio hacia GitHub. No es necesario configurarlo ahora; el sitio funciona perfectamente con la URL gratuita de GitHub Pages mientras tanto.

---

## 14. Resumen rápido de personalización

| Quiero cambiar...        | Dónde lo hago                                   |
|---------------------------|--------------------------------------------------|
| Número de WhatsApp         | Variable `WHATSAPP` al inicio del `<script>`     |
| Instagram / Horario        | Objeto `CONFIG`                                  |
| Productos, precios, tallas | Lista `PRODUCTS`                                 |
| Fotografías                | Carpeta `assets/products/` + campo `image`       |
| Textos generales           | Directamente en el HTML de cada sección          |

---

Hecho con HTML, CSS y JavaScript puro. Sin frameworks, sin servidores, listo para GitHub Pages. 🖤
