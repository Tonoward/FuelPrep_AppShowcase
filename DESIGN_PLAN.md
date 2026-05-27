# ⚡ Fuel — Plan de Diseño de Pantallas MVP

> **Nota:** Toda la interfaz de usuario se implementará en **español**.

---

## Sistema de Colores

| Token | Hex | Rol |
|---|---|---|
| Electric Green | `#14ff69` | CTA principal, estados activos, acentos, efectos glow |
| Sage Green | `#749a76` | Texto secundario, iconos inactivos, bordes, rellenos sutiles |
| Frost White | `#f1fcf1` | Fondos claros, relleno de tarjetas, texto en fondos oscuros |
| Deep Forest | `#131e13` | Fondo oscuro principal, tarjetas oscuras, texto en fondos claros |

**Tipografía:** Inter (Google Fonts) — Bold para títulos, Medium para etiquetas, Regular para cuerpo  
**Bordes redondeados:** 16px tarjetas, 999px pills/botones, 12px inputs  
**Formato:** HTML estático + Tailwind CSS (vía CDN) — un archivo por pantalla, sin herramientas de build  

**Estructura de archivos:**
```
screens/
  01_onboarding/   (5 archivos)
  02_main_app/     (2 archivos)
  03_schedule/     (2 archivos)
  04_admin/        (4 archivos)
  05_ticket/       (1 archivo)
  06_delivery/     (1 archivo)
```

---

## Estado de Fases

| Fase | Contenido | Archivos | Estado |
|---|---|---|---|
| **Fase 1** | Onboarding (5 pantallas) | `01_onboarding/` | ✅ Completado |
| **Fase 2** | App principal + Detalle de menú | `02_main_app/` | ✅ Completado |
| **Fase 3** | Pantallas de agenda | `03_schedule/` | ✅ Completado |
| **Fase 4** | Dashboard admin (4 pantallas) | `04_admin/` | ✅ Completado |
| **Fase 5** | Ticket / Etiqueta de comida | `05_ticket/` | ✅ Completado |
| **Fase 6** | Dashboard de repartidor | `06_delivery/` | ✅ Completado |

---

## Fase 1 — Onboarding Mobile (5 pantallas)

Todas las pantallas de onboarding comparten: fondo oscuro `#131e13`, logotipo `⚡ Fuel` centrado arriba, indicador de progreso de 5 puntos, y botón "Siguiente" de ancho completo en `#14ff69` anclado cerca de la parte inferior.

---

### Pantalla 1.1 — Ingreso de Nombre
**`01_onboarding/01_name.html`**

| Componente | Detalle |
|---|---|
| Fondo | `#131e13` completo |
| Logo | `⚡ Fuel` centrado arriba, rayo en Electric Green + wordmark en Frost White |
| Indicador de paso | 5 puntos, primer punto `#14ff69`, resto `#749a76` al 30% de opacidad |
| Título | `"Hola, ¿cómo te llamas?"` — blanco, ~32px, bold, centrado |
| Subtexto | `"Usaremos esto para personalizar tu experiencia"` — `#749a76`, pequeño, centrado |
| Campo de entrada | Ancho completo, rounded-full, superficie oscura + borde 1px `#749a76`, placeholder `"Tu nombre"` en sage, texto blanco, focus ring `#14ff69` |
| Botón siguiente | Ancho completo, rounded-full, fondo `#14ff69`, texto `#131e13`, bold |
| Espaciado | Espacio vertical generoso, contenido centrado verticalmente |

---

### Pantalla 1.2 — Información Física Básica
**`01_onboarding/02_fitness_info.html`**

| Componente | Detalle |
|---|---|
| Título | `"Cuéntanos sobre ti"` |
| Subtexto | `"Esto nos ayuda a calcular tu plan nutricional ideal"` |
| Campo Edad | Input numérico con unidad `años` |
| Selector Sexo | Grupo de pills horizontal: `Masculino` / `Femenino` / `Otro` — seleccionado rellena `#14ff69` con texto oscuro |
| Campo Peso | Input numérico + toggle de unidad (`kg` / `lbs`) en fila |
| Campo Altura | Input numérico + toggle de unidad (`cm` / `ft·in`); si `ft·in`, se divide en dos inputs |
| Divisores de sección | Líneas delgadas `#749a76` al 20% entre campos |
| Indicador de paso | Punto 2 activo |

---

### Pantalla 1.3 — Objetivos (Prompt IA)
**`01_onboarding/03_goals.html`**

| Componente | Detalle |
|---|---|
| Fila superior | Título izquierda + enlace ghost `"Omitir →"` derecha (color sage) |
| Badge opcional | Pill pequeño `OPCIONAL` en sage |
| Título | `"Cuéntanos sobre tus objetivos"` |
| Subtexto | `"Nuestra IA traducirá tus palabras en un plan de macros personalizado"` |
| Área de texto | Grande, rounded rect, relleno oscuro, mínimo 5 filas; placeholder en cursiva sage con ejemplo: `"Quiero estar más definido y ganar algo de músculo, no hago mucho ejercicio a la semana, pero quiero mantenerme en 3 días de entrenamiento de fuerza"` |
| Contador | Abajo derecha del textarea: `"0 / 500"` en sage |
| Nota IA | Fila con ícono de destellos + `"La IA analizará esto para completar tu plan"` |
| Botón principal | `#14ff69` — `"Analizar y Continuar"` |
| Botón secundario | Ghost debajo: `"Omitir — completar manualmente"` en sage |
| Indicador de paso | Punto 3 activo |

---

### Pantalla 1.4 — Configuración Avanzada
**`01_onboarding/04_advanced_input.html`**

| Componente | Detalle |
|---|---|
| Título | `"Ajusta tu plan"` |
| Badge IA | Pill verde pequeño `⚡ Completado por IA` junto a campos llenados automáticamente |
| Calorías diarias | Input numérico grande con etiqueta `kcal` alineada a la derecha dentro del campo |
| Fila de macros | Tres inputs lado a lado: `Proteína g`, `Carbohidratos g`, `Grasa g`; debajo de cada uno, badge pequeño de porcentaje calculado automáticamente |
| Barra visual de macros | Barra horizontal dividida mostrando proporción de macros en tres colores (verde, ámbar, naranja) |
| Nivel de actividad | Control segmentado horizontal: `Sedentario` / `Ligero` / `Moderado` / `Activo` / `Muy activo` — con scroll en pantallas pequeñas |
| Objetivo fitness | Grid de pills (2×2): `Perder peso` / `Mantener` / `Ganar músculo` / `Rendimiento` |
| Botón | `"Guardar Plan"` — primario |
| Indicador de paso | Punto 4 activo |

---

### Pantalla 1.5 — Alergias y Solicitudes Especiales
**`01_onboarding/05_allergies.html`**

| Componente | Detalle |
|---|---|
| Título | `"¿Tienes alergias alimentarias?"` |
| Grid de alérgenos | 2 columnas de pills con ícono + etiqueta: Gluten, Lácteos, Frutos secos, Huevos, Mariscos, Soya, Pescado, Sésamo — no seleccionado = contorno sage, seleccionado = relleno `#14ff69` + texto oscuro + ícono de check |
| Agregar custom | Fila botón `"+ Agregar alérgeno"`, al tocar abre input de texto en línea |
| Divisor | Línea horizontal |
| Solicitudes especiales | `"¿Alguna solicitud especial para la preparación?"` |
| Textarea solicitudes | Redondeado, oscuro, 3 filas, placeholder: `"Ej. Sin cebolla, extra picante, menos aceite..."` |
| Disclaimer | Texto sage muy pequeño: `"Nuestro equipo de cocina revisará esto en cada comida"` |
| Botón CTA | `"¡Vamos! ⚡"` — ancho completo, `#14ff69`, grande, bold |
| Indicador de paso | Punto 5 activo |

---

## Fase 2 — App Principal Mobile (2 pantallas)

Todas las pantallas de la app principal incluyen la **barra de navegación inferior**.

### Barra de Navegación Inferior (compartida)
5 tabs. Tab central de QR elevado:

| Tab | Ícono | Etiqueta | Estado activo |
|---|---|---|---|
| Inicio | Ícono casa | `Menú` | Ícono + label `#14ff69` |
| Agenda | Ícono calendario | `Agenda` | `#14ff69` |
| QR | Ícono QR | *(sin label)* | Pill flotante elevado 8px, fondo `#14ff69` con ícono oscuro; sombra glow verde si hay pedido activo |
| Perfil | Ícono persona | `Perfil` | `#14ff69` |
| Ajustes | Ícono engranaje | `Ajustes` | `#14ff69` |

Fondo barra: `#131e13`, borde superior 1px sage al 20%, alto ~64px + safe area.

---

### Pantalla 2.1 — Inicio / Menú
**`02_main_app/01_home_menu.html`**

| Componente | Detalle |
|---|---|
| Barra superior | Izquierda: wordmark `⚡ Fuel`. Derecha: avatar circular placeholder |
| Saludo | `"Buenos días, Alex 👋"` — peso medio, Frost White, alineado izquierda |
| Tabs de tipo de comida | Pills horizontales desplazables: `Desayuno` `Almuerzo` `Cena` — tab activo relleno `#14ff69`, otros contorno sage |
| Tarjeta de cuenta regresiva | Ancho completo, relleno oscuro `#1a2a1a`, izquierda: ícono reloj + `"Cierre de pedidos en"`, derecha: cuenta regresiva mono grande en `#14ff69`; abajo: barra de progreso delgada en Electric Green |
| Grid de menús | 2 columnas, tarjetas altas (~180px), rounded-2xl |
| Tarjeta de menú | Foto de ancho completo (placeholder), degradado en mitad inferior, nombre bold blanco, fila de barras de macros |
| Barras de macros | Tres barras mini horizontales (alto 4px). Etiquetas: `P` verde, `C` ámbar, `G` naranja. Gramos debajo (ej. `38g P · 52g C · 14g G`) en frost white pequeño |

---

### Pantalla 2.2 — Detalle de Menú
**`02_main_app/02_menu_detail.html`**

| Componente | Detalle |
|---|---|
| Imagen hero | Ancho completo arriba, ~45% de la pantalla |
| Botón regresar | Arriba izquierda sobre imagen, pill circular semi-transparente oscuro |
| Hoja de contenido | Tarjeta oscura rounded-top-2xl deslizándose sobre la imagen, desplazable |
| Nombre del menú | Frost White bold grande, ~24px |
| Badge tipo comida | Pill `#749a76` pequeño: `ALMUERZO` |
| Descripción | Texto cuerpo, sage, 2–3 líneas |
| Sección nutrición | Etiqueta `"Nutrición"` + divisor delgado |
| Barras de macros (detalle) | Tres barras ancho completo: `Proteína — 38g (35%)` barra `#14ff69`; `Carbohidratos — 52g (48%)` ámbar; `Grasas — 14g (13%)` naranja; cada barra con pista de fondo |
| Total calorías | Número grande `"463 kcal"` alineado derecha, etiqueta sage |
| Sección micronutrientes | Lista plegable en 2 columnas: Vitamina C, Hierro, Calcio, Fibra, Sodio, etc. |
| Texto de cobertura de objetivo | Caja destacada (bg tintado verde sutil): `"Este menú cubre ~72% de tu objetivo diario de proteína para el almuerzo"` |
| Botón agendar | Parte inferior fija, ancho completo, `#14ff69`, texto `#131e13`, bold — `"Agendar este menú"` |

---

## Fase 3 — Agenda Mobile (2 pantallas)

### Pantalla 3.1 — Calendario Mensual
**`03_schedule/01_monthly_calendar.html`**

| Componente | Detalle |
|---|---|
| Encabezado | `"Mi Agenda"` bold izquierda, mes/año centro con flechas izquierda/derecha |
| Grid del calendario | 7 columnas (Lun–Dom), grid estándar mensual, celda ~44px |
| Celda de hoy | Círculo relleno `#14ff69` detrás del número de fecha |
| Celda con pedido | Número de fecha + 1–3 íconos de rayo pequeños debajo, con colores: desayuno `#f59e0b` (ámbar), almuerzo `#14ff69`, cena `#a78bfa` (violeta) |
| Día vacío | Solo número de fecha, frost white |
| Días pasados | Sage, atenuado |
| Leyenda | Fila debajo del calendario: íconos de rayo coloreados con etiquetas `Desayuno · Almuerzo · Cena` |

---

### Pantalla 3.2 — Vista Semanal
**`03_schedule/02_weekly_view.html`**

| Componente | Detalle |
|---|---|
| Tira de semana | 7 días horizontal, hoy destacado; deslizar para cambiar semana |
| Lista vertical | Agrupado por encabezado de día (`LUN 26`, etc.) como separadores |
| Tarjeta de pedido | Izquierda: miniatura foto redondeada; Centro: nombre menú bold, badge tipo, notas; Derecha: resumen de macros P/C/G |
| Día vacío | Fila placeholder: `"Sin comidas agendadas"` + botón `"+ Agregar"` en sage |
| Aviso cierre de pedidos | Si es hoy, banner pequeño: `"Cierre de hoy: 10:00 AM — 2h 34m restantes"` |

---

## Fase 4 — Admin Dashboard Desktop (4 pantallas)

Todas las pantallas admin comparten una **barra lateral** (220px fija izquierda) y una barra de encabezado superior.

### Barra Lateral Compartida
| Elemento | Detalle |
|---|---|
| Logo | `⚡ Fuel Admin` — parte superior de la barra |
| Ítems de navegación | Dashboard, Menús, Pedidos, Cocina, Entregas, Analíticas, Ajustes — cada uno con ícono |
| Ítem activo | Barra acento izquierda `#14ff69`, fondo tintado |
| Parte inferior | Avatar usuario admin + nombre + cerrar sesión |
| Esquema de color | Barra lateral `#131e13`, área principal `#f1fcf1` |

---

### Pantalla 4.1 — Agregar Menú
**`04_admin/01_add_menu.html`**

| Componente | Detalle |
|---|---|
| Título | `"Agregar Nuevo Menú"` + breadcrumb `Menús / Nuevo` |
| Layout dos columnas | Columna izquierda (~60%): campos del formulario. Columna derecha (~40%): subida de imagen + vista previa |
| Zona de imagen | Borde punteado rounded-2xl, zona drag-drop, clic para subir, muestra vista previa al seleccionar |
| Campos del formulario | Nombre del menú, Descripción, Categoría (pill select: Desayuno/Almuerzo/Cena), Tiempo de preparación (número + `min`), Toggle de disponibilidad |
| Sección ingredientes | Filas repetibles: nombre ingrediente + cantidad (g) + botón `+ Agregar Ingrediente` |
| Sección nutrición | Grid: Calorías, Proteína, Carbohidratos, Grasas, Fibra, Sodio — inputs numéricos con etiqueta |
| Alérgenos | Pills multi-select (mismo estilo que pantalla 1.5) |
| Botón guardar | Alineado derecha, `#14ff69` — `"Guardar Menú"` + ghost `"Guardar Borrador"` |

---

### Pantalla 4.2 — Analíticas
**`04_admin/02_analytics.html`**

| Componente | Detalle |
|---|---|
| Tarjetas KPI (4 columnas) | Pedidos Hoy, Ingresos del Día, Usuarios Activos, Comidas en Preparación — número grande, badge delta %, mini spark |
| Gráfico de pedidos (línea) | Ancho completo, serie de tiempo, línea `#14ff69`, filtro de fecha arriba derecha |
| Popularidad de menús (barras) | Barras horizontales por nombre de menú, relleno `#749a76`, ordenado por conteo |
| Distribución de macros (dona) | Gráfico dona pequeño mostrando ratios P/C/G agregados |
| Tabla de pedidos recientes | Columnas: Código, Cliente, Menú, Tipo, Hora, Badge de estado, Acción |
| Badges de estado | `Pendiente` sage, `En preparación` ámbar, `Listo` verde, `Entregado` atenuado |

---

### Pantalla 4.3 — Pedidos de Cocina
**`04_admin/03_kitchen_orders.html`**

| Componente | Detalle |
|---|---|
| Encabezado | `"Dashboard de Cocina"` + reloj en vivo + pill `"Servicio de Almuerzo"` |
| Tabs de tipo de comida | `Desayuno (12)` `Almuerzo (34)` `Cena (8)` — tab activo subrayado en `#14ff69` |
| Grid de pedidos | 3–4 columnas, tarjetas |
| Tarjeta de pedido | Arriba: código `#FUL-1042` bold + badge de estado. Medio: nombre cliente, nombre menú bold, miniatura. Abajo: íconos de alérgenos, timestamp |
| Badges de estado (interactivos) | Pill con nombre de estado — clic cicla: Pendiente → En preparación → Listo |
| Íconos de alérgenos | Íconos pequeños en fila (trigo, leche, nuez, etc.) |

---

### Pantalla 4.4 — Detalle de Pedido (Cocina)
**`04_admin/04_order_detail.html`**

| Componente | Detalle |
|---|---|
| Encabezado | Código pedido + nombre cliente + badge estado + botón imprimir |
| Info del menú | Foto + nombre menú + badge tipo + tiempo de preparación |
| Lista de ingredientes | Tabla: Ingrediente / Cantidad base / Cantidad ajustada (para objetivos del usuario) — cantidad ajustada en bold |
| Sección de alérgenos | Tarjeta de advertencia prominente (fondo tintado rojo): lista todos los alérgenos con íconos |
| Solicitudes especiales | Caja destacada: texto del usuario verbatim, solo lectura |
| Pasos de estado | Progreso lineal: `Recibido → En preparación → Listo → Entregado` con timestamps |
| Botón imprimir / etiqueta | `"Imprimir Ticket"` — `#14ff69` |

---

## Fase 5 — Ticket / Etiqueta de Comida
**`05_ticket/meal_ticket.html`**

Optimizado para impresión, fondo blanco, proporciones ~100mm×150mm renderizadas en pantalla. Múltiples ejemplos mostrados lado a lado.

| Componente | Detalle |
|---|---|
| Barra superior | Logo `⚡ Fuel` izquierda + código `#FUL-1042` derecha, borde inferior delgado |
| Nombre del cliente | Grande bold, ~20px |
| Nombre del menú | Medium bold, debajo del nombre |
| Tipo de comida + fecha | `ALMUERZO — 26 de Mayo, 2026` en sage más pequeño |
| Código QR | Cuadrado ~80×80px, centrado o columna derecha |
| Fila de macros | Compacta 3 columnas: `P 38g · C 52g · G 14g` con puntos de color |
| Alérgenos | Íconos de alérgenos o texto: `⚠ Contiene: Lácteos, Gluten` en ámbar |
| Notas especiales | Caja pequeña con notas de preparación del usuario |
| Pie de página | Borde superior delgado, timestamp `Preparado a las 08:42 AM`, pequeño |
| Estilos de impresión | `@media print` oculta cualquier contenedor, fuerza fondo blanco |

---

## Fase 6 — Dashboard de Repartidor Mobile
**`06_delivery/delivery_dashboard.html`**

| Componente | Detalle |
|---|---|
| Encabezado | Logo `⚡ Fuel`, avatar + nombre del repartidor derecha, badge `"En servicio"` verde |
| Fila resumen | `"Hoy: 28 entregas · 4 zonas"` — pills de estadísticas pequeñas |
| Grupos por zona | Secciones colapsables, etiquetadas `"Zona A — Centro (8)"` con dirección |
| Encabezado de zona | Nombre zona + conteo + botón ghost `"Ver mapa"` |
| Fila de comida | Dentro de cada grupo: pill código `#FUL-1042`, nombre cliente, badge tipo (`ALMUERZO`) |
| Entregados vs Pendientes | Filas entregadas atenuadas + tachado en código; pendientes normal |
| Botón CTA inferior | Grande, fijo abajo, `"Entregar ⚡"` ancho completo, `#14ff69`, texto `#131e13` |
| Barra de progreso | Arriba de la página: `"12 / 28 entregadas"` con barra delgada `#14ff69` |

---

*Última actualización: 26 de Mayo, 2026*
