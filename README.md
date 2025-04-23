# 🚀 BaseApp | Laravel 11 + Vue 3 + Inertia.js

![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white)
![Inertia.js](https://img.shields.io/badge/Inertia.js-000000?style=for-the-badge&logo=inertia&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)

Plantilla base para proyectos modernos con autenticación lista y arquitectura optimizada.

## ✨ Características Principales

- **Stack Moderno**: Laravel 11 + Vue 3 Composition API
- **Autenticación Instantánea**: Integrada con Laravel Breeze
- **Rendimiento**: Bundling con Vite para desarrollo ultrarrápido
- **Arquitectura Limpia**: Separación clara entre frontend y backend
- **Ready-to-Deploy**: Configuración optimizada para producción

## 🛠 Tecnologías Clave

| Backend           | Frontend          | Herramientas       |
|-------------------|-------------------|--------------------|
| Laravel 11        | Vue 3             | Vite               |
| Eloquent ORM      | Composition API   | Laravel Breeze     |
| Laravel Sanctum   | Pinia (Opcional)  | ESLint + Prettier  |
| MySQL/PostgreSQL  | Tailwind CSS      | Git Flow           |

## 📦 Requisitos del Sistema

```bash 
# Versiones mínimas requeridas
PHP 8.3+
Composer 2.5+
Node.js 18+
npm 9+
MySQL 8.0+
```

##  🏗 Estructura del Proyecto
baseapp/
├── app/               # Lógica de backend
│   ├── Http/         # Controladores
│   └── Models/       # Modelos Eloquent
├── config/           # Configuraciones
├── database/         # Migraciones y seeds
├── public/           # Assets compilados
├── resources/
│   ├── js/           # Código Vue
│   │   ├── Components/ # Componentes reutilizables
│   │   ├── Layouts/    # Layouts principales
│   │   ├── Pages/      # Vistas (Inertia)
│   │   └── Stores/     # Estado global 
│   └── scss/         # Estilos globales
├── routes/           # Definición de rutas
└── vite.config.js    # Configuración de Vite

## 🚀 Instalación Rápida

1. Instalar dependencias
```bash 
composer install
npm install
npm install bootstrap@5.3.3 @popperjs/core
npm install bootstrap@5.3.3 sass
```

2. Configurar entorno
```bash 
cp .env.example .env
php artisan key:generate
```

3. Ejecutar migraciones
```bash 
php artisan migrate
```

4. Iniciar servidores
```bash 
php artisan serve
npm run dev
```
##  Comandos Útiles
Comando	Descripción
npm run dev	Inicia Vite en modo desarrollo
npm run build	Compila assets para producción
php artisan test	Ejecuta pruebas PHPUnit
php artisan make:module	Crea nuevo módulo (si está configurado)
🤝 Contribución
Haz fork del proyecto

Crea tu branch (git checkout -b feature/awesome-feature)

Commit tus cambios (git commit -m 'Add awesome feature')

Push al branch (git push origin feature/awesome-feature)

Abre un Pull Request

## 🚀 Comandos si solo quieres iniciar el proyecto y trabajr en el

```bash 
1. Instalar dependencias
composer install
npm install
```
```bash 
2. Ejecutar migraciones
php artisan migrate
```
```bash 
3. Iniciar servidores
php artisan serve
npm run dev
```


<div align="center"> <p> usando el stack más moderno de PHP/JavaScript</p> <img src="https://laravel.com/img/logomark.min.svg" width="50" alt="Laravel"> <img src="https://vuejs.org/images/logo.png" width="50" alt="Vue"></div> ```