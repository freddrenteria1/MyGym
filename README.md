# 🏋️‍♂️ MyGym - Sistema de Gestión para Gimnasio

## 📖 Descripción General
MyGym es una aplicación web moderna diseñada para gestionar de manera integral todas las operaciones de un gimnasio, desde la administración de miembros hasta el seguimiento de entrenamientos y facturación.

## 🎯 Objetivos del Proyecto
- Digitalizar la gestión completa del gimnasio
- Mejorar la experiencia del usuario (miembros y staff)
- Automatizar procesos administrativos
- Proporcionar análisis y reportes en tiempo real
- Crear una plataforma escalable y moderna

## 🚀 Funcionalidades Principales
- **Gestión de Miembros**: Registro, perfiles, membresías
- **Control de Acceso**: Check-in/out automático
- **Gestión de Entrenamientos**: Planes, rutinas, seguimiento
- **Facturación**: Pagos, membresías, productos
- **Inventario**: Equipos, mantenimiento, disponibilidad
- **Reportes**: Analytics, estadísticas, dashboards
- **Comunicación**: Notificaciones, mensajes, eventos

## 🛠️ Stack Tecnológico (Propuesto)
### Frontend
- **Framework**: Angular 18 con TypeScript
- **UI Library**: Tailwind CSS + PrimeNG
- **Estado**: RxJS + Services (Enfoque tradicional Angular)
- **Routing**: Angular Router con Guards
- **Arquitectura**: Standalone Components + Signals
- **Formularios**: Reactive Forms
- **Build**: Angular CLI + Vite

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js o Fastify
- **Base de Datos**: PostgreSQL
- **ORM**: Prisma o TypeORM
- **Autenticación**: JWT + bcrypt

### DevOps & Herramientas
- **Control de Versiones**: Git
- **Testing**: Playwright o Cypress (en evaluación)
- **Linting**: ESLint + Prettier
- **Unit Testing**: Jest + Angular Testing Library

## 📁 Estructura del Proyecto
```
MyGym/
├── docs/                   # Documentación del proyecto
├── frontend/              # Aplicación Angular 18
├── backend/               # API Node.js
├── database/              # Scripts y migraciones
├── shared/                # Tipos y utilidades compartidas
└── deployment/ -ll            # Configuración de despliegue
```

## 🏗️ Arquitectura
- **Patrón**: Arquitectura de 3 capas (Presentación, Lógica de Negocio, Datos)
- **API**: RESTful con autenticación JWT
- **Base de Datos**: Relacional con PostgreSQL
- **Frontend**: SPA (Single Page Application)

## 📚 Documentación
- [Requisitos Funcionales](docs/requirements.md)
- [Historias de Usuario](docs/user-stories.md)
- [Diseño de API](docs/api-design.md)
- [Esquema de Base de Datos](docs/database-schema.md)
- [Diseño de UI/UX](docs/ui-design.md)
- [Arquitectura del Sistema](docs/architecture.md)
- [Plan de Desarrollo](docs/development-plan.md)

## 🚦 Estado del Proyecto
**Fase Actual**: Planificación y Documentación
- ✅ Estructura de documentación
- ⏳ Definición de requisitos
- ⏳ Diseño de base de datos
- ⏳ Prototipado de UI
- ❌ Desarrollo backend
- ❌ Desarrollo frontend
- ❌ Testing
- ❌ Despliegue

## 👥 Equipo
- **Desarrollador Principal**: [Tu nombre]
- **Asistente IA**: GitHub Copilot

## 📄 Licencia
[Definir licencia]

---
*Última actualización: 9 de junio de 2025*
