<template>
  <header class="main-header">
    <nav class="main-nav">
      <div class="nav-container">
        <Link href="/" class="nav-brand">
          <img src="" alt="Logo" class="nav-logo" />
          <span class="nav-brand-text">MiApp</span>
        </Link>

        <div class="nav-collapse">
          <ul class="nav-menu">
            <li class="nav-item">
              <Link
                href="/"
                class="nav-link"
                :class="{ 'nav-link-active': $page.url === '/' }"
              >
                <i class="nav-icon bi bi-house-door"></i>Inicio
              </Link>
            </li>
            <li class="nav-item">
              <Link
                href="/contacto"
                class="nav-link"
                :class="{ 'nav-link-active': $page.url === '/contacto' }"
              >
                <i class="nav-icon bi bi-envelope"></i>Contacto
              </Link>
            </li>
            <li class="nav-item">
              <Link
                href="/blog"
                class="nav-link"
                :class="{ 'nav-link-active': $page.url === '/blog' }"
              >
                <i class="nav-icon bi bi-journal-text"></i>Blog
              </Link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { Link, usePage } from '@inertiajs/vue3';

const { props } = usePage();
</script>