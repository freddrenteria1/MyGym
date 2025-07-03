# 🚀 API Design - MyGym REST API

## 📋 Información General

**Base URL**: `https://api.mygym.com/v1`  
**Formato**: JSON  
**Autenticación**: JWT Bearer Token  
**Rate Limiting**: 1000 requests/hour por usuario  

## 🔐 Autenticación

### Endpoints de Autenticación

#### POST /auth/register
Registrar nuevo usuario

**Request Body:**
```json
{
  "email": "maria@email.com",
  "password": "SecurePass123!",
  "firstName": "María",
  "lastName": "González",
  "phone": "+52-555-1234567",
  "dateOfBirth": "1992-05-15",
  "membershipTypeId": 1
}
```

**Response (201):**
```json
{
  "success": true,
  "message": "Usuario registrado exitosamente",
  "data": {
    "user": {
      "id": 123,
      "email": "maria@email.com",
      "firstName": "María",
      "lastName": "González",
      "role": "member"
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  }
}
```

#### POST /auth/login
Iniciar sesión

**Request Body:**
```json
{
  "email": "maria@email.com",
  "password": "SecurePass123!"
}
```

**Response (200):**
```json
{
  "success": true,
  "data": {
    "user": {
      "id": 123,
      "email": "maria@email.com",
      "firstName": "María",
      "lastName": "González",
      "role": "member"
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "expiresIn": "24h"
  }
}
```

#### POST /auth/logout
Cerrar sesión

**Headers:** `Authorization: Bearer {token}`

**Response (200):**
```json
{
  "success": true,
  "message": "Sesión cerrada exitosamente"
}
```

#### POST /auth/forgot-password
Recuperar contraseña

**Request Body:**
```json
{
  "email": "maria@email.com"
}
```

---

## 👥 Gestión de Usuarios

### GET /users/profile
Obtener perfil del usuario autenticado

**Headers:** `Authorization: Bearer {token}`

**Response (200):**
```json
{
  "success": true,
  "data": {
    "id": 123,
    "email": "maria@email.com",
    "firstName": "María",
    "lastName": "González",
    "phone": "+52-555-1234567",
    "dateOfBirth": "1992-05-15",
    "profilePicture": "https://cdn.mygym.com/profiles/123.jpg",
    "role": "member",
    "emergencyContact": {
      "name": "Juan González",
      "phone": "+52-555-7654321",
      "relationship": "hermano"
    },
    "medicalInfo": {
      "allergies": ["penicilina"],
      "conditions": [],
      "notes": "Ninguna restricción especial"
    },
    "createdAt": "2025-01-15T10:00:00Z"
  }
}
```

### PUT /users/profile
Actualizar perfil del usuario

**Headers:** `Authorization: Bearer {token}`

**Request Body:**
```json
{
  "firstName": "María Elena",
  "phone": "+52-555-9876543",
  "emergencyContact": {
    "name": "Juan González",
    "phone": "+52-555-7654321",
    "relationship": "hermano"
  }
}
```

### POST /users/profile/picture
Subir foto de perfil

**Headers:** `Authorization: Bearer {token}`  
**Content-Type:** `multipart/form-data`

**Request:** Form data con archivo imagen

---

## 🏋️‍♂️ Gestión de Membresías

### GET /memberships/types
Obtener tipos de membresía disponibles

**Response (200):**
```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "name": "Básica",
      "description": "Acceso a área de pesas y cardio",
      "price": 800.00,
      "durationMonths": 1,
      "benefits": [
        "Acceso a gimnasio",
        "Casillero",
        "Evaluación inicial"
      ],
      "accessHours": {
        "start": "06:00",
        "end": "22:00",
        "days": [1, 2, 3, 4, 5, 6, 7]
      }
    },
    {
      "id": 2,
      "name": "Premium",
      "description": "Acceso completo + clases grupales",
      "price": 1200.00,
      "durationMonths": 1,
      "benefits": [
        "Todo lo de Básica",
        "Clases grupales ilimitadas",
        "Consulta nutricional mensual"
      ]
    }
  ]
}
```

### GET /memberships/my-membership
Obtener membresía actual del usuario

**Headers:** `Authorization: Bearer {token}`

**Response (200):**
```json
{
  "success": true,
  "data": {
    "id": 456,
    "type": {
      "id": 2,
      "name": "Premium",
      "price": 1200.00
    },
    "startDate": "2025-06-01",
    "endDate": "2025-07-01",
    "status": "active",
    "paymentStatus": "paid",
    "autoRenew": true,
    "daysRemaining": 22
  }
}
```

### POST /memberships/renew
Renovar membresía

**Headers:** `Authorization: Bearer {token}`

**Request Body:**
```json
{
  "membershipTypeId": 2,
  "paymentMethod": "card",
  "autoRenew": true
}
```

---

## 🚪 Control de Acceso

### POST /check-ins
Registrar check-in

**Headers:** `Authorization: Bearer {token}`

**Request Body:**
```json
{
  "location": "main_entrance"
}
```

**Response (201):**
```json
{
  "success": true,
  "data": {
    "id": 789,
    "checkInTime": "2025-06-09T18:30:00Z",
    "location": "main_entrance",
    "membershipValid": true,
    "welcomeMessage": "¡Bienvenida María! Que tengas un excelente entrenamiento."
  }
}
```

### PUT /check-ins/{id}/checkout
Registrar check-out

**Headers:** `Authorization: Bearer {token}`

**Response (200):**
```json
{
  "success": true,
  "data": {
    "id": 789,
    "checkInTime": "2025-06-09T18:30:00Z",
    "checkOutTime": "2025-06-09T20:15:00Z",
    "duration": "1 hora 45 minutos"
  }
}
```

### GET /check-ins/my-history
Obtener historial de check-ins del usuario

**Headers:** `Authorization: Bearer {token}`  
**Query Params:** `?page=1&limit=20&from=2025-06-01&to=2025-06-09`

### GET /gym/capacity
Obtener capacidad actual del gimnasio

**Response (200):**
```json
{
  "success": true,
  "data": {
    "currentCapacity": 45,
    "maxCapacity": 100,
    "occupancyPercentage": 45,
    "peakHours": ["18:00-20:00", "07:00-09:00"],
    "recommendedTime": "14:00-16:00"
  }
}
```

---

## 💪 Planes de Entrenamiento

### GET /workout-plans/my-plans
Obtener planes de entrenamiento del usuario

**Headers:** `Authorization: Bearer {token}`

**Response (200):**
```json
{
  "success": true,
  "data": [
    {
      "id": 101,
      "name": "Plan de Fuerza - Principiante",
      "description": "Enfoque en movimientos básicos",
      "trainer": {
        "id": 25,
        "name": "Carlos Rodríguez"
      },
      "goal": "muscle_gain",
      "difficulty": "beginner",
      "startDate": "2025-06-01",
      "endDate": "2025-07-31",
      "isActive": true,
      "progress": {
        "completedWorkouts": 8,
        "totalWorkouts": 24,
        "percentage": 33
      }
    }
  ]
}
```

### GET /workout-plans/{id}/today
Obtener rutina del día

**Headers:** `Authorization: Bearer {token}`

**Response (200):**
```json
{
  "success": true,
  "data": {
    "dayOfWeek": 2,
    "workoutName": "Tren Superior - Día A",
    "exercises": [
      {
        "id": 301,
        "name": "Press de Banca",
        "muscleGroups": ["chest", "triceps", "shoulders"],
        "sets": 3,
        "reps": 12,
        "weight": 50.0,
        "restTime": 90,
        "instructions": "Mantén la espalda en contacto con el banco...",
        "isCompleted": false
      },
      {
        "id": 302,
        "name": "Remo con Barra",
        "muscleGroups": ["back", "biceps"],
        "sets": 3,
        "reps": 10,
        "weight": 40.0,
        "restTime": 90,
        "isCompleted": false
      }
    ]
  }
}
```

### PUT /workout-plans/{planId}/exercises/{exerciseId}/complete
Marcar ejercicio como completado

**Headers:** `Authorization: Bearer {token}`

**Request Body:**
```json
{
  "setsCompleted": 3,
  "repsCompleted": [12, 11, 10],
  "weightsUsed": [50.0, 50.0, 45.0],
  "notes": "Último set con menos peso por fatiga"
}
```

### GET /exercises/search
Buscar ejercicios

**Query Params:** `?q=press&muscleGroup=chest&difficulty=beginner`

---

## 🏃‍♂️ Clases Grupales

### GET /classes
Obtener clases disponibles

**Query Params:** `?date=2025-06-10&category=yoga`

**Response (200):**
```json
{
  "success": true,
  "data": [
    {
      "id": 201,
      "name": "Yoga Matutino",
      "description": "Clase de yoga para todos los niveles",
      "instructor": {
        "id": 26,
        "name": "Ana Martínez",
        "profilePicture": "https://cdn.mygym.com/instructors/26.jpg"
      },
      "dateTime": "2025-06-10T07:00:00Z",
      "duration": 60,
      "maxCapacity": 20,
      "currentReservations": 15,
      "availableSpots": 5,
      "price": 0.00,
      "room": "Studio A",
      "status": "scheduled"
    }
  ]
}
```

### POST /classes/{id}/reserve
Reservar lugar en clase

**Headers:** `Authorization: Bearer {token}`

**Response (201):**
```json
{
  "success": true,
  "data": {
    "reservationId": 501,
    "class": {
      "id": 201,
      "name": "Yoga Matutino",
      "dateTime": "2025-06-10T07:00:00Z"
    },
    "status": "reserved",
    "confirmationCode": "YG-501-2025"
  }
}
```

### DELETE /classes/reservations/{id}
Cancelar reserva

**Headers:** `Authorization: Bearer {token}`

### GET /classes/my-reservations
Obtener mis reservas

**Headers:** `Authorization: Bearer {token}`

---

## 🛒 Productos y Ventas

### GET /products
Obtener catálogo de productos

**Query Params:** `?category=supplements&inStock=true`

**Response (200):**
```json
{
  "success": true,
  "data": [
    {
      "id": 701,
      "name": "Proteína Whey Chocolate",
      "description": "Proteína de suero de alta calidad",
      "price": 850.00,
      "category": "supplements",
      "brand": "NutriFit",
      "sku": "NF-WPC-CHOC-2K",
      "stockQuantity": 15,
      "imageUrl": "https://cdn.mygym.com/products/701.jpg",
      "isActive": true
    }
  ]
}
```

### POST /orders
Crear orden de compra

**Headers:** `Authorization: Bearer {token}`

**Request Body:**
```json
{
  "items": [
    {
      "productId": 701,
      "quantity": 1
    },
    {
      "productId": 702,
      "quantity": 2
    }
  ],
  "paymentMethod": "card",
  "notes": "Recoger en recepción"
}
```

### GET /orders/my-orders
Obtener mis órdenes

**Headers:** `Authorization: Bearer {token}`

---

## 📊 Reportes y Analytics (Admin)

### GET /admin/dashboard
Dashboard administrativo

**Headers:** `Authorization: Bearer {token}` (role: admin)

**Response (200):**
```json
{
  "success": true,
  "data": {
    "summary": {
      "totalMembers": 250,
      "activeMemberships": 230,
      "currentlyInGym": 45,
      "monthlyRevenue": 280000.00,
      "newMembersThisMonth": 15
    },
    "charts": {
      "dailyAttendance": [
        {"date": "2025-06-01", "count": 85},
        {"date": "2025-06-02", "count": 92}
      ],
      "membershipTypes": [
        {"type": "Básica", "count": 120},
        {"type": "Premium", "count": 90},
        {"type": "VIP", "count": 20}
      ]
    },
    "alerts": [
      {
        "type": "warning",
        "message": "5 membresías vencen esta semana",
        "actionUrl": "/admin/memberships?expiring=true"
      }
    ]
  }
}
```

### GET /admin/reports/attendance
Reporte de asistencia

**Headers:** `Authorization: Bearer {token}` (role: admin)  
**Query Params:** `?from=2025-06-01&to=2025-06-30&format=json`

### GET /admin/reports/revenue
Reporte de ingresos

**Headers:** `Authorization: Bearer {token}` (role: admin)  
**Query Params:** `?period=monthly&year=2025`

---

## 📱 Notificaciones

### GET /notifications
Obtener notificaciones del usuario

**Headers:** `Authorization: Bearer {token}`  
**Query Params:** `?unreadOnly=true&page=1&limit=10`

**Response (200):**
```json
{
  "success": true,
  "data": {
    "notifications": [
      {
        "id": 901,
        "title": "Tu membresía vence pronto",
        "message": "Tu membresía Premium vence el 1 de julio. ¡Renueva ahora!",
        "type": "membership",
        "priority": "high",
        "isRead": false,
        "actionUrl": "/memberships/renew",
        "createdAt": "2025-06-09T10:00:00Z"
      }
    ],
    "unreadCount": 3,
    "pagination": {
      "page": 1,
      "limit": 10,
      "total": 25
    }
  }
}
```

### PUT /notifications/{id}/read
Marcar notificación como leída

**Headers:** `Authorization: Bearer {token}`

### PUT /notifications/mark-all-read
Marcar todas como leídas

**Headers:** `Authorization: Bearer {token}`

---

## 🔧 Utilidades

### GET /gym/hours
Obtener horarios del gimnasio

**Response (200):**
```json
{
  "success": true,
  "data": {
    "regular": {
      "monday": {"open": "05:00", "close": "23:00"},
      "tuesday": {"open": "05:00", "close": "23:00"},
      "sunday": {"open": "07:00", "close": "21:00"}
    },
    "holidays": [
      {
        "date": "2025-12-25",
        "name": "Navidad",
        "hours": {"open": "08:00", "close": "14:00"}
      }
    ]
  }
}
```

### GET /health
Health check del API

**Response (200):**
```json
{
  "status": "healthy",
  "timestamp": "2025-06-09T22:30:00Z",
  "version": "1.0.0",
  "database": "connected"
}
```

---

## 📝 Códigos de Estado HTTP

| Código | Descripción |
|--------|-------------|
| 200 | OK - Solicitud exitosa |
| 201 | Created - Recurso creado exitosamente |
| 400 | Bad Request - Error en la solicitud |
| 401 | Unauthorized - No autenticado |
| 403 | Forbidden - Sin permisos |
| 404 | Not Found - Recurso no encontrado |
| 409 | Conflict - Conflicto (ej: email ya existe) |
| 422 | Unprocessable Entity - Error de validación |
| 429 | Too Many Requests - Rate limit excedido |
| 500 | Internal Server Error - Error del servidor |

## 🚨 Formato de Errores

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Los datos proporcionados no son válidos",
    "details": [
      {
        "field": "email",
        "message": "El email ya está registrado"
      },
      {
        "field": "password",
        "message": "La contraseña debe tener al menos 8 caracteres"
      }
    ]
  },
  "timestamp": "2025-06-09T22:30:00Z"
}
```

---

*Documento actualizado: 9 de junio de 2025*
