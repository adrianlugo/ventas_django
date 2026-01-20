# 💼 Sistema de Gestión de Ventas - Django

Sistema profesional para gestión integral de productos, clientes y ventas con interfaz moderna, validación robusta y mensajes de usuario en tiempo real.

## 🎯 Características Principales

### ✨ Funcionalidades Core
- **CRUD completo** - Crear, leer, actualizar, eliminar productos, clientes y ventas
- **Dashboard interactivo** - Métricas de ventas en tiempo real con gráficos
- **Autenticación segura** - Sistema de usuarios con login/logout
- **Interfaz responsiva** - Funciona perfectamente en móvil, tablet y desktop

### 🎨 Características Avanzadas
- **Sistema de mensajes** - Feedback visual inmediato (éxito, error, advertencia)
- **Validación robusta**:
  - Previene productos duplicados
  - Evita sobreventa (validación de stock)
  - Valida correos electrónicos únicos
  - Valida precios y cantidades correctas
- **Interfaz profesional** - Estilos Bootstrap 5, iconos, animaciones suaves
- **Auto-dismiss** - Mensajes desaparecen automáticamente en 5 segundos

## � Por qué este proyecto es importante

Este proyecto demuestra **habilidades profesionales de desarrollo web completo**:

✅ **Arquitectura MVC** - Separación clara de responsabilidades (Models, Views, Forms, Templates)
✅ **Validación robusta** - Lógica de negocio protegida en múltiples niveles
✅ **Autenticación y seguridad** - Sistema de usuarios integrado, CSRF tokens, XSS prevention
✅ **Diseño responsivo** - Interfaz adaptable a cualquier dispositivo
✅ **Experiencia del usuario** - Feedback visual, mensajes claros, animaciones
✅ **Base de datos relacional** - Modelos con relaciones ForeignKey, integridad referencial
✅ **Buenas prácticas Django** - Estructura estándar, code conventions, decorators
✅ **Caso de uso real** - Sistema usado en negocios pequeños y medianos

**Aplicable a**: E-commerce, gestión de inventario, SaaS, sistemas administrativos, ERPs pequeños

## �🛠️ Stack Tecnológico

- **Backend**: Django 3.2+
- **Frontend**: HTML5, CSS3, Bootstrap 5.3
- **Base de datos**: SQLite (desarrollo)
- **Iconos**: Bootstrap Icons
- **JavaScript**: Vanilla JS (sin dependencias externas)
- **Python**: 3.8+

## 📋 Requisitos Previos

- Python 3.8+
- pip (gestor de paquetes)
- Navegador moderno

## 🚀 Instalación

### 1. Clonar o descargar el proyecto
```bash
cd proyecto_ventas
```

### 2. Crear entorno virtual
```bash
python -m venv venv
```

### 3. Activar entorno virtual
```bash
# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

### 4. Instalar dependencias
```bash
pip install -r requirements.txt
```

### 5. Ejecutar migraciones
```bash
python manage.py migrate
```

### 6. Crear usuario administrador
```bash
python manage.py createsuperuser
# Ingresa username, email y contraseña
```

### 7. Iniciar servidor
```bash
python manage.py runserver
```

### 8. Acceder a la aplicación
- **Aplicación**: http://localhost:8000
- **Admin**: http://localhost:8000/admin/

## 💡 Cómo Usar

### Primera vez
1. Inicia sesión con tus credenciales de superusuario
2. Ve a **Productos** y crea algunos productos de prueba
3. Ve a **Clientes** y agrega algunos clientes
4. Ve a **Ventas** y crea una venta

### Observa las características
- ✓ Los mensajes verdes confirman acciones exitosas
- ✓ Los mensajes rojos previenen errores
- ✓ Los mensajes desaparecen automáticamente
- ✓ Intenta crear un producto duplicado (verás error)
- ✓ Intenta vender más stock del disponible (verás error)

### Panel de Administración
- Accede a http://localhost:8000/admin/
- Gestiona usuarios, productos, clientes y ventas
- Visualiza datos directamente desde el ORM

## 📸 Capturas de Pantalla

Las capturas de las vistas principales están en la carpeta [`screenshots/`](./screenshots/):

- `dashboard_1.png`: Métricas principales del dashboard
- `dashboard_2.png`: Gráfico de barras y últimas ventas
- `login.png`: Pantalla de inicio de sesión
- `productos_lista.png`: Listado de productos
- `clientes_lista.png`: Listado de clientes
- `ventas_lista.png`: Listado de ventas

Puedes abrirlas directamente desde la carpeta para ver la interfaz real de la aplicación.

## 📁 Estructura del Proyecto

```
proyecto_ventas/
├── ventas/                 # Configuración principal
│   ├── settings.py        # Configuración Django
│   ├── urls.py            # URLs del proyecto
│   ├── wsgi.py            # WSGI para producción
│   └── asgi.py            # ASGI para async
├── ventas_app/            # Aplicación principal
│   ├── models.py          # Modelos: Producto, Cliente, Venta
│   ├── views.py           # Vistas con mensajes
│   ├── forms.py           # Formularios con validación
│   ├── urls.py            # URLs de la app
│   ├── admin.py           # Configuración admin
│   └── templates/         # Templates HTML
│       ├── base.html      # Template base con mensajes
│       ├── dashboard.html
│       ├── productos/
│       ├── clientes/
│       ├── ventas/
│       └── registration/
├── manage.py              # CLI de Django
├── requirements.txt       # Dependencias
└── db.sqlite3            # Base de datos (generada)
```

## 🔒 Validaciones Implementadas

El proyecto implementa **validación robusta en múltiples niveles**:

| Formulario | Validaciones |
|-----------|--------------|
| **Productos** | Nombre único, precio > 0, stock >= 0 |
| **Clientes** | Email único, formato email válido |
| **Ventas** | Stock disponible, cantidad > 0 |

✅ Validación HTML5 (frontend) + Django (backend) = **Seguro e inmediato**

## 🔐 Sistema de Roles y Permisos

El proyecto implementa **control de acceso basado en grupos**:

### Grupos Disponibles

| Grupo | Productos | Clientes | Ventas | Ver Dashboard |
|-------|-----------|----------|--------|---------------|
| **Admin** | C-R-U-D ✓ | C-R-U-D ✓ | C-R-D ✓ | ✓ |
| **Vendedor** | Solo R ✓ | C-R-U ✓ | C-R-D ✓ | ✓ |
| **Invitado** | Solo R ✓ | Solo R ✓ | Solo R ✓ | ✓ |

**Leyenda**: C = Crear, R = Leer, U = Actualizar, D = Eliminar

### Cómo Configurar Roles

1. Accede al admin: http://localhost:8000/admin/
2. Ve a **Autenticación y Autorización** → **Grupos**
3. Crea tres grupos: `Admin`, `Vendedor`, `Invitado`
4. Asigna usuarios a cada grupo
5. Los permisos se aplican **automáticamente**

### Cómo Funcionan los Permisos

```python
# El decorator @requiere_grupo() protege cada vista
@requiere_grupo('Admin')
def crear_producto(request):
    # Solo Admin puede crear productos
    ...

@requiere_grupo('Admin', 'Vendedor')
def crear_venta(request):
    # Admin y Vendedor pueden crear ventas
    ...
```

Si un usuario sin permisos intenta acceder, verá:
- 🚫 Mensaje: "No tienes permisos para acceder a esta acción"
- ⬅️ Redirige al dashboard automáticamente

## 🎨 Sistema de Mensajes

El sistema muestra **feedback visual inmediato**:

- **Verde ✓** - Operación exitosa
- **Rojo ✗** - Error o validación fallida
- **Amarillo ⚠** - Advertencia
- **Azul ℹ** - Información

Ejemplo:
```
✓ Producto "Laptop Dell" creado correctamente
✗ Error: el producto "Laptop" ya existe
✗ Solo hay 5 unidades disponibles de "Mouse"
```

## 📊 Modelos de Datos

### Producto
```python
- nombre (CharField, único)
- precio (DecimalField)
- stock (IntegerField)
```

### Cliente
```python
- nombre (CharField)
- correo (EmailField, único)
- telefono (CharField)
```

### Venta
```python
- producto (ForeignKey)
- cliente (ForeignKey)
- cantidad (IntegerField)
- total (DecimalField, calculado)
```

## 🔧 Configuración de Producción

Para desplegar a producción:

1. **Cambiar DEBUG a False** en settings.py
2. **Configurar SECRET_KEY** con valor seguro
3. **Usar base de datos PostgreSQL** en lugar de SQLite
4. **Configurar servidor WSGI** (Gunicorn)
5. **Usar servidor web** (Nginx)
6. **Habilitar HTTPS**
7. **Configurar variables de entorno**

```bash
# Ejemplo con variables de entorno
export DEBUG=False
export SECRET_KEY="tu-clave-secreta-aqui"
export DATABASE_URL="postgresql://..."
```

## 🐛 Solución de Problemas

**P: No veo los mensajes**
```
R: Recarga la página (F5)
   Verifica que el servidor está corriendo
```

**P: Los estilos no se aplican**
```
R: Limpia cache (Ctrl+Shift+Supr)
   Recarga la página
```

**P: Error "Module not found"**
```
R: pip install -r requirements.txt
```

**P: Error de base de datos**
```
R: python manage.py migrate
```

## 📈 Mejoras Futuras

- [ ] API REST con Django REST Framework
- [ ] Reportes avanzados en PDF
- [ ] Notificaciones por email
- [ ] Permisos granulares por objeto
- [ ] Tema oscuro/claro
- [ ] Búsqueda avanzada
- [ ] Paginación en listas
- [ ] Exportar datos a Excel/CSV

## 📄 Licencia

Este proyecto es de código abierto y está disponible bajo la licencia MIT.

## 👤 Autor

**Adrian Lugo**

- GitHub: [github.com/adrianlugo](https://github.com/adrianlugo)
- Email: adrianlugofrontela@gmail.com

## Lo que aprendí

- Cómo estructurar un proyecto Django profesional con CRUDs y autenticación.
- Uso de Bootstrap para crear interfaces responsivas y atractivas.
- Implementación de dashboards con métricas y gráficos usando Chart.js.
- Buenas prácticas en vistas, formularios y manejo de mensajes en Django.
- Cómo preparar un proyecto para portafolio y compartirlo online.

---

**Última actualización**: Enero 2026
**Versión**: 1.0
