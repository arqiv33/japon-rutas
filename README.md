# Rutas JR y Shinkansen · Japón

Visualizador web de rutas de tren por Japón. Selecciona estaciones (en la lista o en el mapa),
se muestran las distancias aproximadas entre paradas, el total acumulado y el trazado de la ruta
sobre un mapa real de Japón (Leaflet + OpenStreetMap).

## Características

- Mapa real de Japón con OpenStreetMap.
- Selección de paradas en orden; puedes repetir estaciones (por ejemplo, volver a Tokio).
- Distancia aproximada por tramo, con las vías intermedias cuando no hay conexión directa.
- Distancia total acumulada.
- Botón **Cargar itinerario** con el recorrido de la imagen de itinerario general.
- La ruta se guarda en el navegador (localStorage), así no se pierde al recargar.

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub, por ejemplo `japon-rutas`.
2. Sube `index.html` y `README.md` a la rama `main`.
3. Ve a **Settings → Pages**.
4. En **Build and deployment**, elige **Deploy from a branch**, rama `main` y carpeta `/ (root)`.
5. Guarda. En uno o dos minutos la página estará en:
   `https://TU-USUARIO.github.io/japon-rutas/`

Tambien puedes probarla localmente abriendo `index.html` en el navegador.

## Editar estaciones y distancias

Todo está en el bloque `<script>` de `index.html`:

- `STATIONS`: nombre, nombre en japonés, coordenadas y operador de cada estación.
- `EDGES`: tramos directos entre estaciones como `[origen, destino, km, modo, servicio]`.
  Modos válidos: `shinkansen`, `jr`, `bus`, `otro`.
- `PRESET`: secuencia de paradas del botón **Cargar itinerario**.

Para agregar una estación, añade una entrada a `STATIONS` con un `id` único y después
agrega sus tramos a `EDGES`.

## Notas

- Las distancias son aproximaciones por vía ferroviaria y pueden variar un poco de las oficiales.
- El trazado en el mapa sigue un recorrido aproximado de cada línea mediante puntos intermedios
  (campo 6 de `EDGES`). No es el trazado GPS oficial.
- Algunos tramos no son JR: Keikyu/Monorail (aeropuerto Haneda), Odakyu (Hakone), autobús
  (Shirakawa-go) y el ferry a Miyajima. Se marcan con colores distintos en el mapa.
- Verifica horarios y tramos (por ejemplo, Kanazawa → Osaka se modela vía Tsuruga y Kioto con el
  Thunderbird) antes de viajar.
