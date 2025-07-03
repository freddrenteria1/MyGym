# 🎨 Diseño UI/UX - MyGym

## 🎯 Principios de Diseño

### 1. **Simplicidad y Claridad**
- Interfaz limpia y minimalista
- Navegación intuitiva para todos los tipos de usuarios
- Información importante siempre visible

### 2. **Accesibilidad**
- Cumplimiento con WCAG 2.1 AA
- Contraste adecuado para legibilidad
- Navegación por teclado completa
- Textos alternativos para imágenes

### 3. **Responsive Design**
- Mobile-first approach
- Adaptable a tablets y desktop
- Touch-friendly en dispositivos móviles

### 4. **Consistencia**
- Sistema de diseño coherente
- Patrones de interacción consistentes
- Branding uniforme en toda la aplicación

---

## 🎨 Sistema de Diseño

### Paleta de Colores

#### Colores Primarios
```css
--primary-50: #f0f9ff;   /* Azul muy claro */
--primary-100: #e0f2fe;  /* Azul claro */
--primary-500: #0ea5e9;  /* Azul principal */
--primary-600: #0284c7;  /* Azul medio */
--primary-900: #0c4a6e;  /* Azul oscuro */
```

#### Colores Secundarios
```css
--secondary-50: #fefce8;  /* Amarillo muy claro */
--secondary-100: #fef3c7; /* Amarillo claro */
--secondary-500: #eab308; /* Amarillo principal */
--secondary-600: #ca8a04; /* Amarillo medio */
--secondary-900: #713f12; /* Amarillo oscuro */
```

#### Colores de Estado
```css
--success: #10b981;   /* Verde éxito */
--warning: #f59e0b;   /* Naranja advertencia */
--error: #ef4444;     /* Rojo error */
--info: #3b82f6;      /* Azul información */
```

#### Colores Neutros
```css
--gray-50: #f9fafb;
--gray-100: #f3f4f6;
--gray-200: #e5e7eb;
--gray-300: #d1d5db;
--gray-400: #9ca3af;
--gray-500: #6b7280;
--gray-600: #4b5563;
--gray-700: #374151;
--gray-800: #1f2937;
--gray-900: #111827;
```

### Tipografía

#### Fuentes
- **Principal**: Inter (Google Fonts)
- **Secundaria**: Roboto (para datos numéricos)
- **Monospace**: Fira Code (para código/IDs)

#### Escalas
```css
--text-xs: 0.75rem;    /* 12px */
--text-sm: 0.875rem;   /* 14px */
--text-base: 1rem;     /* 16px */
--text-lg: 1.125rem;   /* 18px */
--text-xl: 1.25rem;    /* 20px */
--text-2xl: 1.5rem;    /* 24px */
--text-3xl: 1.875rem;  /* 30px */
--text-4xl: 2.25rem;   /* 36px */
```

### Espaciado
```css
--spacing-1: 0.25rem;  /* 4px */
--spacing-2: 0.5rem;   /* 8px */
--spacing-3: 0.75rem;  /* 12px */
--spacing-4: 1rem;     /* 16px */
--spacing-5: 1.25rem;  /* 20px */
--spacing-6: 1.5rem;   /* 24px */
--spacing-8: 2rem;     /* 32px */
--spacing-10: 2.5rem;  /* 40px */
--spacing-12: 3rem;    /* 48px */
```

### Sombras
```css
--shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
--shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1);
--shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1);
--shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1);
```

---

## 📱 Wireframes y Layouts

### 1. Dashboard Principal (Miembro)

```
┌─────────────────────────────────────┐
│ [☰] MyGym              [🔔] [👤]   │
├─────────────────────────────────────┤
│                                     │
│ ¡Hola María! 👋                     │
│ Tu membresía vence en 22 días       │
│                                     │
│ ┌─────────────┐ ┌─────────────┐    │
│ │ CHECK-IN    │ │ MI RUTINA   │    │
│ │ ┌─────────┐ │ │ Tren Superior│   │
│ │ │ [📍]    │ │ │ 5 ejercicios │    │
│ │ │ TAP     │ │ │ [▶️ Empezar]│    │
│ │ └─────────┘ │ └─────────────┘    │
│ └─────────────┘                    │
│                                     │
│ 📊 PROGRESO SEMANAL                │
│ ████████░░ 80% (4/5 entrenamientos) │
│                                     │
│ 🏃‍♂️ PRÓXIMAS CLASES                │
│ • Yoga - Mañana 7:00 AM            │
│ • Spinning - Miércoles 6:00 PM     │
│                                     │
│ 💪 CAPACIDAD DEL GYM               │
│ ████████████░░░░░░ 60% (45/75)     │
│                                     │
└─────────────────────────────────────┘
```

### 2. Pantalla de Check-in

```
┌─────────────────────────────────────┐
│ [←] Check-in                        │
├─────────────────────────────────────┤
│                                     │
│         ┌─────────────┐             │
│         │    [QR]     │             │
│         │  Scanner    │             │
│         │             │             │
│         └─────────────┘             │
│                                     │
│      Escanea tu código QR           │
│         o toca el botón             │
│                                     │
│      ┌─────────────────┐            │
│      │  📍 CHECK-IN    │            │
│      │    MANUAL       │            │
│      └─────────────────┘            │
│                                     │
│ ℹ️  Capacidad actual: 45/75 (60%)   │
│                                     │
│ 🕐 Horario: 06:00 - 23:00          │
│                                     │
└─────────────────────────────────────┘
```

### 3. Plan de Entrenamiento

```
┌─────────────────────────────────────┐
│ [←] Plan de Fuerza - Día 2         │
├─────────────────────────────────────┤
│                                     │
│ 💪 TREN SUPERIOR - DÍA A            │
│ Entrenador: Carlos Rodríguez        │
│                                     │
│ ┌─────────────────────────────────┐ │
│ │ ✅ Press de Banca               │ │
│ │    3 series x 12 reps           │ │
│ │    Peso: 50kg | Descanso: 90s   │ │
│ │    [Ver técnica] [Completado]   │ │
│ └─────────────────────────────────┘ │
│                                     │
│ ┌─────────────────────────────────┐ │
│ │ ⏳ Remo con Barra              │ │
│ │    3 series x 10 reps           │ │
│ │    Peso: 40kg | Descanso: 90s   │ │
│ │    [Ver técnica] [Empezar]      │ │
│ └─────────────────────────────────┘ │
│                                     │
│ ⏱️ Tiempo transcurrido: 25 min      │
│ 📊 Progreso: 2/6 ejercicios        │
│                                     │
└─────────────────────────────────────┘
```

### 4. Clases Grupales

```
┌─────────────────────────────────────┐
│ [←] Clases Grupales    [📅] [🔍]   │
├─────────────────────────────────────┤
│                                     │
│ HOY - Lunes 9 de Junio             │
│                                     │
│ ┌─────────────────────────────────┐ │
│ │ 🧘 Yoga Matutino                │ │
│ │ 7:00 - 8:00 AM | Studio A       │ │
│ │ Instructor: Ana Martínez         │ │
│ │ 👥 15/20 participantes          │ │
│ │ [RESERVAR] 🟢 5 lugares         │ │
│ └─────────────────────────────────┘ │
│                                     │
│ ┌─────────────────────────────────┐ │
│ │ 🚴 Spinning Intenso             │ │
│ │ 6:00 - 7:00 PM | Studio B       │ │
│ │ Instructor: Luis García          │ │
│ │ 👥 20/20 participantes          │ │
│ │ [LISTA ESPERA] 🔴 Lleno         │ │
│ └─────────────────────────────────┘ │
│                                     │
│ MIS RESERVAS                        │
│ • Yoga - Mañana 7:00 AM ✅         │
│                                     │
└─────────────────────────────────────┘
```

---

## 📋 Componentes UI

### 1. Botones (PrimeNG + Tailwind)

#### Botón Primario
```typescript
@Component({
  selector: 'app-primary-button',
  standalone: true,
  imports: [ButtonModule],
  template: `
    <p-button 
      [label]="label"
      [loading]="loading"
      [disabled]="disabled"
      styleClass="bg-primary-500 hover:bg-primary-600 border-primary-500 px-6 py-3 text-white font-medium rounded-lg transition-colors"
      (onClick)="handleClick()"
    />
  `
})
export class PrimaryButtonComponent {
  @Input() label = '';
  @Input() loading = false;
  @Input() disabled = false;
  @Output() onClick = new EventEmitter<void>();
  
  handleClick() {
    this.onClick.emit();
  }
}
```

#### Botón Secundario
```typescript
<p-button 
  label="Ver Historial"
  severity="secondary"
  styleClass="border-primary-500 text-primary-500 hover:bg-primary-50 px-4 py-2 rounded-md"
/>
```

### 2. Cards (PrimeNG Panel + Tailwind)

#### Card de Información
```typescript
@Component({
  selector: 'app-info-card',
  standalone: true,
  imports: [PanelModule, ButtonModule, CommonModule],
  template: `
    <p-panel styleClass="bg-white rounded-lg shadow-md border-0">
      <ng-template pTemplate="header">
        <div class="flex items-center gap-2">
          <span class="text-2xl">{{ icon }}</span>
          <h3 class="text-lg font-semibold text-gray-800">{{ title }}</h3>
        </div>
      </ng-template>
      
      <div class="p-4">
        <p class="text-gray-600 mb-4">{{ description }}</p>
        <p-button 
          [label]="buttonLabel"
          styleClass="bg-primary-500 hover:bg-primary-600 text-white px-4 py-2 rounded"
          (onClick)="onAction()"
        />
      </div>
    </p-panel>
  `
})
export class InfoCardComponent {
  @Input() icon = '';
  @Input() title = '';
  @Input() description = '';
  @Input() buttonLabel = '';
  @Output() action = new EventEmitter<void>();
  
  onAction() {
    this.action.emit();
  }
}
```

#### Card de Estadística
```typescript
@Component({
  selector: 'app-stat-card',
  standalone: true,
  imports: [CardModule, CommonModule],
  template: `
    <p-card styleClass="bg-gradient-to-r from-primary-500 to-primary-600 text-white rounded-lg shadow-lg">
      <div class="text-center">
        <h3 class="text-sm font-medium opacity-90">{{ title }}</h3>
        <div class="text-3xl font-bold mt-2">{{ value }}</div>
        @if (change) {
          <div class="text-sm mt-1 opacity-75 flex items-center justify-center gap-1">
            @if (trend === 'up') {
              <i class="pi pi-arrow-up"></i>
            } @else {
              <i class="pi pi-arrow-down"></i>
            }
            {{ change }}
          </div>
        }
      </div>
    </p-card>
  `
})
export class StatCardComponent {
  @Input() title = '';
  @Input() value = '';
  @Input() change = '';
  @Input() trend: 'up' | 'down' = 'up';
}
```

### 3. Formularios (Reactive Forms + PrimeNG)

#### Input Field
```typescript
@Component({
  selector: 'app-form-field',
  standalone: true,
  imports: [InputTextModule, CommonModule, ReactiveFormsModule],
  template: `
    <div class="field mb-4">
      <label [for]="fieldId" class="block text-sm font-medium text-gray-700 mb-2">
        {{ label }}
        @if (required) {
          <span class="text-red-500">*</span>
        }
      </label>
      
      <input 
        pInputText 
        [id]="fieldId"
        [formControl]="control"
        [placeholder]="placeholder"
        [type]="type"
        class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
        [class.border-red-500]="control.invalid && control.touched"
      />
      
      @if (control.invalid && control.touched) {
        <small class="text-red-500 mt-1 block">
          {{ getErrorMessage() }}
        </small>
      }
    </div>
  `
})
export class FormFieldComponent {
  @Input() label = '';
  @Input() placeholder = '';
  @Input() type = 'text';
  @Input() required = false;
  @Input() control!: FormControl;
  
  fieldId = `field-${Math.random().toString(36).substr(2, 9)}`;
  
  getErrorMessage(): string {
    if (this.control.errors?.['required']) return `${this.label} es obligatorio`;
    if (this.control.errors?.['email']) return 'Email inválido';
    if (this.control.errors?.['minlength']) return `Mínimo ${this.control.errors?.['minlength'].requiredLength} caracteres`;
    return 'Campo inválido';
  }
}
```

#### Dropdown/Select
```typescript
@Component({
  selector: 'app-select-field',
  standalone: true,
  imports: [DropdownModule, CommonModule, ReactiveFormsModule],
  template: `
    <div class="field mb-4">
      <label [for]="fieldId" class="block text-sm font-medium text-gray-700 mb-2">
        {{ label }}
      </label>
      
      <p-dropdown 
        [id]="fieldId"
        [formControl]="control"
        [options]="options"
        [placeholder]="placeholder"
        optionLabel="label"
        optionValue="value"
        styleClass="w-full"
        [class.border-red-500]="control.invalid && control.touched"
      />
      
      @if (control.invalid && control.touched) {
        <small class="text-red-500 mt-1 block">
          {{ label }} es obligatorio
        </small>
      }
    </div>
  `
})
export class SelectFieldComponent {
  @Input() label = '';
  @Input() placeholder = 'Seleccionar...';
  @Input() options: any[] = [];
  @Input() control!: FormControl;
  
  fieldId = `select-${Math.random().toString(36).substr(2, 9)}`;
}
```

### 4. Navegación

#### Sidebar Navigation
```typescript
@Component({
  selector: 'app-sidebar',
  standalone: true,
  imports: [MenuModule, RouterModule, CommonModule],
  template: `
    <div class="w-64 bg-white shadow-lg h-full">
      <div class="p-4 border-b">
        <h2 class="text-xl font-bold text-gray-800">MyGym</h2>
      </div>
      
      <p-menu 
        [model]="menuItems"
        styleClass="w-full border-0"
      />
    </div>
  `
})
export class SidebarComponent implements OnInit {
  menuItems: MenuItem[] = [];
  
  ngOnInit() {
    this.menuItems = [
      {
        label: 'Dashboard',
        icon: 'pi pi-home',
        routerLink: '/dashboard',
        styleClass: 'p-3 hover:bg-gray-50'
      },
      {
        label: 'Entrenamientos',
        icon: 'pi pi-bolt',
        routerLink: '/workouts',
        styleClass: 'p-3 hover:bg-gray-50'
      },
      {
        label: 'Clases',
        icon: 'pi pi-users',
        routerLink: '/classes',
        styleClass: 'p-3 hover:bg-gray-50'
      },
      {
        label: 'Perfil',
        icon: 'pi pi-user',
        routerLink: '/profile',
        styleClass: 'p-3 hover:bg-gray-50'
      }
    ];
  }
}
```

### 5. Modals y Dialogs (PrimeNG Dialog)

#### Modal de Confirmación
```typescript
@Component({
  selector: 'app-confirm-dialog',
  standalone: true,
  imports: [DialogModule, ButtonModule],
  template: `
    <p-dialog 
      [visible]="visible"
      [modal]="true"
      [closable]="false"
      [draggable]="false"
      styleClass="w-96"
      (onHide)="onCancel()"
    >
      <ng-template pTemplate="header">
        <h3 class="text-lg font-semibold">{{ title }}</h3>
      </ng-template>
      
      <div class="py-4">
        <p class="text-gray-600">{{ message }}</p>
      </div>
      
      <ng-template pTemplate="footer">
        <div class="flex gap-2 justify-end">
          <p-button 
            label="Cancelar"
            severity="secondary"
            (onClick)="onCancel()"
            styleClass="px-4 py-2"
          />
          <p-button 
            [label]="confirmLabel"
            severity="danger"
            (onClick)="onConfirm()"
            styleClass="px-4 py-2"
          />
        </div>
      </ng-template>
    </p-dialog>
  `
})
export class ConfirmDialogComponent {
  @Input() visible = false;
  @Input() title = 'Confirmar';
  @Input() message = '¿Estás seguro?';
  @Input() confirmLabel = 'Confirmar';
  
  @Output() confirm = new EventEmitter<void>();
  @Output() cancel = new EventEmitter<void>();
  
  onConfirm() {
    this.confirm.emit();
  }
  
  onCancel() {
    this.cancel.emit();
  }
}
```

---

## 📱 Responsive Breakpoints

```css
/* Mobile First */
@media (min-width: 640px) { /* sm */ }
@media (min-width: 768px) { /* md */ }
@media (min-width: 1024px) { /* lg */ }
@media (min-width: 1280px) { /* xl */ }
@media (min-width: 1536px) { /* 2xl */ }
```

### Layout por Dispositivo

#### Mobile (< 768px)
- Bottom navigation
- Single column layout
- Touch-optimized buttons (min 44px)
- Swipe gestures para carruseles

#### Tablet (768px - 1024px)
- Sidebar colapsable
- Grid de 2-3 columnas
- Navegación híbrida

#### Desktop (> 1024px)
- Sidebar fija
- Grid multi-columna
- Hover states
- Keyboard shortcuts

---

## 🎭 Estados de Interacción

### Loading States
```jsx
<Card loading>
  <Skeleton height="200px" />
</Card>
```

### Empty States
```jsx
<EmptyState
  icon="📊"
  title="No hay entrenamientos"
  description="Agenda tu primer entrenamiento"
  action={<Button>Empezar ahora</Button>}
/>
```

### Error States
```jsx
<ErrorState
  icon="⚠️"
  title="Error de conexión"
  description="No se pudo cargar la información"
  action={<Button onClick={retry}>Reintentar</Button>}
/>
```

---

## 🎨 Integración Tailwind CSS + PrimeNG

### Configuración de Tailwind para PrimeNG

#### tailwind.config.js
```javascript
module.exports = {
  content: [
    "./src/**/*.{html,ts}",
  ],
  theme: {
    extend: {
      colors: {
        primary: {
          50: '#f0f9ff',
          100: '#e0f2fe',
          500: '#0ea5e9',
          600: '#0284c7',
          900: '#0c4a6e',
        },
        secondary: {
          50: '#fefce8',
          500: '#eab308',
          600: '#ca8a04',
        }
      },
      fontFamily: {
        sans: ['Inter', 'sans-serif'],
      }
    },
  },
  plugins: [],
}
```

#### Global Styles (styles/globals.css)
```css
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';

/* PrimeNG Theme Overrides */
:root {
  --primary-color: #0ea5e9;
  --primary-color-text: #ffffff;
  --surface-0: #ffffff;
  --surface-50: #f9fafb;
  --surface-100: #f3f4f6;
  --text-color: #374151;
  --text-color-secondary: #6b7280;
}

/* Custom PrimeNG component styles */
.p-button.p-button-primary {
  @apply bg-primary-500 border-primary-500 hover:bg-primary-600 hover:border-primary-600;
}

.p-inputtext {
  @apply border-gray-300 focus:border-primary-500 focus:ring-2 focus:ring-primary-500 focus:ring-opacity-20;
}

.p-card {
  @apply shadow-md border-0 rounded-lg;
}

.p-panel .p-panel-header {
  @apply bg-gray-50 border-gray-200;
}
```

### Responsive Design con Angular

#### Responsive Service
```typescript
@Injectable({
  providedIn: 'root'
})
export class ResponsiveService {
  private breakpointObserver = inject(BreakpointObserver);
  
  // Signals para responsive design
  isMobile = signal(false);
  isTablet = signal(false);
  isDesktop = signal(false);
  
  constructor() {
    // Mobile
    this.breakpointObserver.observe(['(max-width: 767px)'])
      .subscribe(result => this.isMobile.set(result.matches));
    
    // Tablet  
    this.breakpointObserver.observe(['(min-width: 768px) and (max-width: 1023px)'])
      .subscribe(result => this.isTablet.set(result.matches));
      
    // Desktop
    this.breakpointObserver.observe(['(min-width: 1024px)'])
      .subscribe(result => this.isDesktop.set(result.matches));
  }
}

// Uso en componentes
@Component({
  selector: 'app-dashboard',
  standalone: true,
  template: `
    <div [class]="containerClass()">
      @if (responsive.isMobile()) {
        <!-- Mobile layout -->
        <app-mobile-nav />
      } @else {
        <!-- Desktop layout -->
        <app-sidebar />
      }
      
      <main [class]="mainClass()">
        <router-outlet />
      </main>
    </div>
  `
})
export class DashboardComponent {
  responsive = inject(ResponsiveService);
  
  containerClass = computed(() => 
    this.responsive.isMobile() 
      ? 'flex flex-col h-screen' 
      : 'flex h-screen'
  );
  
  mainClass = computed(() =>
    this.responsive.isMobile()
      ? 'flex-1 overflow-auto p-4'
      : 'flex-1 overflow-auto p-6 ml-64'
  );
}
```

---

## ♿ Accesibilidad

### Focus Management
```jsx
<Button 
  className="focus:ring-2 focus:ring-primary-500 focus:outline-none"
  aria-label="Iniciar entrenamiento"
>
  Empezar
</Button>
```

### ARIA Labels
```jsx
<div role="progressbar" aria-valuenow={75} aria-valuemax={100}>
  <div className="w-3/4 bg-primary-500 h-2 rounded" />
</div>
```

### Color Contrast
- Mínimo 4.5:1 para texto normal
- Mínimo 3:1 para texto grande
- No usar solo color para transmitir información

### Keyboard Navigation
- Tab order lógico
- Skip links para navegación rápida
- Shortcuts para acciones frecuentes

---

## 🎨 Herramientas de Desarrollo

### Design System Tools
- **Storybook**: Para documentar componentes
- **Figma**: Para diseños y prototipos
- **Tailwind CSS**: Para styling consistente

### Testing Visual
- **Chromatic**: Para testing visual automático
- **Percy**: Para regression testing
- **Accessibility Tree**: Para testing de accesibilidad

---

*Documento actualizado: 9 de junio de 2025*
