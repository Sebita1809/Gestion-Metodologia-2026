# Sistema de Recolección de Residuos - MVP Implementation Plan

El objetivo de este plan es construir la versión fundacional (MVP) del sistema de recolección de residuos, basándonos rigurosamente en la documentación técnica provista en la carpeta `docs/`. El ecosistema técnico está definido por: React + Tailwind CSS para el Frontend, FastAPI (Python) para el Backend, Supabase externa u hospedada para base de datos y Docker para la orquestación del despliegue.

## Consideraciones Generales y Reglas de Desarrollo

1. **Spec-Driven Development:** Cualquier desarrollo futuro debe regirse por los documentos `reglas_negocio.md`, `contratos_api.md`, `historias_usuario.md`, etc.
2. **Escalabilidad y Clean Code:** Seguiremos las prácticas delineadas en `skills.md` para React, FastApi y Docker.
3. **Simplicidad Cognitiva:** El frontend deberá estar diseñado con accesibilidad prioritaria (colores clave, UI responsiva) según marca el negocio.

---

## Propuesta de Cambios e Implementación

### 1. Base de Datos y Autenticación (Supabase)
Definición e inicialización del esquema de datos relacional y configuración de Row Level Security (RLS) para proteger las operaciones según los roles (Vecino vs Administrador).
- `database/schema.sql`: Creación de tablas de usuarios, zonas, tipo de residuo, notificaciones y reportes.
- `database/policies.sql`: Políticas de RLS de Supabase.
- `database/seed.sql`: Inserción de zonas maestras, tipos de residuos por defecto y calendarios base para probar.

### 2. Backend (Python + FastAPI)
Creación de la API REST que servirá la lógica de negocio y expondrá los endpoints. 
- `backend/requirements.txt`: Dependencias principales.
- `backend/main.py`: Punto de entrada de FastAPI.
- `backend/app/models/`: Modelos Pydantic.
- `backend/app/routers/auth.py`: Autenticación y registro de vecinos.
- `backend/app/routers/schedule.py`: Entrega de calendarios semanales y diarios.
- `backend/app/routers/locations.py`: Entrega de puntos de reciclaje filtrables por cercanía o tipo.
- `backend/app/routers/reports.py`: Manejo de las quejas o avisos (basura acumulada).
- `backend/Dockerfile`: Configuración del contenedor propio para el backend.

### 3. Frontend (React + Tailwind CSS + PWA)
Desarrollo de la aplicación web de los usuarios (Progressive Web App pidiendo geolocalización de puntos y notificaciones).
- `frontend/package.json` y `frontend/tailwind.config.js`: Estructura base del proyecto y tokens de sistema de diseño.
- `frontend/src/App.jsx`: Manejo general y ruteo.
- `frontend/src/components/MapLocations.jsx`: Mapa interactivo (ej. Leaflet).
- `frontend/src/components/ScheduleCalendar.jsx`: Vista semanal de los tipos de residuos y los colores designados.
- `frontend/src/components/ReportForm.jsx`: Flujo de denuncias.
- `frontend/src/service-worker.js`: Manejo de Notificaciones (Push).
- `frontend/Dockerfile`: Empaquetado optimizado para web.

### 4. Infraestructura Global (Docker)
Configuración para orquestar los contenedores del ecosistema.
- `docker-compose.yml`: Levantará el Frontend del lado del cliente y el Backend interno y los comunicará.

---

## Decisiones / Preguntas de Diseño Abiertas (Pendientes de resolver)

Al empezar a codificar estas partes, el equipo debe definir los siguientes puntos:

> **Base de Datos:** ¿Utilizaremos un proyecto de Supabase en la nube u hospedaremos un entorno open-source de Supabase de forma local cargado en el propio `docker-compose.yml`?

> **Mapas:** Para la Epic de "Puntos de reciclaje cercanos", ¿qué proveedor de mapas se empleará de manera predeterminada? Opciones posibles: Google Maps API, Mapbox o Leaflet/OpenStreetMap.

> **Notificaciones PWA:** Para proveer con antelación o contingencias ¿Integraremos Firebase Cloud Messaging (FCM) u otro servicio específico para el Push? ¿O se dejará un mock inicial para el MVP rápido?

---

## Plan de Verificación

Una vez que cada iteración o Pull Request termine, el equipo debe verificar la fidelidad de la entrega así:

### Pruebas Automáticas y Locales
- Validar que todo levante de cero con el comando `docker-compose up --build`.
- Ejecutar pruebas automáticas en FastAPI (ej. vía `pytest`) para los endpoints críticos de consulta de cronograma (`/api/v1/schedule/today`) y contratos de la API en `docs/contratos_api.md`.

### Verificación Manual de las Historias de Usuario
- Registrar a un "Vecino" en el Frontend y validar que se le exija y asigne su "Zona".
- Corroborar visualmente que el calendario semanal es "cognitivamente simple", es decir, que usa correctamente códigos de color para cada tipo de recolección según el MVP.
- Renderizar el mapa de puntos verdes e interactuar con el filtro de materiales.
- Realizar el proceso completo, como vecino, de emitir un reporte de basura acumulada con geolocalización.
