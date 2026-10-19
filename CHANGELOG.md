# Changelog — Trento Social

Historial de cambios del registro vecinal de Trento Residencial.
Lo más reciente arriba. Formato de fecha: DD mmm AAAA · HH:MM (hora local CDMX).

## v1.6 — 18 oct 2026 · 22:10

### Corregido
- `panel.html` seguía apuntando a `http://localhost:10000` en producción en vez de `https://trento-social-backend.onrender.com`, por lo que el panel de administración nunca podía conectar al cargar registros, exportar CSV o ver analíticas del acortador desde `https://hackerjj.github.io/trento-social/panel.html`. Corregido `API_URL`.

## v1.5 — 19 oct 2026 · 09:10

### Agregado
- Validación de número duplicado en el backend: si el WhatsApp ya está registrado, responde 409 y el frontend muestra "Este número ya se encuentra registrado" en vez de crear un segundo registro.
- Panel de administración activado en producción con token `TRENTO_ADMIN_TOKEN`.
- Favicon con el logo circular de Trento Social en las 3 páginas.

## v1.4 — 18 oct 2026 · 22:25

### Agregado
- Overlay de carga con barra de progreso mientras se envía el registro al backend. El botón "Registrarme" ya no parece congelado durante los segundos que tarda el servidor en responder.
- Nota que aparece a los 3 segundos si la espera se alarga, aclarando que el servidor gratuito de Render puede estar "despertando" tras estar inactivo.

## v1.3 — 17 oct 2026 · 06:30

### Agregado
- Campo obligatorio "¿Cuántas personas viven en tu domicilio?" en el formulario de registro, para controlar cuántos registros puede reportar un mismo domicilio y evitar duplicados de tráfico.
- Explicación visible: cada persona debe registrarse por separado con su propio número de WhatsApp, y el total de registros del domicilio debe coincidir con el número indicado (si viven 3, deben completarse 3 registros).

### Cambiado
- Backend (`RegistroController` + modelo `TrentoRegistration`) valida, guarda y exporta el nuevo campo `personas_vivienda`.
- Panel de administración muestra una columna "Personas" en la tabla de registros.

### Corregido
- Backend en Render conectado correctamente a MongoDB: se corrigieron las variables `MONGO_URI` (tenía pegado el valor de APP_KEY) y `APP_KEY`. El formulario de registro ya guarda en la base de datos (verificado con un registro de prueba exitoso).

## v1.2 — 15 oct 2026 · 22:05

### Corregido
- Formulario de contacto activado con el Access Key de Web3Forms (`ed4b98c1-...`). Los mensajes de los vecinos ya llegan a `jairalonsogarcias@gmail.com`.

## v1.1 — 15 oct 2026 · 21:40

### Agregado
- Aviso de Privacidad como modal con scroll propio (abre dentro de la página, no en otra pestaña), con buen diseño y barra de scroll personalizada.
- Sección "Una sola persona a cargo": aclara que una única persona responsable administra los datos y que no se divulgan ni comparten con terceros comerciales.
- Sección "Seguridad de tu información": explica el cifrado SSL/HTTPS en tránsito, almacenamiento con acceso restringido, acceso mínimo por contraseña y ausencia de terceros comerciales.
- Formulario de contacto dentro del aviso (Web3Forms) que envía los mensajes a `jairalonsogarcias@gmail.com` sin exponer el correo del responsable en el sitio.
- Pantalla de éxito tras el registro, con botón directo al grupo de WhatsApp (`https://chat.whatsapp.com/BTkXLSDkTIg21kgDzuMOcm`).
- Chip de versión + modal de historial de cambios (igual que las demás herramientas del workspace).

### Cambiado
- Citas legales de la LFPDPPP 2025 verificadas con fuentes públicas: artículo 15 (contenido del aviso), plazos ARCO de 20 + 15 días, autoridad = Secretaría Anticorrupción y Buen Gobierno (ya no INAI). Se quitó la nota de "pendiente de verificar" y se reemplazó por un disclaimer de orientación general.

## v1.0 — 15 oct 2026 · 17:45

### Agregado
- Formulario de registro vecinal mobile-first con validación de teléfono MX, consentimiento obligatorio y tracking invisible (tiempo en página, referrer, user-agent, idioma, pantalla).
- Logo circular "Trento Social" (personas tomadas de la mano alrededor del logo de Trento Residencial).
- Backend Laravel 11 calcado del stack de Sushi Queen (Mongo + Redis aislados con prefijo `trento:` y colecciones `trento_*`, sin crear base ni instancia nueva).
- Acortador de enlaces propio tipo bit.ly con métricas completas (IP, país, ciudad, dispositivo, navegador, OS, referrer, timestamp) y panel de analíticas.
- Aviso de privacidad conforme a la nueva LFPDPPP 2025.
- Panel de administración con registros, tracking, export CSV y analíticas del acortador.
- Publicación del frontend en GitHub Pages con SSL gratuito (https://hackerjj.github.io/trento-social/).
