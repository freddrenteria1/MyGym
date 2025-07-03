# 👤 Historias de Usuario - MyGym

## 🎭 Personas del Sistema

### 1. **María González** - Miembro Regular
- 32 años, profesional ocupada
- Va al gym 4 veces por semana
- Le gusta las clases grupales
- Prefiere tecnología simple y rápida

### 2. **Carlos Rodríguez** - Entrenador Personal
- 28 años, certificado en fitness
- Maneja 15-20 clientes
- Necesita seguimiento detallado del progreso
- Quiere herramientas para comunicarse con clientes

### 3. **Ana López** - Administradora del Gym
- 45 años, gerente general
- Responsable de operaciones y finanzas
- Necesita reportes y métricas claras
- Maneja staff de 8 personas

### 4. **Roberto Silva** - Miembro Premium
- 40 años, empresario
- Membresía VIP, horarios flexibles
- Usa servicios adicionales (masajes, nutrición)
- Valora atención personalizada

---

## 🏃‍♂️ Historias de Usuario por Módulo

### 1. Registro y Autenticación

**HU-001: Registro de Nuevo Miembro**
> **Como** visitante interesado
> **Quiero** registrarme en el sistema
> **Para** acceder a los servicios del gimnasio

**Criterios de Aceptación:**
- Puedo completar un formulario con mis datos básicos
- Puedo seleccionar el tipo de membresía que deseo
- Recibo confirmación por email al registrarme
- Mi cuenta queda pendiente hasta que complete el pago

**HU-002: Inicio de Sesión**
> **Como** miembro registrado
> **Quiero** iniciar sesión en el sistema
> **Para** acceder a mi cuenta y servicios

**Criterios de Aceptación:**
- Puedo ingresar con email/username y contraseña
- Si olvido mi contraseña, puedo recuperarla por email
- El sistema recuerda mi sesión por un tiempo determinado
- Recibo mensaje de error claro si las credentials son incorrectas

### 2. Gestión de Perfil

**HU-003: Actualizar Información Personal**
> **Como** miembro (María)
> **Quiero** actualizar mi información personal
> **Para** mantener mis datos actualizados

**Criterios de Aceptación:**
- Puedo editar mi nombre, teléfono, dirección
- Puedo cambiar mi contraseña
- Puedo subir una foto de perfil
- Los cambios se guardan inmediatamente

**HU-004: Configurar Información Médica**
> **Como** miembro con condiciones médicas
> **Quiero** registrar mi información médica
> **Para** que el staff esté informado en caso de emergencia

**Criterios de Aceptación:**
- Puedo registrar alergias conocidas
- Puedo indicar condiciones médicas relevantes
- Puedo especificar contacto de emergencia
- Esta información es visible solo para staff autorizado

### 3. Control de Acceso

**HU-005: Check-in en el Gimnasio**
> **Como** miembro (María)
> **Quiero** hacer check-in rápidamente
> **Para** acceder al gimnasio sin complicaciones

**Criterios de Aceptación:**
- Puedo hacer check-in con mi teléfono o tarjeta
- El sistema valida que mi membresía esté activa
- Veo un mensaje de bienvenida personalizado
- El sistema registra mi hora de entrada

**HU-006: Ver Capacidad del Gimnasio**
> **Como** miembro (Roberto)
> **Quiero** ver qué tan lleno está el gimnasio
> **Para** decidir cuándo ir a entrenar

**Criterios de Aceptación:**
- Puedo ver la capacidad actual en tiempo real
- Puedo ver estadísticas de horarios menos concurridos
- Recibo notificación cuando hay menos gente
- Puedo hacer check-in remoto para reservar mi lugar

### 4. Gestión de Entrenamientos

**HU-007: Seguir Plan de Entrenamiento**
> **Como** miembro (María)
> **Quiero** seguir un plan de entrenamiento personalizado
> **Para** alcanzar mis objetivos fitness

**Criterios de Aceptación:**
- Puedo ver mi rutina del día claramente
- Puedo marcar ejercicios como completados
- Puedo registrar pesos y repeticiones realizadas
- Puedo ver mi progreso a lo largo del tiempo

**HU-008: Crear Plan para Cliente**
> **Como** entrenador (Carlos)
> **Quiero** crear planes de entrenamiento para mis clientes
> **Para** ayudarlos a alcanzar sus objetivos

**Criterios de Aceptación:**
- Puedo crear rutinas personalizadas por cliente
- Puedo ajustar ejercicios, series, repeticiones y pesos
- Puedo clonar rutinas exitosas para otros clientes
- Puedo hacer ajustes basados en el progreso del cliente

### 5. Clases Grupales

**HU-009: Reservar Clase Grupal**
> **Como** miembro (María)
> **Quiero** reservar lugar en clases grupales
> **Para** asegurar mi participación

**Criterios de Aceptación:**
- Puedo ver el horario de todas las clases disponibles
- Puedo reservar mi lugar con un click
- Puedo cancelar mi reserva hasta 2 horas antes
- Recibo notificación de confirmación y recordatorios

**HU-010: Gestionar Lista de Espera**
> **Como** miembro interesado
> **Quiero** unirme a la lista de espera de clases llenas
> **Para** tener oportunidad de participar si hay cancelaciones

**Criterios de Aceptación:**
- Puedo unirme a lista de espera automáticamente
- Recibo notificación inmediata si se libera un cupo
- Tengo 15 minutos para confirmar mi participación
- Puedo ver mi posición en la lista de espera

### 6. Facturación y Pagos

**HU-011: Ver Estado de Membresía**
> **Como** miembro (Roberto)
> **Quiero** ver el estado de mi membresía y pagos
> **Para** estar al día con mis obligaciones

**Criterios de Aceptación:**
- Puedo ver la fecha de vencimiento de mi membresía
- Puedo ver el historial de pagos realizados
- Puedo descargar facturas y recibos
- Recibo notificación antes de que venza mi membresía

**HU-012: Renovar Membresía**
> **Como** miembro (María)
> **Quiero** renovar mi membresía fácilmente
> **Para** continuar usando los servicios del gimnasio

**Criterios de Aceptación:**
- Puedo renovar directamente desde la aplicación
- Puedo cambiar mi tipo de membresía al renovar
- Puedo configurar renovación automática
- Recibo confirmación inmediata del pago

### 7. Productos y Servicios

**HU-013: Comprar Productos**
> **Como** miembro (Roberto)
> **Quiero** comprar suplementos y productos del gym
> **Para** complementar mi entrenamiento

**Criterios de Aceptación:**
- Puedo ver catálogo de productos disponibles
- Puedo agregar productos a un carrito de compras
- Puedo pagar junto con mi mensualidad o por separado
- Puedo recoger productos en recepción

**HU-014: Agendar Servicios Adicionales**
> **Como** miembro premium (Roberto)
> **Quiero** agendar servicios como masajes o consulta nutricional
> **Para** aprovechar los beneficios de mi membresía

**Criterios de Aceptación:**
- Puedo ver disponibilidad de servicios en calendario
- Puedo agendar citas según mi disponibilidad
- Puedo cancelar o reprogramar con anticipación
- Recibo recordatorios de mis citas agendadas

### 8. Comunicación

**HU-015: Recibir Notificaciones Relevantes**
> **Como** miembro (María)
> **Quiero** recibir notificaciones importantes
> **Para** estar informada sobre cambios y eventos

**Criterios de Aceptación:**
- Recibo notificaciones sobre cambios en mis clases
- Recibo recordatorios de vencimiento de membresía
- Puedo configurar qué notificaciones quiero recibir
- Puedo elegir recibirlas por email, SMS o push

**HU-016: Comunicarse con Clientes**
> **Como** entrenador (Carlos)
> **Quiero** comunicarme con mis clientes
> **Para** brindar mejor seguimiento y motivación

**Criterios de Aceptación:**
- Puedo enviar mensajes individuales a mis clientes
- Puedo enviar recordatorios sobre rutinas
- Puedo compartir consejos y motivación
- Los clientes pueden responder mis mensajes

### 9. Administración

**HU-017: Ver Dashboard Administrativo**
> **Como** administradora (Ana)
> **Quiero** ver métricas clave del gimnasio
> **Para** tomar decisiones informadas

**Criterios de Aceptación:**
- Puedo ver asistencia diaria en tiempo real
- Puedo ver ingresos del mes actual vs anterior
- Puedo ver clases más populares y menos populares
- Puedo ver alertas importantes que requieren acción

**HU-018: Generar Reportes**
> **Como** administradora (Ana)
> **Quiero** generar reportes detallados
> **Para** analizar el desempeño del negocio

**Criterios de Aceptación:**
- Puedo generar reportes financieros mensuales
- Puedo exportar reportes a PDF y Excel
- Puedo personalizar rangos de fechas para reportes
- Puedo agendar reportes automáticos por email

### 10. Gestión de Staff

**HU-019: Gestionar Horarios del Staff**
> **Como** administradora (Ana)
> **Quiero** gestionar horarios y turnos del staff
> **Para** asegurar cobertura adecuada

**Criterios de Aceptación:**
- Puedo crear horarios semanales para cada empleado
- Puedo manejar cambios de turno y sustituciones
- Puedo ver qué empleados están trabajando en tiempo real
- Puedo calcular horas trabajadas para nómina

---

## 🎯 Épicas del Proyecto

### Épica 1: Gestión de Miembros
- HU-001, HU-002, HU-003, HU-004, HU-011, HU-012

### Épica 2: Control de Acceso y Asistencia
- HU-005, HU-006

### Épica 3: Sistema de Entrenamientos
- HU-007, HU-008

### Épica 4: Clases Grupales
- HU-009, HU-010

### Épica 5: Comercio y Facturación
- HU-013, HU-014

### Épica 6: Comunicación y Notificaciones
- HU-015, HU-016

### Épica 7: Administración y Reportes
- HU-017, HU-018, HU-019

---

*Documento actualizado: 9 de junio de 2025*
