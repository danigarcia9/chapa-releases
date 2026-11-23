# Chapa para Tinycast (y Raycast)

Un comando, **Historial de dictados**: lo que has dictado con Chapa, agrupado por día, con búsqueda (sin
distinguir mayúsculas ni tildes) y filtro por app.

| Tecla | Acción |
|---|---|
| **↵** | Copiar |
| **⌘ ↵** | Pegar en la app de delante |
| **⌘ ⇧ E** | Copiar con tus correcciones (si lo retocaste después de pegarlo) |
| **⌘ ⇧ C** | Copiar sin pulir (lo que oyó el modelo de voz) |
| **⌘ R** | Recargar |

Lee `~/Library/Application Support/Chapa/chapa.sqlite` en solo lectura con `/usr/bin/sqlite3`, que viene con
macOS. No manda nada a ningún sitio y no hace falta tocar Chapa. Solo salen los dictados terminados: los
pendientes, fallidos y cancelados se resuelven desde el Historial de Chapa.

## Instalar

En Tinycast, activa antes las extensiones en *Ajustes ▸ Extensions*.

- **Desde GitHub (lo normal):** *Ajustes ▸ Extensions ▸ Install* y pega
  `https://github.com/danigarcia9/chapa-releases/tree/main/tinycast`. Tinycast la instala y la compila solo. Esa
  copia pública la pone al día `scripts/publish-tinycast.sh` en cada versión de Chapa (el repo de código es privado).
- **Desde esta carpeta:** `npm install && npm run build` y luego *Ajustes ▸ Extensions ▸ Add from folder*.
- **En Raycast:** `npm install && npm run dev`.

Tinycast no actualiza solas las extensiones de GitHub o de una carpeta: para una versión nueva, vuelve a instalarla.

## Desarrollo

`npm run typecheck` y `npm run build`. El esquema de la tabla `dictations` está en
`Sources/ChapaCore/Datos/History.swift`; si cambia, revisa la consulta de `src/historial.tsx`.
