Las principales entidades de la base de datos son:

1. Usuario: Representa a los vecinos y administradores.
2. Zona: Representa las zonas logísticas de recolección.
3. Tipo de residuo: Representa el tipo de residuo que se recolecta.
4. Notificación: Representa las notificaciones enviadas a los usuarios.
5. Punto de Reciclaje: Representa los puntos de reciclaje geolocalizados.
6. Reporte/Denuncia: Para que el vecino pueda reportar problemas con la recolección.

Las relaciones son:

Usuario (Vecino) —> pertenece a —> Zona.

Zona —> tiene asignado —> Calendario.

Calendario —> referencia a —> Tipo de Residuo.

Punto de Reciclaje —> filtra por —> Tipo de Residuo.