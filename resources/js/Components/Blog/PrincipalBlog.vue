<template>
    <div class="blog-detail-container">
        <div class="blog-content-row">
            <!-- Contenido principal -->
            <div class="blog-main-content">
                <div class="blog-image-container">
                    <!-- Título del blog -->
                    <h1 class="blog-main-title">{{ blogs.titulo }}</h1>

                    <!-- Imagen del blog -->
                    <img :src="`/storage/blog/${blogs.foto}`" class="blog-featured-image" alt="Blog Image" />

                    <!-- Fecha y compartir -->
                    <div class="blog-meta-info">
                        <span class="blog-publish-date">
                            Publicado el {{ formattedDate }}
                        </span>
                        <div class="blog-social-share">
                            <span class="blog-share-label">Comparte: </span>
                            <a href="https://www.facebook.com/unilangsantander1350"
                                class="blog-social-icon blog-fb-icon">
                                <i class="fab fa-facebook-f"></i>
                            </a>
                            <a href="https://www.instagram.com/unilangidiomas/" class="blog-social-icon blog-ig-icon">
                                <i class="fab fa-instagram"></i>
                            </a>
                            <a href="https://www.youtube.com/channel/UCEFWeMxponjX_QIwHav7ZGQ"
                                class="blog-social-icon blog-yt-icon">
                                <i class="fab fa-youtube"></i>
                            </a>
                        </div>
                    </div>

                    <!-- Descripción del blog -->
                    <div class="blog-content-text" v-html="formattedDescription" :class="{
                        'blog-empty-content': isEmpty(formattedDescription),
                    }"></div>
                </div>
            </div>

            <!-- Sidebar -->
            <div class="blog-sidebar">
                <!-- Buscador -->
                <div class="blog-search-box">
                    <input type="text" class="blog-search-input" placeholder="Buscar..." v-model="searchQuery" />
                </div>

                <!-- Resultados de la búsqueda -->
                <div v-if="searchQuery.length > 0" class="blog-search-results">
                    <h2 class="blog-sidebar-title">Resultados de búsqueda</h2>
                    <section class="blog-search-grid">
                        <article v-for="(articulo, index) in filteredBlogs" :key="articulo.slug"
                            class="blog-search-item">
                            <a :href="`/blog/${articulo.slug}`" class="blog-search-link">
                                <div class="blog-search-image-container">
                                    <img :src="`/storage/blog/${articulo.foto}`" :alt="articulo.titulo"
                                        class="blog-search-image" />
                                    <div class="blog-search-overlay">
                                        <h2 class="blog-search-title">
                                            {{ articulo.titulo }}
                                        </h2>
                                    </div>
                                </div>
                            </a>
                        </article>
                    </section>
                </div>

                <!-- Artículos más recientes -->
                <div class="blog-recent-posts">
                    <div class="blog-sidebar-header">
                        <h2 class="blog-sidebar-title">Noticias más actuales</h2>
                    </div>
                    <div class="blog-recent-grid">
                        <section class="blog-recent-items">
                            <article v-for="(articulo, index) in filteredBlogs.slice(0, 3)" :key="articulo.slug"
                                class="blog-recent-item">
                                <a :href="`/blog/${articulo.slug}`" class="blog-recent-link">
                                    <div class="blog-recent-image-container">
                                        <img :src="`/storage/blog/${articulo.foto}`" :alt="articulo.titulo"
                                            class="blog-recent-image" />
                                        <div class="blog-recent-overlay"></div>
                                    </div>
                                    <div class="blog-recent-content">
                                        <h2 class="blog-recent-post-title">
                                            {{ articulo.titulo }}
                                        </h2>
                                    </div>
                                </a>
                            </article>
                        </section>
                    </div>
                </div>
            </div>
        </div>
        <!-- Contenedor para los botones de navegación -->
        <div class="blog-navigation">
            <div class="blog-nav-item">
                <a href="/blog" class="blog-nav-btn blog-nav-text">
                    <i class="bi bi-arrow-left me-2"></i>
                    Regresar a los blogs
                </a>
            </div>
        </div>

    </div>
</template>

<script setup>
import { defineProps, computed, ref } from "vue";
import { Link } from '@inertiajs/vue3';

const props = defineProps({
    blogs: {
        type: Object,
        required: true,
    },
    blogs3ultimos: {
        type: Array,
        default: () => [],
    },
    todosLosBlogs: {
        type: Array,
        default: () => [],
    },
    previousBlogSlug: {
        type: String,
        default: null,
    },
    nextBlogSlug: {
        type: String,
        default: null,
    },
});

const searchQuery = ref("");

const formattedDate = computed(() => {
    if (!props.blogs?.created_at) return "Fecha no disponible";
    return new Date(props.blogs.created_at).toLocaleDateString();
});

const filteredBlogs = computed(() => {
    if (!props.todosLosBlogs || !Array.isArray(props.todosLosBlogs)) return [];
    if (!searchQuery.value) return props.todosLosBlogs;

    return props.todosLosBlogs.filter((blog) =>
        blog.titulo?.toLowerCase().trim().includes(searchQuery.value.toLowerCase().trim())
    );
});

const previousBlogSlug = computed(() => props.previousBlogSlug);
const nextBlogSlug = computed(() => props.nextBlogSlug);

const formattedDescription = computed(() => {
    let description = props.blogs?.descripcion || "";
    description = description.replace(/\n/g, "<br />");
    description = formatMarkdown(description);
    description = formatListTypes(description);
    return `<p>${description}</p>`;
});

const isEmpty = (description) => !(description && description.trim());

const formatListTypes = (description) => {
    description = description.replace(
        /<li[^>]*data-list="bullet"[^>]*>/g,
        '<li style="list-style-type: disc;">'
    );
    description = description.replace(
        /<li[^>]*data-list="ordered"[^>]*>/g,
        '<li style="list-style-type: decimal;">'
    );
    return description;
};

const formatMarkdown = (description) => {
    return description
        .replace(/(#{1})\s*(.*)/g, '<h1 class="blog-heading-1">$2</h1>')
        .replace(/(#{2})\s*(.*)/g, '<h2 class="blog-heading-2">$2</h2>')
        .replace(/(#{3})\s*(.*)/g, '<h3 class="blog-heading-3">$2</h3>')
        .replace(/(#{4})\s*(.*)/g, '<h4 class="blog-heading-4">$2</h4>')
        .replace(/(#{5})\s*(.*)/g, '<h5 class="blog-heading-5">$2</h5>');
};
</script>
