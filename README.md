# Inventario GENIALab

<img src="logo.png" alt="Logo GENIALab" width="96" align="right">

Aplicación web de GENIALab para llevar el control de un inventario de forma sencilla, rápida y sin necesidad de servidor: todo funciona en el navegador y los datos se guardan en el propio dispositivo.

## Funciones

- **Artículos**: registra cada artículo con cantidad, unidad, mínimo, precio unitario, categoría, lugar y notas.
  - Suma o resta unidades con un toque.
  - Alerta visual de **bajo mínimo** cuando la cantidad llega al mínimo definido.
  - Búsqueda por nombre, categoría o lugar, filtro por categoría y varios órdenes.
  - Estadísticas en vivo: total de artículos, unidades, valor del inventario y pendientes.
- **Movimientos**: registra ventas (salidas) o compras (entradas) de varios artículos a la vez — por ejemplo, 10 lapiceros y 5 cuadernos — y las cantidades se actualizan de un solo golpe, con validación de stock y opción de deshacer.
- **Historial**: cada movimiento queda anotado con fecha y hora en su propia pestaña.
- **Marcas**:
  - Automáticas: sello **Top ventas** para los 3 artículos más vendidos y **Poca rotación** para los que llevan más de dos semanas sin venderse; contador de vendidos por artículo y orden "Más vendidos".
  - Manuales: estrella de **destacado** (con filtro "Solo destacados") y etiquetas rápidas como **Promoción**, **Vence pronto**, **Pedido** o **Dañado**.
- **Notas**: espacio libre para proveedores, medidas o recordatorios; se guardan solas mientras escribes.
- **Checklist**: lista de tareas con barra de progreso. Puedes traer automáticamente los artículos bajo mínimo como tareas de reposición.
- **Copia de seguridad**: exporta e importa todos los datos en un archivo `.json` desde el botón **Datos**.
- **Deshacer**: al borrar un artículo, nota o tarea tienes unos segundos para recuperarlo.

## Cómo usarla

No requiere instalación ni dependencias. Abre `index.html` en cualquier navegador moderno (computador o celular) y empieza a registrar artículos con el botón **+**.

> Los datos se guardan solo en el navegador del dispositivo (localStorage). Si vas a cambiar de navegador o de equipo, descarga una copia desde **Datos → Descargar copia (.json)** y cárgala en el otro dispositivo.

## Tecnología

- HTML, CSS y JavaScript puros en un solo archivo (`index.html`), sin frameworks ni build.
- Diseño responsivo (móvil primero) con estilo neobrutalista en amarillo y azul.
- Accesible: etiquetas ARIA, foco visible y soporte de `prefers-reduced-motion`.
