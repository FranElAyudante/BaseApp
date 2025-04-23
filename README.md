# BaseApp

## 🧩 Tecnologías Utilizadas

- **Laravel 11** – Backend moderno y potente.
- **Vue 3** – Framework frontend progresivo.
- **Inertia.js** – Conexión entre Laravel y Vue sin necesidad de una SPA completa.
- **Laravel Breeze (Inertia + Vue)** – Autenticación y scaffolding rápido.
- **Vite** – Bundler moderno para desarrollo rápido.
- **PHP 8.3+, Node.js 18+, Composer, npm**

---

## 🔧 Requisitos Previos

Antes de empezar, asegúrate de tener instalados:

- PHP 8.3 o superior
- Composer
- Node.js y npm
- Base de datos (MySQL, PostgreSQL, etc.)
- Git
- Xamp

---

## Estructura del Proyecto

BaseApp/ 
├── app/ # Lógica backend de Laravel 
├── bootstrap/ 
├── config/ 
├── database/ 
├── public/ # Archivos públicos (JS, CSS, imágenes) 
├── resources/ 
│ ├── js/ # Código Vue 
│ │ └── Pages/ # Vistas conectadas con Inertia 
│ └── views/ # Blade files (opcional, poco usados con Inertia) 
├── routes/          
│ └── web.php 
├── tests/           
└── vite.config.js


---

## 🚀 Instalación Paso a Paso

1. **Crear proyecto Laravel con Breeze (Inertia + Vue)**

   ```bash
   composer create-project laravel/laravel:^11.0 BaseApp
   
Verificar si estás usando Laravel 11:
cd BaseApp
php artisan --version

Instalar Laravel Breeze:
composer require laravel/breeze --dev
php artisan breeze:install vue

Instalar dependencias y ejecutar el desarrollo:
npm install && npm run dev
php artisan migrate


Levantar el servidor:
php artisan serve
npm run dev
¡Listo! Ahora puedes comenzar a trabajar con tu proyecto.

Este `README.md` contiene todos los detalles organizados y listos para usarse.