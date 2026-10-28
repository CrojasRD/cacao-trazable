# Cacao Trazable · Maicao — Trazabilidad con QR

Bitácora del proyecto. Autor: Carlos Alberto Rojas Domínguez.

## Dirección publicada
https://crojasrd.github.io/cacao-trazable/ (GitHub Pages, repo CrojasRD/cacao-trazable).

## Qué es
App web de un solo archivo (`index.html`) para seguir un lote de cacao desde la finca
hasta el país de destino. Cada etapa se guarda como un "bloque" encadenado al anterior
con una huella SHA-256, igual que en una blockchain. Cada lote genera un código QR.

## Etapas registradas
Cultivo → Cosecha → Fermentación → Secado → Acopio y venta → Transformación →
Exportación → Llegada a destino. Cada una guarda fecha, responsable, documento/NIT,
lugar y datos técnicos propios (kg, humedad, precio, puerto, destino, contenedor…).

## Cómo usarla
1. Abrir `index.html` en Chrome o Edge.
2. "Cargar lote de ejemplo" para ver un lote completo (Dibulla → Maicao → Santa Marta → Hamburgo).
3. "Registrar etapa" para agregar etapas a lotes propios.
4. "Trazabilidad y QR": ver la línea de tiempo, la verificación y descargar o imprimir el QR.
5. "Simular manipulación" muestra cómo la cadena detecta un dato alterado (para la exposición).

## Para que el QR funcione en un celular
El QR contiene el lote completo comprimido más las huellas, y abre esta misma página.
Hay que publicar `index.html` en internet (por ejemplo GitHub Pages o Netlify, gratis)
y escribir esa dirección en el campo "Dirección pública" antes de generar el QR.

## Decisiones
- 2026-10-27 — Sin servidor ni base de datos: los datos viven en el navegador
  (localStorage) y viajan dentro del QR. Suficiente para la demostración académica.
- 2026-10-27 — El QR lleva los datos, los primeros 8 caracteres de cada huella y la
  huella final completa; al abrirlo se recalcula toda la cadena y se compara.
- 2026-10-27 — Alcance: es una cadena de hashes, no una blockchain distribuida. En
  producción se anclarían las huellas en una red pública (Polygon/Ethereum) o
  permisionada (Hyperledger Fabric).
- 2026-10-27 — Publicada en GitHub Pages; el lote de ejemplo se carga solo si el
  navegador no tiene lotes guardados, para que la página nunca se vea vacía.
- Los nombres del lote de ejemplo son ficticios.
