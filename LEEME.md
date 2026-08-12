# Tarjeta de lealtad digital — Kupuri The Rooftop

Mismo sistema que Püri Café y Kupuri Cocina de Mar: GitHub + Netlify + Firebase Firestore (gratis).

## Archivos que debes subir a GitHub

Sube **toda la carpeta**, no solo los HTML:
- `index.html` (link para clientes)
- `staff.html` (link para el rooftop, con PIN)
- `LEEME.md` (opcional, referencia tuya)
- carpeta `assets/` completa (logo y fotos)

## Paso 1 — Crear el proyecto en Firebase

1. https://console.firebase.google.com → "Agregar proyecto" → nómbralo `kupuri-rooftop-lealtad` (o el que prefieras).
2. Compilación → **Firestore Database** (no Realtime Database) → "Crear base de datos" → **Standard** → **modo de producción** → región más cercana.
3. Pestaña "Reglas" → pega esto → "Publicar":

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /clientes/{clienteId} {
      allow read, write: if true;
    }
  }
}
```

4. Ícono de engrane ⚙️ → Configuración del proyecto → "Tus apps" → ícono `</>` (Web) → regístrala → copia los 6 valores del `firebaseConfig`.

## Paso 2 — Pegar la configuración

Pega esos 6 valores **en los dos archivos**: `index.html` Y `staff.html` (busca "TU_API_KEY" en cada uno).

## Paso 3 — GitHub y Netlify

Mismo proceso de siempre: crea el repositorio, sube el contenido completo de la carpeta, conéctalo a Netlify, dale deploy.

## Links una vez desplegado

- **Clientes:** `tu-sitio.netlify.app`
- **Staff (con PIN):** `tu-sitio.netlify.app/staff.html`
- **PIN por default:** `2026` — cámbialo en `staff.html`, busca `const PIN_STAFF = "2026";`

## Programa de lealtad

- Sello 3 de 10 → 20% de descuento en el total de la cuenta
- Sello 5 de 10 → 30% de descuento en el total de la cuenta
- Sello 10 de 10 → 50% de descuento en el total de la cuenta (reinicia la tarjeta)

## Funciones incluidas

- Botón de WhatsApp para el staff con mensaje automático de progreso.
- Datos extra opcionales del cliente (correo, Instagram, colonia, cumpleaños, cómo conoció el lugar, ocupación).
- Dashboard en `staff.html` → "Todos los clientes": lista completa con filtro y estadísticas.
