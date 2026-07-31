# 📋 Escáner de Asistencia por Carnet

Aplicación web para registrar la asistencia del personal de una empresa
fotografiando su carnet. La aplicación lee el carnet con OCR y extrae **el
nombre y el cargo de la persona** (ignora número de documento, fechas y
cualquier otro dato), registrándola como **presente** con fecha y hora.

## Formato de carnet esperado

Los carnets de la empresa siguen esta distribución vertical, sin etiquetas:

```
[ foto de la persona ]
NOMBRE APELLIDO        <- debajo de la foto
CARGO                  <- justo debajo del nombre
```

La detección usa la posición de cada línea de texto en la imagen: busca la
línea que parece un nombre (solo letras, 2 a 6 palabras, sin palabras del
documento ni de la empresa) y toma la línea inmediatamente inferior como
cargo. Un diccionario de cargos frecuentes (gerente, auxiliar, operario,
técnico, etc.) refuerza la elección.

## ¿Cómo funciona?

1. Abre `index.html` en el navegador (celular o computadora).
2. Permite el acceso a la cámara y coloca el carnet dentro del recuadro guía.
3. Pulsa **📸 Tomar foto** (o **🖼️ Subir imagen** si prefieres usar una foto ya tomada).
4. El OCR (Tesseract.js en español) detecta el nombre y el cargo; puedes corregirlos antes de confirmar.
5. Pulsa **✅ Registrar presente**: la persona queda en la lista del día con su cargo y hora de entrada.

## Funciones

- **Nombre y cargo**: filtros que descartan números, fechas, encabezados de la empresa y demás datos del carnet.
- **Recorte automático**: al tomar la foto solo se procesa la zona del recuadro guía, lo que mejora mucho la precisión del OCR.
- **Preprocesado de imagen**: escala de grises y ajuste de contraste antes de leer el texto.
- **Sin duplicados**: si la misma persona ya fue registrada hoy, la app lo avisa y no la vuelve a registrar.
- **Lista del día**: contador de presentes, hora de cada registro y opción de eliminar entradas erróneas.
- **Exportar CSV**: descarga la asistencia del día (`asistencia_AAAA-MM-DD.csv`) con columnas Nombre, Cargo, Fecha y Hora, lista para Excel.
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
