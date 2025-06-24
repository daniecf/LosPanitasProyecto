LosPanitas es una aplicación web diseñada para facilitar la gestión de ventas y el control de inventario en tiendas de bebidas alcohólicas. Está pensada para ofrecer una interfaz intuitiva tanto para el administrador del negocio como para los vendedores que vayan a usarla.

TECNOLOGIAS USADAS
Backend: Python con el framework FastAPI, ideal para construir APIs rápidas, modernas y eficientes.

Frontend: TypeScript con el framework React, brindando una interfaz de usuario dinámica y responsiva.

FUNCIONALIDADES PRINCIPALES
Registro y gestión de productos (bebidas).

Control de inventario en tiempo real.

Gestión de ventas y reportes de actividad.

Interfaz moderna para una experiencia fluida del usuario.

ESTRUCTURA DEL PROYECTO
Estructura del frontend:
Frontend/
├── package.json
├── package-lock.json
├── public/
│   └── vite.svg
├── src/
│   ├── App.tsx
│   ├── api/
│   │   └── axios.tsx
│   ├── assets/
│   ├── auth/
│   │   ├── AuthContext.tsx
│   │   └── UseAuth.tsx
│   ├── components/
│   │   ├── AlmacenModal.tsx
│   │   ├── InventarioModal.tsx
│   │   ├── ProductModal.tsx
│   │   ├── ProveedorAutocomplete.tsx
│   │   ├── ProveedorModal.tsx
│   │   ├── Sidebar.tsx
│   │   ├── TableComponent.tsx
│   │   ├── VentaModal.tsx
│   │   └── VentasChart.tsx
│   ├── index.css
│   ├── layout/
│   │   └── AppLayout.tsx
│   ├── main.tsx
│   ├── pages/
│   │   ├── AlmacenPage.tsx
│   │   ├── HomePage.tsx
│   │   ├── InventarioPage.tsx
│   │   ├── LoginPage.tsx
│   │   ├── ProductsPage.tsx
│   │   ├── ProveedoresPage.tsx
│   │   ├── RegisterPage.tsx
│   │   ├── ReportesPage.tsx
│   │   └── VentasPage.tsx
│   ├── routes/
│   │   └── ProtectedRoute.tsx
│   ├── styles/
│   │   ├── global.css
│   │   ├── home.css
│   │   ├── layout.css
│   │   ├── login.css
│   │   ├── modal.css
│   │   ├── register.css
│   │   ├── tabla-unificada.css
│   │   └── table.css
│   └── vite-env.d.ts
├── tsconfig.app.json
├── tsconfig.json
├── tsconfig.node.json
└── vite.config.ts

ARRANQUE DEL FRONTEND
main.tsx renderiza el componente principal <App /> dentro del DOM. Es el punto de entrada de la aplicación.

Configuración
vite.config.ts define la configuración de Vite, como aliases y plugins. tsconfig.json y relacionados configuran TypeScript. axios.tsx define la conexión al backend (URL base, headers, etc.).

Ruteo
App.tsx define las rutas usando React Router. Se separan rutas públicas (como login y registro) y rutas protegidas (productos, ventas, etc.). ProtectedRoute.tsx verifica que el usuario esté autenticado.

Autenticación
AuthContext.tsx define un contexto que guarda el usuario logueado y sus datos. UseAuth.tsx es un hook personalizado para acceder a ese contexto desde cualquier componente.

Componentes reutilizables
En components/ se encuentran modales, tablas, gráficos y elementos como la barra lateral. Se reutilizan en varias páginas del sistema.

Vistas o páginas
En pages/ están los componentes que representan cada pantalla del sistema: productos, ventas, inventario, reportes, etc. Cada uno está asociado a una ruta.

Estilos
En styles/ están los archivos CSS, organizados por secciones de la interfaz como login, tablas, layout, etc. Usan CSS puro.

Layout
AppLayout.tsx define la estructura visual común para las páginas protegidas: barra lateral, encabezado y espacio para el contenido dinámico.

cerveceria_backend/
│
├── .env                        # Variables de entorno (conexión DB, claves, etc.)
├── alembic.ini                # Configuración para migraciones de base de datos con Alembic
├── pyproject.toml             # Dependencias y configuración del proyecto (usando Poetry o similar)
├── requirements.txt           # Dependencias (para pip)
├── README.md                  # Documentación básica
├── estructura backend.txt     # Explicación en texto (lo leeré a continuación)
├── .gitignore, .flake8        # Configuración para git y linters
│
└── app/                       # Código fuente del backend
    ├── main.py                # Punto de entrada para FastAPI
    ├── config.py              # Configuración general (lectura del .env)
    └── interfaces/api/        # Capa de presentación (API)
        ├── routers/           # Rutas organizadas por funcionalidad
        │   ├── health.py      # Ruta para comprobar que el backend funciona
        │   └── products.py    # Rutas relacionadas con productos
        ├── schemas.py         # Pydantic: validaciones de entrada/salida
        ├── deps.py            # Dependencias comunes de FastAPI
        └── _init_.py

ARRANQUE DEL SERVIDOR

main.py crea la instancia de FastAPI, incluye las rutas (routers) y configura middlewares si hay.

Configuración

config.py carga variables desde .env (como la conexión a la base de datos).

alembic.ini y posibles carpetas relacionadas se usan para manejar versiones/migraciones del esquema SQL.

Rutas API

En interfaces/api/routers/, cada archivo define un conjunto de endpoints. Por ejemplo:

health.py típicamente sirve para GET /health que devuelve "OK" (para verificar si el backend está vivo).

products.py maneja operaciones CRUD sobre productos.

Esquemas (Schemas)

schemas.py define las estructuras que validan datos entrantes (inputs) y salientes (responses) usando pydantic.

Dependencias (deps.py)

Funciones comunes para inyección de dependencias: por ejemplo, autenticación, roles, obtener el usuario actual, etc.

AUTORES DEL PROYECTO
