# 🗄️ Diseño de Base de Datos - MyGym

## 📊 Diagrama de Entidades (ERD)

```
┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│     Users       │       │   Memberships   │       │ MembershipTypes │
├─────────────────┤       ├─────────────────┤       ├─────────────────┤
│ id (PK)         │◄──────┤ id (PK)         │──────►│ id (PK)         │
│ email           │       │ user_id (FK)    │       │ name            │
│ password_hash   │       │ type_id (FK)    │       │ description     │
│ first_name      │       │ start_date      │       │ price           │
│ last_name       │       │ end_date        │       │ duration_months │
│ phone           │       │ status          │       │ benefits        │
│ date_of_birth   │       │ created_at      │       │ access_hours    │
│ role            │       │ updated_at      │       │ created_at      │
│ profile_picture │       └─────────────────┘       │ updated_at      │
│ created_at      │                                 └─────────────────┘
│ updated_at      │
└─────────────────┘

┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│   CheckIns      │       │   Equipment     │       │ WorkoutPlans    │
├─────────────────┤       ├─────────────────┤       ├─────────────────┤
│ id (PK)         │       │ id (PK)         │       │ id (PK)         │
│ user_id (FK)    │       │ name            │       │ user_id (FK)    │
│ check_in_time   │       │ category        │       │ trainer_id (FK) │
│ check_out_time  │       │ brand           │       │ name            │
│ created_at      │       │ status          │       │ description     │
└─────────────────┘       │ last_maintenance│       │ start_date      │
                          │ location        │       │ end_date        │
                          │ created_at      │       │ created_at      │
                          │ updated_at      │       │ updated_at      │
                          └─────────────────┘       └─────────────────┘

┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│   Exercises     │       │  WorkoutSets    │       │ GroupClasses    │
├─────────────────┤       ├─────────────────┤       ├─────────────────┤
│ id (PK)         │◄──────┤ id (PK)         │       │ id (PK)         │
│ name            │       │ plan_id (FK)    │       │ name            │
│ description     │       │ exercise_id (FK)│       │ description     │
│ muscle_groups   │       │ sets            │       │ instructor_id   │
│ equipment_needed│       │ reps            │       │ max_capacity    │
│ difficulty      │       │ weight          │       │ date_time       │
│ instructions    │       │ rest_time       │       │ duration        │
│ created_at      │       │ notes           │       │ status          │
│ updated_at      │       │ completed_at    │       │ created_at      │
└─────────────────┘       │ created_at      │       │ updated_at      │
                          └─────────────────┘       └─────────────────┘

┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│ClassReservations│       │    Products     │       │     Orders      │
├─────────────────┤       ├─────────────────┤       ├─────────────────┤
│ id (PK)         │       │ id (PK)         │       │ id (PK)         │
│ user_id (FK)    │       │ name            │       │ user_id (FK)    │
│ class_id (FK)   │       │ description     │       │ total_amount    │
│ reservation_date│       │ price           │       │ status          │
│ status          │       │ category        │       │ order_date      │
│ created_at      │       │ stock_quantity  │       │ created_at      │
└─────────────────┘       │ is_active       │       │ updated_at      │
                          │ created_at      │       └─────────────────┘
                          │ updated_at      │
                          └─────────────────┘

┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│   OrderItems    │       │    Payments     │       │  Notifications  │
├─────────────────┤       ├─────────────────┤       ├─────────────────┤
│ id (PK)         │       │ id (PK)         │       │ id (PK)         │
│ order_id (FK)   │       │ user_id (FK)    │       │ user_id (FK)    │
│ product_id (FK) │       │ amount          │       │ title           │
│ quantity        │       │ payment_method  │       │ message         │
│ unit_price      │       │ transaction_id  │       │ type            │
│ total_price     │       │ status          │       │ is_read         │
│ created_at      │       │ payment_date    │       │ created_at      │
└─────────────────┘       │ created_at      │       └─────────────────┘
                          └─────────────────┘
```

## 📋 Definición de Tablas

### 1. **Users** - Usuarios del Sistema
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    phone VARCHAR(20),
    date_of_birth DATE,
    role VARCHAR(20) DEFAULT 'member' CHECK (role IN ('admin', 'staff', 'trainer', 'member')),
    profile_picture VARCHAR(500),
    emergency_contact JSONB,
    medical_info JSONB,
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 2. **MembershipTypes** - Tipos de Membresía
```sql
CREATE TABLE membership_types (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    price DECIMAL(10,2) NOT NULL,
    duration_months INTEGER NOT NULL,
    benefits JSONB,
    access_hours JSONB, -- {"start": "05:00", "end": "23:00", "days": [1,2,3,4,5,6,7]}
    max_classes_per_month INTEGER,
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 3. **Memberships** - Membresías Activas
```sql
CREATE TABLE memberships (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    type_id INTEGER REFERENCES membership_types(id),
    start_date DATE NOT NULL,
    end_date DATE NOT NULL,
    status VARCHAR(20) DEFAULT 'active' CHECK (status IN ('active', 'expired', 'suspended', 'cancelled')),
    payment_status VARCHAR(20) DEFAULT 'pending' CHECK (payment_status IN ('pending', 'paid', 'overdue')),
    auto_renew BOOLEAN DEFAULT false,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 4. **CheckIns** - Control de Acceso
```sql
CREATE TABLE check_ins (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    check_in_time TIMESTAMP NOT NULL,
    check_out_time TIMESTAMP,
    location VARCHAR(100) DEFAULT 'main_entrance',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 5. **Equipment** - Equipos del Gimnasio
```sql
CREATE TABLE equipment (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    category VARCHAR(50) NOT NULL, -- 'cardio', 'strength', 'free_weights', etc.
    brand VARCHAR(50),
    model VARCHAR(50),
    serial_number VARCHAR(100),
    status VARCHAR(20) DEFAULT 'available' CHECK (status IN ('available', 'in_use', 'maintenance', 'out_of_service')),
    location VARCHAR(100),
    purchase_date DATE,
    last_maintenance DATE,
    next_maintenance DATE,
    maintenance_notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 6. **Exercises** - Catálogo de Ejercicios
```sql
CREATE TABLE exercises (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    muscle_groups JSONB, -- ["chest", "triceps", "shoulders"]
    equipment_needed JSONB, -- ["barbell", "bench"]
    difficulty VARCHAR(20) CHECK (difficulty IN ('beginner', 'intermediate', 'advanced')),
    instructions TEXT,
    video_url VARCHAR(500),
    image_url VARCHAR(500),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 7. **WorkoutPlans** - Planes de Entrenamiento
```sql
CREATE TABLE workout_plans (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    trainer_id INTEGER REFERENCES users(id),
    name VARCHAR(100) NOT NULL,
    description TEXT,
    goal VARCHAR(50), -- 'weight_loss', 'muscle_gain', 'endurance', etc.
    difficulty VARCHAR(20) CHECK (difficulty IN ('beginner', 'intermediate', 'advanced')),
    duration_weeks INTEGER,
    start_date DATE,
    end_date DATE,
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 8. **WorkoutSets** - Sets de Ejercicios en Planes
```sql
CREATE TABLE workout_sets (
    id SERIAL PRIMARY KEY,
    plan_id INTEGER REFERENCES workout_plans(id) ON DELETE CASCADE,
    exercise_id INTEGER REFERENCES exercises(id),
    day_of_week INTEGER CHECK (day_of_week BETWEEN 1 AND 7),
    order_in_workout INTEGER,
    sets INTEGER NOT NULL,
    reps INTEGER,
    weight DECIMAL(5,2),
    duration_seconds INTEGER, -- para ejercicios de tiempo
    rest_time_seconds INTEGER,
    notes TEXT,
    is_completed BOOLEAN DEFAULT false,
    completed_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 9. **GroupClasses** - Clases Grupales
```sql
CREATE TABLE group_classes (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    instructor_id INTEGER REFERENCES users(id),
    max_capacity INTEGER NOT NULL,
    date_time TIMESTAMP NOT NULL,
    duration_minutes INTEGER NOT NULL,
    price DECIMAL(8,2) DEFAULT 0.00,
    status VARCHAR(20) DEFAULT 'scheduled' CHECK (status IN ('scheduled', 'in_progress', 'completed', 'cancelled')),
    room VARCHAR(50),
    equipment_needed JSONB,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 10. **ClassReservations** - Reservas de Clases
```sql
CREATE TABLE class_reservations (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    class_id INTEGER REFERENCES group_classes(id) ON DELETE CASCADE,
    reservation_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(20) DEFAULT 'reserved' CHECK (status IN ('reserved', 'attended', 'no_show', 'cancelled')),
    waitlist_position INTEGER, -- NULL si no está en lista de espera
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE(user_id, class_id)
);
```

### 11. **Products** - Productos para Venta
```sql
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    price DECIMAL(10,2) NOT NULL,
    category VARCHAR(50) NOT NULL, -- 'supplements', 'apparel', 'accessories', etc.
    brand VARCHAR(50),
    sku VARCHAR(50) UNIQUE,
    stock_quantity INTEGER DEFAULT 0,
    min_stock_level INTEGER DEFAULT 0,
    image_url VARCHAR(500),
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 12. **Orders** - Órdenes de Compra
```sql
CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    order_number VARCHAR(50) UNIQUE NOT NULL,
    total_amount DECIMAL(10,2) NOT NULL,
    status VARCHAR(20) DEFAULT 'pending' CHECK (status IN ('pending', 'paid', 'processing', 'completed', 'cancelled')),
    payment_method VARCHAR(50),
    order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 13. **OrderItems** - Items de Órdenes
```sql
CREATE TABLE order_items (
    id SERIAL PRIMARY KEY,
    order_id INTEGER REFERENCES orders(id) ON DELETE CASCADE,
    product_id INTEGER REFERENCES products(id),
    quantity INTEGER NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    total_price DECIMAL(10,2) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 14. **Payments** - Historial de Pagos
```sql
CREATE TABLE payments (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    order_id INTEGER REFERENCES orders(id),
    membership_id INTEGER REFERENCES memberships(id),
    amount DECIMAL(10,2) NOT NULL,
    payment_method VARCHAR(50) NOT NULL, -- 'cash', 'card', 'transfer', 'paypal', etc.
    transaction_id VARCHAR(100),
    status VARCHAR(20) DEFAULT 'pending' CHECK (status IN ('pending', 'completed', 'failed', 'refunded')),
    payment_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 15. **Notifications** - Sistema de Notificaciones
```sql
CREATE TABLE notifications (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    title VARCHAR(200) NOT NULL,
    message TEXT NOT NULL,
    type VARCHAR(50) NOT NULL, -- 'membership', 'class', 'payment', 'general', etc.
    priority VARCHAR(20) DEFAULT 'normal' CHECK (priority IN ('low', 'normal', 'high', 'urgent')),
    is_read BOOLEAN DEFAULT false,
    action_url VARCHAR(500), -- URL para acción relacionada
    scheduled_for TIMESTAMP, -- para notificaciones programadas
    sent_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## 📈 Índices Recomendados

```sql
-- Índices para mejores consultas
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_role ON users(role);
CREATE INDEX idx_memberships_user_id ON memberships(user_id);
CREATE INDEX idx_memberships_status ON memberships(status);
CREATE INDEX idx_checkins_user_id ON check_ins(user_id);
CREATE INDEX idx_checkins_datetime ON check_ins(check_in_time);
CREATE INDEX idx_class_reservations_user_id ON class_reservations(user_id);
CREATE INDEX idx_class_reservations_class_id ON class_reservations(class_id);
CREATE INDEX idx_notifications_user_id ON notifications(user_id);
CREATE INDEX idx_notifications_is_read ON notifications(is_read);
CREATE INDEX idx_orders_user_id ON orders(user_id);
CREATE INDEX idx_payments_user_id ON payments(user_id);
```

## 🔄 Triggers y Funciones

```sql
-- Función para actualizar updated_at automáticamente
CREATE OR REPLACE FUNCTION update_updated_at_column()
RETURNS TRIGGER AS $$
BEGIN
    NEW.updated_at = CURRENT_TIMESTAMP;
    RETURN NEW;
END;
$$ language 'plpgsql';

-- Aplicar trigger a todas las tablas que tengan updated_at
CREATE TRIGGER update_users_updated_at BEFORE UPDATE ON users 
    FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();
    
CREATE TRIGGER update_memberships_updated_at BEFORE UPDATE ON memberships 
    FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();
    
-- (Aplicar a todas las tablas relevantes...)
```

## 🎯 Consideraciones de Diseño

### Normalización
- **3NF (Tercera Forma Normal)**: Todas las tablas están normalizadas para evitar redundancia
- **JSONB**: Usado para datos semi-estructurados que pueden variar (beneficios, información médica)

### Escalabilidad
- **Particionamiento**: `check_ins` podría particionarse por fecha para mejor rendimiento
- **Archivado**: Implementar estrategia de archivado para datos históricos

### Seguridad
- **Soft Delete**: Considerar columna `deleted_at` para eliminación lógica
- **Auditoría**: Implementar tabla de auditoría para cambios críticos
- **Encriptación**: Datos sensibles médicos deben estar encriptados

### Integridad Referencial
- **Cascadas**: Configuradas apropiadamente para mantener integridad
- **Constraints**: Validaciones a nivel de base de datos

---

*Documento actualizado: 9 de junio de 2025*
