Endpoints principales:

POST /api/v1/auth/register: Registro de nuevos vecinos (incluye nombre, email y dirección para asignar zona).

GET /api/v1/user/profile: Retorna los datos del usuario y, fundamentalmente, su zona_id asignada.

GET /api/v1/schedule/zone/{zona_id}: Obtiene el cronograma completo de la semana para la zona del vecino.

Respuesta esperada: Un array de objetos con dia_semana, tipo_residuo, color_hex y horario_paso.

GET /api/v1/schedule/today: Endpoint rápido que devuelve solo qué residuo se saca hoy basándose en el token del usuario.

GET /api/v1/locations/points: Lista todos los centros de acopio.

Filtros opcionales: ?type=glass, ?lat=-34.6&lon=-58.4 (para ordenar por cercanía).

GET /api/v1/locations/points/{id}: Detalle de un punto específico (horarios y qué materiales recibe exactamente).

PATCH /api/v1/user/notifications: Permite al vecino activar/desactivar alertas o cambiar la antelación (ej: "avisame 1 hora antes").

POST /api/v1/reports: Permite al vecino subir una foto y coordenadas de basura acumulada o un punto de reciclaje lleno.

GET /api/v1/reports/my-reports: Para que el vecino vea el estado de sus reclamos (Pendiente/Resuelto).