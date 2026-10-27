# AguaAlerta Guayaquil 🌧️

Prototipo web interactivo (mobile-first) para el reto **"Lluvias intensas en Guayaquil"**. Combina participación ciudadana y datos en tiempo real para que la ciudad anticipe y responda mejor a las inundaciones.

> **Estado:** prototipo de demostración. Todos los datos son simulados; no hay backend ni APIs reales.

---

## El problema

Cada temporada de lluvias, miles de guayaquileños quedan atrapados en calles inundadas sin información actualizada. Las alertas oficiales llegan tarde y no muestran qué calles están realmente intransitables en este momento.

## La solución

AguaAlerta convierte a cada ciudadano en un sensor. Las personas reportan el nivel del agua, la comunidad lo confirma o lo desmiente, y la app sugiere rutas que evitan las zonas críticas. Un asistente de emergencia entrega pasos de seguridad al instante.

---

## Funcionalidades

| Módulo | Descripción |
|---|---|
| **Mapa interactivo** | Mapa de Guayaquil con Leaflet y pines de inundación clasificados por gravedad (bordillo, rodilla, cubre llantas). |
| **Reportar inundación** | Modal con slider de nivel del agua, medidor animado, carga de foto simulada y envío. El nuevo pin aparece en el mapa con animación. |
| **Interacción comunitaria** | Al tocar un pin: tiempo del reporte, número de confirmaciones y botones **Confirmo inundación** y **El agua ya bajó**. |
| **Ruta segura** | Dibuja una ruta que esquiva las zonas inundadas y muestra el tiempo estimado. Se puede activar y desactivar. |
| **Asistente de emergencia** | Chat simulado con respuestas rápidas ("El agua está entrando a mi casa", "Mi auto se apagó en el agua", "¿Puedo cruzar esta calle?") y botón de llamada al 911. |

---

## Estructura del proyecto

```
aguaalerta/
├── index.html              # Estructura de la página
├── css/
│   ├── base.css            # Variables, reset, toast y accesibilidad
│   ├── interfaz.css        # Barra superior, alerta, leyenda y botones flotantes
│   ├── pines.css           # Pines del mapa y popups
│   ├── modal-reporte.css   # Modal "Reportar inundación"
│   └── chat.css            # Chatbot
└── js/
    ├── config.js           # Utilidades y niveles de agua
    ├── data.js             # Reportes simulados iniciales
    ├── toast.js            # Notificaciones breves
    ├── map.js              # Mapa Leaflet y ubicación del usuario
    ├── reports.js          # Pines, popups y votos
    ├── route.js            # Ruta segura simulada
    ├── report-modal.js     # Modal de reporte
    └── chat.js             # Chatbot de emergencia
```

> Los scripts se cargan en ese orden desde `index.html`; cada archivo usa lo definido en los anteriores. Se usan scripts clásicos (no módulos ES) para que funcione con doble clic, sin servidor.

---

## Cómo ejecutarlo

No requiere instalación ni compilación.

1. Descarga la carpeta completa del proyecto (mantén la estructura de carpetas).
2. Abre `index.html` con doble clic en Chrome, Edge o Firefox.
3. Para verlo como celular: `F12` → `Ctrl + Shift + M` → elige *iPhone 14 Pro*.

**Requiere conexión a internet** para cargar los mosaicos del mapa, Leaflet y las fuentes de Google Fonts.

### Probarlo en un celular real

```bash
# Desde la carpeta del proyecto
python3 -m http.server 8000
```

Luego abre `http://<IP-de-tu-computadora>:8000/index.html` desde el celular (ambos dispositivos en la misma red Wi-Fi).

---

## Tecnologías

- **HTML5 + CSS3** (sin frameworks, un solo archivo)
- **JavaScript** vanilla
- **[Leaflet 1.9.4](https://leafletjs.com/)** para el mapa
- **CARTO / OpenStreetMap** como mosaicos del mapa
- **Google Fonts:** Bricolage Grotesque y Figtree

---

## Limitaciones del prototipo

- Los reportes, votos y la ruta no se guardan; al recargar la página todo vuelve al estado inicial.
- La ruta segura es una línea predefinida, no un cálculo real.
- El chatbot usa respuestas fijas, sin IA real.
- La ubicación del usuario es fija (norte de Guayaquil).

## Próximos pasos

- Base de datos en tiempo real para guardar y sincronizar reportes.
- Integración con datos meteorológicos (INAMHI, estaciones de la ciudad).
- Cálculo de rutas reales con un motor de enrutamiento (OSRM, Google Maps).
- Chatbot con un modelo de lenguaje y protocolos oficiales de emergencia.
- Validación de reportes (reputación del usuario y detección de duplicados).
- Notificaciones push por zona.
- Panel para el municipio con mapa de calor de zonas críticas.

