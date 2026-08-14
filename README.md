# Sitio de talleres

Los materiales del taller servidos como web, para poder darle un link a los participantes en vez de mandarles un archivo.

Mismo patrón que `08-productos-internos/invitaciones/`: nginx sirviendo archivos estáticos, sin build ni backend.

---

## Qué se publica

| Archivo | URL final | Para quién |
|---|---|---|
| `index.html` | `taller.ambarrojostudios.cloud` | **Participantes** — el cuaderno de trabajo |
| `recursos.html` | `.../recursos.html` | Participantes — hoja de recursos |
| `presentacion.html` | `.../presentacion.html` | Facilitador — los slides |

El link corto (el dominio pelón) va al cuaderno **a propósito**: es el que se dicta en voz alta y se escribe en el proyector. Entre menos tenga que teclear alguien desde su celular, mejor.

---

## Desplegar en EasyPanel

1. **Subir esta carpeta a un repo de GitHub** (ej. `Ambar-Rojo-Studios/talleres-web`).
2. En EasyPanel → proyecto → **Create Service → Compose**.
3. Apuntarlo al repo, rama `main`.
4. **Domains** → agregar `taller.ambarrojostudios.cloud` → puerto **80**.
5. En Cloudflare, apuntar el subdominio `taller` al VPS.
6. **Deploy**.

> ⚠️ Igual que con el front de 300 Lugares: **el deploy no es automático**. Después de cada push hay que entrar a EasyPanel y darle Deploy. Ver [`../../01-procesos/despliegue.md`](../../01-procesos/despliegue.md).

---

## Antes del próximo taller

- [ ] **Conectar la encuesta.** En `index.html`, la constante `ENCUESTA` está vacía, así que la tarjeta de evaluación no se muestra. Pasar `Materiales/4 - Instrumento de evaluacion.pdf` a Google Forms y pegar la URL ahí.
- [ ] **Confirmar el WhatsApp.** La constante `WHATSAPP` apunta a `529612255126` (Raúl). Ahí llegan las hojas de ruta de los participantes — que son leads calificados, vale la pena que llegue a quien dé seguimiento.

---

## Para el siguiente taller

Cuando haya otro (universidad, otro gremio), meter sus materiales en una subcarpeta:

```
_web/
├── index.html          ← el taller activo
├── coparmex/           ← el anterior, archivado
│   └── index.html
└── universidad/
    └── index.html
```

Así `taller.ambarrojostudios.cloud/universidad/` funciona solo, sin tocar nada más.

> **Ojo con el `localStorage`:** el cuaderno guarda con la llave `taller-ia-coparmex-v1`. Si se reusa el archivo para otro taller, cambiar esa llave — si no, alguien que haya estado en los dos ve las respuestas del anterior.

---

## De dónde salen estos archivos

Son copias de `../Taller Coparmex/Materiales/`. Esa carpeta conserva los originales para abrirlos localmente sin servidor; **esta carpeta es la que se publica**. Si editas el cuaderno para producción, edítalo aquí.

**Creado:** 2026-08-14
