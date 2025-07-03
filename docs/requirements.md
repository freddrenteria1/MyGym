# 📋 Requisitos Funcionales - MyGym

## 1. 👥 Gestión de Usuarios

### 1.1 Registro y Autenticación
- **RF-001**: El sistema debe permitir el registro de nuevos miembros
- **RF-002**: El sistema debe autenticar usuarios con email/username y contraseña
- **RF-003**: El sistema debe manejar diferentes roles (Admin, Staff, Miembro)
- **RF-004**: El sistema debe permitir recuperación de contraseña
- **RF-005**: El sistema debe mantener sesiones seguras

### 1.2 Perfiles de Usuario
- **RF-006**: Los miembros deben poder actualizar su información personal
- **RF-007**: El sistema debe almacenar datos médicos básicos (alergias, condiciones)
- **RF-008**: El sistema debe permitir subir foto de perfil
- **RF-009**: Los usuarios deben poder configurar preferencias de notificación

## 2. 🏋️‍♂️ Gestión de Membresías

### 2.1 Tipos de Membresía
- **RF-010**: El sistema debe manejar diferentes tipos de membresía (Básica, Premium, VIP)
- **RF-011**: Cada membresía debe tener duración configurable
- **RF-012**: El sistema debe manejar precios diferentes por tipo de membresía
- **RF-013**: El sistema debe permitir membresías familiares o grupales

### 2.2 Control de Membresías
- **RF-014**: El sistema debe notificar membresías próximas a vencer
- **RF-015**: El sistema debe suspender automáticamente membresías vencidas
- **RF-016**: El sistema debe permitir renovación de membresías
- **RF-017**: El sistema debe generar reportes de membresías activas/inactivas

## 3. 🚪 Control de Acceso

### 3.1 Check-in/Check-out
- **RF-018**: El sistema debe registrar entrada y salida de miembros
- **RF-019**: El sistema debe validar membresía activa en el check-in
- **RF-020**: El sistema debe mostrar capacidad actual del gimnasio
- **RF-021**: El sistema debe generar alertas por sobrecapacidad

### 3.2 Horarios y Restricciones
- **RF-022**: El sistema debe manejar horarios de operación
- **RF-023**: Diferentes membresías pueden tener horarios de acceso diferentes
- **RF-024**: El sistema debe restringir acceso fuera de horarios permitidos

## 4. 💪 Gestión de Entrenamientos

### 4.1 Planes y Rutinas
- **RF-025**: Los entrenadores deben poder crear planes de entrenamiento
- **RF-026**: Los miembros deben poder seguir rutinas asignadas
- **RF-027**: El sistema debe permitir crear rutinas personalizadas
- **RF-028**: El sistema debe sugerir ejercicios basados en objetivos

### 4.2 Seguimiento de Progress
- **RF-029**: Los miembros deben poder registrar pesos y repeticiones
- **RF-030**: El sistema debe mostrar gráficos de progreso
- **RF-031**: El sistema debe calcular estadísticas de entrenamiento
- **RF-032**: Los entrenadores deben poder revisar el progreso de sus clientes

## 5. 🏃‍♂️ Gestión de Clases Grupales

### 5.1 Programación de Clases
- **RF-033**: El sistema debe permitir programar clases grupales
- **RF-034**: Cada clase debe tener instructor asignado
- **RF-035**: Las clases deben tener capacidad máxima configurable
- **RF-036**: El sistema debe manejar horarios de clases

### 5.2 Reservas
- **RF-037**: Los miembros deben poder reservar lugar en clases
- **RF-038**: El sistema debe manejar lista de espera para clases llenas
- **RF-039**: El sistema debe permitir cancelar reservas
- **RF-040**: El sistema debe notificar cambios en las clases

## 6. 💰 Gestión Financiera

### 6.1 Facturación
- **RF-041**: El sistema debe generar facturas automáticas
- **RF-042**: El sistema debe manejar diferentes métodos de pago
- **RF-043**: El sistema debe registrar pagos recibidos
- **RF-044**: El sistema debe generar recibos

### 6.2 Productos y Servicios
- **RF-045**: El sistema debe manejar venta de productos (suplementos, ropa)
- **RF-046**: El sistema debe manejar servicios adicionales (masajes, nutrición)
- **RF-047**: El sistema debe manejar inventario de productos
- **RF-048**: El sistema debe calcular comisiones por ventas

## 7. 🏋️ Gestión de Equipos

### 7.1 Inventario de Equipos
- **RF-049**: El sistema debe mantener registro de todos los equipos
- **RF-050**: Cada equipo debe tener estado (Disponible, En mantenimiento, Fuera de servicio)
- **RF-051**: El sistema debe programar mantenimiento preventivo
- **RF-052**: El sistema debe registrar incidencias y reparaciones

### 7.2 Reserva de Equipos
- **RF-053**: Los miembros deben poder reservar equipos específicos
- **RF-054**: El sistema debe manejar turnos para equipos populares
- **RF-055**: El sistema debe notificar cuando un equipo reservado esté disponible

## 8. 📊 Reportes y Analytics

### 8.1 Reportes Operativos
- **RF-056**: El sistema debe generar reportes de asistencia diaria/mensual
- **RF-057**: El sistema debe generar reportes financieros
- **RF-058**: El sistema debe mostrar estadísticas de uso de equipos
- **RF-059**: El sistema debe generar reportes de clases más populares

### 8.2 Dashboard Administrativo
- **RF-060**: El sistema debe mostrar métricas en tiempo real
- **RF-061**: El sistema debe mostrar alertas importantes
- **RF-062**: El sistema debe permitir exportar reportes a PDF/Excel

## 9. 📱 Comunicación y Notificaciones

### 9.1 Sistema de Notificaciones
- **RF-063**: El sistema debe enviar notificaciones por email
- **RF-064**: El sistema debe enviar notificaciones push (si hay app móvil)
- **RF-065**: El sistema debe notificar vencimiento de membresías
- **RF-066**: El sistema debe notificar cambios en clases programadas

### 9.2 Comunicación Interna
- **RF-067**: El sistema debe permitir mensajes entre staff
- **RF-068**: Los entrenadores deben poder enviar mensajes a sus clientes
- **RF-069**: El sistema debe manejar anuncios generales

## 10. 🔧 Administración del Sistema

### 10.1 Configuración
- **RF-070**: El sistema debe permitir configurar horarios de operación
- **RF-071**: El sistema debe permitir configurar precios y tarifas
- **RF-072**: El sistema debe permitir configurar capacidades máximas
- **RF-073**: El sistema debe permitir gestionar usuarios del staff

### 10.2 Backup y Seguridad
- **RF-074**: El sistema debe realizar backups automáticos
- **RF-075**: El sistema debe mantener logs de auditoría
- **RF-076**: El sistema debe cumplir con protección de datos personales

---

## 📝 Notas de Implementación
- Todos los requisitos deben ser validados con casos de uso específicos
- La priorización de requisitos se definirá en el plan de desarrollo
- Algunos requisitos pueden ser implementados en fases posteriores

*Documento actualizado: 9 de junio de 2025*
