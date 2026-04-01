# Skills de Agente para el Sistema de Recolección de Residuos

En este documento se detallan las distintas skills ("habilidades") de agente que han sido instaladas para asistir y acelerar el desarrollo del **Sistema de Recolección de Residuos**. Estas extensiones aseguran que trabajemos bajo las mejores pautas de calidad para el stack seleccionado (React, FastAPI, Supabase y Docker) así como para las funcionalidades clave del proyecto (Mapas, Geolocalización y Notificaciones).

## Interfaz de Usuario (Frontend)

### 1. React Best Practices
- **Paquete:** `vercel-labs/agent-skills@react-best-practices`
- **Qué hace:** Proporciona un conjunto de directrices completas, buenas prácticas y optimizaciones de rendimiento en React.
- **Qué soluciona:** Garantiza que el desarrollo del calendario visual de recolección de residuos y los modales de reportes se rija por estructuras eficientes. Mantiene limpio el código de UI, haciéndolo escalable y simple para el usuario final (vecinos).

### 2. Tailwind Design System
- **Paquete:** `wshobson/agents@tailwind-design-system`
- **Qué hace:** Proporciona asistencia para construir un sistema de diseño estructurado utilizando Tailwind CSS (design tokens, colores y patrones responsivos).
- **Qué soluciona:** Asegura que la aplicación sea intuitiva y muy clara, cumpliendo la regla de simplicidad cognitiva donde los usuarios puedan visualizar los colores de reciclaje (verde, marrón, etc.) sin problemas, además de facilitar una UI 100% responsiva para celulares.

---

## Funcionalidades Core (Geolocalización y Notificaciones)

### 3. Geo Fundamentals
- **Paquete:** `sickn33/antigravity-awesome-skills@geo-fundamentals`
- **Qué hace:** Agrega soporte especializado para manejar lógicas de geolocalización, manipulación de coordenadas y renderizado de mapas interactivos.
- **Qué soluciona:** Resuelve la Epic de **"Puntos de reciclaje cercanos"**. Facilita la carga de mapas interactivos donde el vecino puede localizar Puntos Verdes y asegura que al sistema ingrese las coordenadas correctas cuando se denuncian acumulaciones de basura.

### 4. PWA Development
- **Paquete:** `alinaqi/claude-bootstrap@pwa-development`
- **Qué hace:** Brinda los patrones necesarios para convertir la app React en una Progressive Web App (PWA) de alto rendimiento, incluyendo el manejo de Service Workers y Notificaciones Push.
- **Qué soluciona:** Es vital para el envío de notificaciones en tiempo real o con antelación (ej: alerta de sacar la basura 2 horas antes de que pase el camión o alertas de contingencia/paro). Permite que el sistema envíe push notifications directamente a los celulares.

---

## Lógica de Servidor y Acceso a Datos (Backend)

### 5. FastAPI Templates
- **Paquete:** `wshobson/agents@fastapi-templates`
- **Qué hace:** Asiste entregando plantillas comprobadas para diseñar APIs estandarizadas, inyección de dependencias y rutas asíncronas con Python y FastAPI.
- **Qué soluciona:** Reducirá drásticamente el tiempo de modelado de las APIs de lectura de calendarios por zona logística y de altas de denuncias, permitiendo atender la demanda concurrente de los vecinos a gran velocidad.

### 6. Supabase Postgres Best Practices
- **Paquete:** `supabase/agent-skills@supabase-postgres-best-practices`
- **Qué hace:** Brinda asesoría y patrones específicos para bases de datos relacionales aprovechando utilidades como Row Level Security (RLS) y optimizaciones de PostGIS si fuesen necesarias para datos geoespaciales.
- **Qué soluciona:** Evita consultas ineficientes y asegura que sólo el "Administrador (Municipio)" pueda modificar las rutas y calendarios de recolección, bloqueando ese acceso de forma segura contra otros usuarios por medio de políticas nativas de DB.

---

## Infraestructura y Despliegue

### 7. Docker Expert
- **Paquete:** `sickn33/antigravity-awesome-skills@docker-expert`
- **Qué hace:** Experto en creación de contenedores Docker, *multi-stage builds* y manejo de variables de entorno (ej: API Keys de Mapas o Supabase).
- **Qué soluciona:** Garantiza que los entornos de desarrollo (Dev), prueba (Staging) y Producción (Prod) del sistema de residuos corran sin discrepancias, asegurando inmutabilidad en la entrega del software desde React hasta la API en FastAPI.
