# 📋 Escáner de Asistencia por Carnet

Aplicación web para registrar la asistencia del personal de una empresa
fotografiando su carnet. La aplicación lee el carnet con OCR, **extrae
únicamente el nombre de la persona** (ignora número de documento, fechas y
cualquier otro dato) y la registra como **presente** con fecha y hora.

## ¿Cómo funciona?

1. Abre `index.html` en el navegador (celular o computadora).
2. Permite el acceso a la cámara y coloca el carnet dentro del recuadro guía.
3. Pulsa **📸 Tomar foto** (o **🖼️ Subir imagen** si prefieres usar una foto ya tomada).
4. El OCR (Tesseract.js en español) detecta el nombre; puedes corregirlo antes de confirmar.
5. Pulsa **✅ Registrar presente**: la persona queda en la lista del día con su hora de entrada.

## Funciones

- **Solo el nombre**: filtros que descartan números, fechas, etiquetas del documento y demás datos del carnet.
- **Sin duplicados**: si la misma persona ya fue registrada hoy, la app lo avisa y no la vuelve a registrar.
- **Lista del día**: contador de presentes, hora de cada registro y opción de eliminar entradas erróneas.
- **Exportar CSV**: descarga la asistencia del día (`asistencia_AAAA-MM-DD.csv`) para abrirla en Excel.
- **Datos locales**: los registros se guardan en el propio dispositivo (localStorage); no se envían a ningún servidor.

## Requisitos

- Navegador moderno (Chrome, Edge, Safari, Firefox).
- Conexión a internet la primera vez, para descargar la librería de OCR (Tesseract.js) desde el CDN.
- Para usar la cámara, la página debe servirse por **HTTPS** o abrirse en `localhost`
  (requisito de los navegadores). Por ejemplo:

  ```bash
  # opción rápida con Python
  python3 -m http.server 8080
  # luego abrir http://localhost:8080
  ```

  También puede publicarse gratis en GitHub Pages, Netlify o similar.

## Estructura

- `index.html` — toda la aplicación (HTML + CSS + JavaScript) en un solo archivo.

## Consejos para un buen escaneo

- Buena iluminación, sin reflejos sobre el plástico del carnet.
- Llenar el recuadro guía con el carnet, en horizontal.
- Si el nombre sale con errores, se puede corregir en el campo de texto antes de registrar.
