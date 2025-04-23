<template>
    <header class="sticky-top">
      <nav class="navbar navbar-expand-lg navbar-dark bg-dark shadow-sm">
        <div class="container">
          <!-- Logo/Brand -->
          <Link href="/" class="navbar-brand d-flex align-items-center text-white">
            <img src="" alt="Logo" height="40" class="me-2" />
            <span class="fw-bold">MiApp</span>
          </Link>
  
          <!-- Menu Items (sin toggle) -->
          <div class="navbar-collapse d-flex justify-content-between w-100" id="navbarContent">
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
              <li class="nav-item">
                <Link
                  href="/"
                  class="nav-link text-white"
                  :class="{ active: $page.url === '/' }"
                >
                  <i class="bi bi-house-door me-1"></i>Inicio
                </Link>
              </li>
              <li class="nav-item">
                <Link
                  href="/contacto"
                  class="nav-link text-white"
                  :class="{ active: $page.url === '/contacto' }"
                >
                  <i class="bi bi-envelope me-1"></i>Contacto
                </Link>
              </li>
              <li class="nav-item">
                <Link
                  href="/blog"
                  class="nav-link text-white"
                  :class="{ active: $page.url === '/blog' }"
                >
                  <i class="bi bi-journal-text me-1"></i>Blog
                </Link>
              </li>
            </ul>
          </div>
        </div>
      </nav>
    </header>
  </template>
  
  <script setup>
  import { usePage } from '@inertiajs/vue3';
  
  const { props } = usePage();
  
  </script>
  
  <style scoped>
  .navbar {
    padding: 0.8rem 0;
    background: linear-gradient(135deg, #1a1a2e 0%, #161616 100%) !important;
  }
  
  .nav-link {
    font-weight: 500;
    padding: 0.5rem 1rem;
    border-radius: 0.25rem;
    transition: all 0.3s ease;
    color: white !important;
  }
  
  .nav-link:hover,
  .nav-link.active {
    background-color: rgba(255, 255, 255, 0.1);
  }
  
  .dropdown-menu {
    border: none;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  }
  
  .dropdown-item {
    transition: all 0.2s ease;
  }
  
  .dropdown-item:hover {
    background-color: #f8f9fa;
    padding-left: 1.5rem;
  }
  </style>
  