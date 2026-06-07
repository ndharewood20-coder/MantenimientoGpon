# CANTV — Sistema de Gestión de Mantenimiento GPON

Plataforma web progresiva (PWA) para la gestión integral del plan de mantenimiento de la red de fibra óptica GPON de CANTV, desarrollada como parte del Proyecto de Grado de la UCAB.

## Archivos del Proyecto

| Archivo | Descripción |
|---|---|
| `index.html` | Aplicación completa (single-page app) |
| `manifest.json` | Configuración PWA para instalación en móviles |
| `service-worker.js` | Caché offline para uso sin conexión |
| `netlify.toml` | Configuración de despliegue en Netlify |
| `icon.png` | Ícono de la aplicación (logo CANTV) |

## Despliegue en Netlify

### Opción 1 — Arrastrar y soltar (más fácil)
1. Ir a [app.netlify.com](https://app.netlify.com)
2. Iniciar sesión o crear una cuenta gratuita
3. En el panel principal, arrastrar la **carpeta completa** del proyecto al área de despliegue
4. Netlify generará automáticamente una URL pública (ej: `https://cantv-gpon.netlify.app`)

### Opción 2 — GitHub + Netlify (recomendado para actualizaciones)
1. Subir todos los archivos a un repositorio de GitHub
2. En Netlify: New site → Import from Git → Seleccionar el repositorio
3. Build command: (dejar vacío)
4. Publish directory: `.` (punto)
5. Click en Deploy

## Instalación como App Móvil (PWA)

### Android (Chrome)
1. Abrir la URL del sitio en Chrome
2. Tocar el menú (tres puntos) → "Agregar a pantalla de inicio"
3. Confirmar la instalación
4. La app aparecerá como ícono en el escritorio

### iPhone / iPad (Safari)
1. Abrir la URL en Safari
2. Tocar el botón de compartir (cuadrado con flecha)
3. Seleccionar "Agregar a pantalla de inicio"
4. Confirmar el nombre y tocar "Agregar"

## Credenciales de Acceso

| Usuario | Contraseña | Rol | Zona |
|---|---|---|---|
| admin | admin123 | Administrador | Todas |
| tecnico1 | tec123 | Técnico | ALTAVISTA |
| tecnico2 | tec123 | Técnico | UNARE |
| tecnico3 | tec123 | Técnico | PURTO ORDAZ |

## Módulos Disponibles

### Administrador
- **Panel KPIs**: Disponibilidad, MTBF, MTTR, CPP, gráficos por zona y tipo
- **Órdenes de Trabajo**: Crear OTs preventivas/correctivas, asignar por zona y cuadrilla
- **Averías**: Vista completa con clasificación por severidad (5 niveles), filtros, crear OT desde avería
- **Historial**: Registro cronológico de todas las actividades con exportación
- **Red ODN**: Vista tabla + árbol interactivo con todos los detalles de conexión
- **Usuarios**: Gestión de técnicos y cuadrillas
- **Cargar Datos**: Importar Excel de averías y TDC ODN

### Técnico
- **Mis Órdenes**: Ver tareas asignadas, iniciar trabajo, completar con planilla digital
- **Averías**: Ver averías asignadas por severidad con datos del cliente
- **Red ODN**: Consultar conexiones de su zona

## Planillas Digitales Integradas

### Preventivo (Formatos MP-D-001, MP-CON-001)
- Checklists interactivos por actividad (PR-01 a PE-22)
- Registro de potencia óptica, atenuación, temperatura
- Estado general y observaciones

### Correctivo (Formato OT-GPON-001)
- Datos completos del cliente desde la avería
- Causa raíz con opciones predeterminadas
- Acción correctiva realizada
- Mediciones antes/después
- Confirmación de restablecimiento del servicio

## Clasificación de Averías (Sistema Propio)

Basado en el Anexo A del Plan de Mantenimiento:

| Código | Descripción | Severidad | Procedimiento |
|---|---|---|---|
| NNV | No Navega | Mayor (2) | MC-04 |
| NONAV | Sin Navegación | Mayor (2) | MC-04 |
| NL | Navega Lento | Degradación (5) | MC-05 |
| ONT_DANADO | ONT Dañada | Menor (4) | MC-04 |
| LOS | Pérdida de Señal PON | Crítica (1) | MC-02 |
| CORTE | Corte de Cable | Crítica (1) | MC-03 |
| OLT_FALLA | Falla Total OLT | Crítica (1) | MC-01 |
| DEGRAD | Degradación de Señal | Degradación (5) | MC-05 |
| TELIP | Falla Telefonía IP | Moderada (3) | MC-04 |
| BYPASS | Bypass de Emergencia | Crítica (1) | MC-06 |

## Notas Técnicas

- Todos los datos se almacenan en `localStorage` del navegador
- Compatible con Chrome, Firefox, Safari y Edge
- Diseño responsive para móviles, tablets y escritorio
- Sin dependencias de servidor — funciona completamente en el cliente
- Los datos persisten entre sesiones en el mismo dispositivo/navegador
