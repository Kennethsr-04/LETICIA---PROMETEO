# LETICIA - Sistema de Gestión de Licitaciones

LETICIA es una aplicación web moderna diseñada para la gestión integral del proceso de licitaciones. Proporciona un entorno estructurado para el seguimiento, preparación, evaluación y administración de licitaciones, apoyado por un sistema de roles y un panel de administración.

## 🛠️ Stack Tecnológico

El proyecto está construido utilizando un ecosistema moderno de desarrollo web:

* **Frontend:** React + TypeScript
* **Build Tool:** Vite (`vite.config.ts`)
* **Enrutamiento:** Enrutamiento basado en archivos (`routeTree.gen.ts`, típico de TanStack Router).
* **Backend & Base de Datos:** Supabase (Autenticación, Base de datos en tiempo real y migraciones SQL).
* **Gestor de Paquetes y Runtime:** Bun (`bun.lock`, `bunfig.toml`).
* **UI & Estilos:** Sistema de componentes modulares (basado en la arquitectura de *shadcn/ui*, evidenciado por la carpeta `src/components/ui/` con componentes como diálogos, tablas, menús, etc.).

## 📦 Estructura de Módulos (Rutas)

La aplicación está dividida en varias áreas funcionales principales, protegidas bajo un layout autenticado (`_authenticated`):

### 1. Flujo Principal de Licitaciones
* **Recibidas (`/recibidas`):** Bandeja de entrada o listado de las nuevas licitaciones captadas.
* **Preparar (`/preparar`):** Módulo dedicado a la preparación de la documentación y estrategia de la licitación.
* **Evaluar (`/evaluar`):** Área para la evaluación técnica y económica de las licitaciones.
* **Licitadas (`/licitadas`):** Histórico y seguimiento de las licitaciones que ya han sido presentadas.

### 2. Panel de Control y Gestión
* **Bandeja:** Sistema de tareas y notificaciones para el usuario (`bandeja-page.tsx`), incluyendo herramientas de revisión rápida.
* **Indicadores (`/indicadores`):** Panel de métricas y análisis de datos del proceso de licitación.
* **Maestros (`/maestros`):** Gestión de tablas maestras y datos de referencia del sistema.

### 3. Administración (`/admin`)
* **Gestión de Usuarios (`/admin/usuarios`):** Administración de accesos y roles (conectado con `usuarios.functions.ts`).
* **Ingesta de Datos (`/admin/ingesta`):** Módulo para la importación y parseo de datos externos de licitaciones (apoyado por `parser.ts` e `ingesta.functions.ts`).

### 4. Autenticación
* Gestión de inicio de sesión (`/auth`), recuperación de contraseña (`/forgot-password`) y reseteo de claves (`/reset-password`), todo integrado directamente con el middleware de **Supabase**.

## 📂 Arquitectura del Proyecto

```text
LETICIA/
├── src/
│   ├── components/
│   │   ├── leticia/       # Componentes específicos de negocio (fichas, bandeja, sidebar, etc.)
│   │   └── ui/            # Componentes base de la interfaz (botones, tablas, modales, etc.)
│   ├── hooks/             # Hooks personalizados (ej. use-mobile)
│   ├── integrations/      # Conexiones con servicios externos
│   │   └── supabase/      # Cliente de Supabase, middleware y tipos
│   ├── lib/               # Lógica de negocio, funciones auxiliares y utilidades
│   │   └── leticia/       # Funciones core: ingesta, licitaciones, maestros, parser
│   └── routes/            # Páginas y vistas de la aplicación (enrutamiento por archivos)
├── supabase/
│   └── migrations/        # Archivos SQL con el esquema de la base de datos
├── .env                   # Variables de entorno
├── package.json           # Dependencias del proyecto
└── vite.config.ts         # Configuración del bundler
