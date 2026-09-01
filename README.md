# Sitio de talleres

Los materiales del taller servidos como web, para poder darle un link a los participantes en vez de mandarles un archivo.

Mismo patrón que `08-productos-internos/invitaciones/`: nginx sirviendo archivos estáticos, sin build ni backend.

---

## Taller activo — 2026-08-31 · Coparmex (PyMEs)

El anterior (Legítimo, despacho de abogados) quedó archivado en `/legitimo/`.
Para reactivarlo: mover `index.html`/`presentacion.html`/`recursos.html`/el video de la raíz a
una subcarpeta nueva (archivo del taller que sale) y mover los de `/legitimo/` de vuelta a la
raíz. Un commit, sin tags ni reverts.

## Qué se publica

| Archivo | URL final | Para quién |
|---|---|---|
| `index.html` | `taller.ambarrojostudios.cloud` | **Participantes** — el cuaderno de trabajo |
| `recursos.html` | `.../recursos.html` | Participantes — hoja de recursos |
| `presentacion.html` | `.../presentacion.html` | Facilitador — los slides |
| `7 - Video peligros de la IA.mp4` | `.../7 - Video peligros de la IA.mp4` | Video del bloque 1, referenciado por `presentacion.html` |
| `legitimo/*` | `.../legitimo/*` | El taller anterior, archivado tal cual (incluye su propio video) |

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

- [x] ~~Conectar la encuesta~~ — ya no aplica. La evaluación vive **dentro** del cuaderno
      (pestaña 9) desde la versión Coparmex, no hay Google Forms ni constante `ENCUESTA`.
- [ ] **Confirmar el WhatsApp.** La constante `WHATSAPP` apunta a `529612255126` (Raúl). Ahí
      llegan las hojas de ruta de los participantes — que son leads calificados.

---

## Para el siguiente taller

Cuando haya otro, meter sus materiales en una subcarpeta y archivar el que sale de la raíz:

```
_web/
├── index.html          ← el taller activo
└── legitimo/             ← despacho de abogados, ago-2026, archivado
    └── index.html
```

Así `taller.ambarrojostudios.cloud/legitimo/` (o el que sea) funciona solo, sin tocar nada más.

> **Ojo con el `localStorage`:** cada cuaderno guarda con su propia llave —
> `taller-ia-coparmex-v1`, `taller-ia-legitimo-v1`. Si se reusa un archivo para otro taller,
> **cambiar esa llave** — si no, alguien que haya estado en los dos ve las respuestas del anterior.

---

## De dónde salen estos archivos

Son copias de `../Taller Coparmex/Materiales/` (Coparmex, activo) y `../Legitimo/Materiales/`
(Legítimo, archivado). Esas carpetas conservan los originales para abrirlos localmente sin servidor;
**esta carpeta es la que se publica**. Si editas un cuaderno para producción, edítalo en su
carpeta de origen y vuelve a copiarlo aquí — no lo edites solo aquí, se te va a perder.

**Creado:** 2026-08-14 · **Legítimo publicado:** 2026-08-20 · **Coparmex reactivado:** 2026-08-31
