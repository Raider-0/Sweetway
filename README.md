# Sweetway — Menú & Pedidos 🍓

Página de menú interactiva (sin servidor). Los pedidos llegan por WhatsApp ya armados;
el pago se acuerda al confirmar. Hosting **gratis** con HTTPS.

---

## 📁 Estructura del proyecto

```
sweetway-site/
├── index.html      <- la página (NO necesitas tocarla para cambiar el menú)
├── menu.json       <- AQUÍ editas sabores, precios y datos  (estrella)
├── assets/
│   └── logo.png    <- tu logo (lo agregas tú)
├── README.md       <- este archivo
└── .gitignore
```

La idea: **el código vive en `index.html`, los datos en `menu.json`.**
Ama puede cambiar el menú editando solo `menu.json`, sin riesgo de romper el código.

---

## ✏️ Cómo cambiar el menú (editar `menu.json`)

Abre `menu.json` con cualquier editor. Verás bloques claros:

- **config** -> WhatsApp, Instagram, logo, moneda. (`cashapp` y `zelle` se dejan vacíos
  por seguridad; Ama los manda por WhatsApp al confirmar.)
- **signature** -> tus vasitos: `nombre`, `desc`, `precio`.
- **extras** -> toppings y tamaños.
- **personalizado** -> "arma tu vasito": precio, mínimo, bases y toppings.
- **reglas** -> texto de Eventos/Mayoreo (español `es` e inglés `en`).

ATENCIÓN: es JSON. Respeta las **comillas** " y las **comas** entre elementos (sin coma
después del último). Si algo falla, la página te avisará qué revisar.

### WhatsApp
En `config.whatsapp` pon el número con código de país, **sin** + ni espacios.
Ejemplo McAllen: `19561234567`.

### Logo
1. Copia tu imagen a `assets/` y nómbrala `logo.png`.
2. En `menu.json` pon: `"logo": "assets/logo.png"`.
Mientras esté vacío, se muestra una ilustración de respaldo.

---

## 🚀 Subir a GitHub Pages (gratis, con HTTPS)

### Opción A — GitHub Desktop (sin terminal, recomendado)
1. Crea cuenta en https://github.com y descarga **GitHub Desktop**.
2. File -> New repository -> nombre `sweetway` -> Create.
3. Copia TODO el contenido de esta carpeta dentro del repo.
4. Commit to main -> Publish repository (déjalo **público**).
5. En github.com: tu repo -> Settings -> Pages -> Branch: main -> Save.
6. En 1-2 min queda en: https://TU-USUARIO.github.io/sweetway/

### Opción B — Git en terminal
```bash
git init
git add .
git commit -m "primer deploy de Sweetway"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/sweetway.git
git push -u origin main
```
Luego: Settings -> Pages -> Branch: main -> Save.

### Actualizar precios/sabores después
Edita `menu.json`, guarda, y:
```bash
git add .
git commit -m "nuevos precios"
git push
```
Se publica solo en segundos. Queda historial para deshacer.

---

## 👀 Probar en tu compu (importante)

Como el menú se carga desde `menu.json`, **abrir `index.html` con doble clic NO funciona**
(el navegador bloquea la carga con file://). Dos formas de verlo:

- Lo más simple: súbelo a GitHub Pages y míralo desde su URL.
- O levanta un servidor local rápido en la carpeta:
  ```bash
  python3 -m http.server 8000
  ```
  y abre http://localhost:8000

---

## 🔳 El QR
Genera un QR **estático** (gratis, no caduca) apuntando a tu URL de GitHub Pages.
Este QR solo **arma el pedido**, no cobra. El cobro de Cash App usa **otro** QR distinto
que genera la app de Cash App.

## 🔒 Seguridad — en corto
- Repo público = el código se ve. No metas Cash App/Zelle ni datos personales (quedan en
  el historial de Git aunque los borres). Ama los manda por WhatsApp al confirmar.
- Verifica que el pago **llegó a la cuenta** antes de entregar (los screenshots se falsifican).
- Entrega siempre en punto neutro, nunca en casa.
- HTTPS viene incluido en GitHub Pages.

## 💵 Costo
Todo **$0**. Opcional: dominio propio (~$10-12/año).
