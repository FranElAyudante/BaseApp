<template>
    <section class="news-section max-width">
        <div class="news-container">
            <div class="news-row">
                <!-- Contenido principal -->
                <div class="news-main-content">
                    <div class="news-grid">
                        <div v-for="(pair, index) in groupedBlogs" :key="index" class="news-row-group">
                            <div v-for="news in pair" :key="news.id" class="news-card-wrapper">
                                <div class="news-card">
                                    <div class="news-category-label">{{ news.categoria }}</div>
                                    <img :src="`/storage/blog/${news.foto}`" class="news-card-image"
                                        :alt="news.titulo" />
                                    <div class="news-card-body">
                                        <h5 class="news-card-title">{{ news.titulo }}</h5>
                                        <p class="news-card-text">{{ news.subtitulo }}</p>
                                        <a :href="route('blog.showPublic', { slug: news.slug })" class="news-read-more">
                                            Leer más
                                        </a>
                                    </div>
                                    <div class="news-card-footer">
                                        <span class="news-date">{{ formatDate(news.created_at) }}</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Paginación con Bootstrap 5 -->
                    <nav v-if="props.blogs.last_page > 1" aria-label="Paginación del blog">
                        <ul class="pagination justify-content-center">
                            <!-- Anterior -->
                            <li class="page-item" :class="{ disabled: !props.blogs.prev_page_url }">
                                <NavLink class="page-link" :href="props.blogs.prev_page_url || '#'" tabindex="-1"
                                    aria-disabled="!props.blogs.prev_page_url">
                                    Anterior
                                </NavLink>
                            </li>

                            <!-- Números de página -->
                            <li v-for="page in props.blogs.last_page" :key="page" class="page-item"
                                :class="{ active: page === props.blogs.current_page }">
                                <NavLink class="page-link" :href="`/blog?page=${page}`">
                                    {{ page }}
                                </NavLink>
                            </li>

                            <!-- Siguiente -->
                            <li class="page-item" :class="{ disabled: !props.blogs.next_page_url }">
                                <NavLink class="page-link" :href="props.blogs.next_page_url || '#'">
                                    Siguiente
                                </NavLink>
                            </li>
                        </ul>
                    </nav>

                </div>

                <!-- Sidebar -->
                <div class="news-sidebar">
                    <h4 class="sidebar-title">Categorías</h4>
                    <select v-model="currentFilter" @change="changeFilter(currentFilter)" class="sidebar-select">
                        <option v-for="category in ['Todas', ...categoriasUnicas]" :key="category" :value="category">
                            {{ category }}
                        </option>
                    </select>
                    <h4 class="sidebar-title">Blogs más Leídas</h4>
                    <div class="sidebar-popular">
                        <div v-for="image in popularBlogs" :key="image.slug" class="sidebar-popular-item">
                            <a :href="route('blog.showPublic', { slug: image.slug })">
                                <img :src="`/storage/blog/${image.foto}`" class="sidebar-popular-image"
                                    :alt="image.titulo" />
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, computed, onMounted } from "vue";
import NavLink from "../NavLink.vue";

const props = defineProps({
    blogs: { type: Object, required: true },
    todosLosBlogs: { type: Array, required: true },
    categoriasUnicas: { type: Array, required: true },
});

const currentFilter = ref(localStorage.getItem("currentFilter") || "Todas");

onMounted(() => {
    currentFilter.value = localStorage.getItem("currentFilter") || "Todas";
});

const formatDate = (date) => {
    if (!date) return "Fecha no disponible";
    const dateObj = new Date(date);
    return dateObj.toLocaleDateString("es-ES", {
        year: "numeric",
        month: "long",
        day: "numeric",
    });
};

const changeFilter = (newFilter) => {
    currentFilter.value = newFilter;
    localStorage.setItem("currentFilter", newFilter);
};

const filteredBlogs = computed(() => {
    let blogs = currentFilter.value === "Todas"
        ? props.todosLosBlogs
        : props.todosLosBlogs.filter((news) => {
            const categories = news.categoria
                ? news.categoria.split(",").map((c) => c.trim().toLowerCase())
                : [];
            return categories.includes(currentFilter.value.toLowerCase());
        });

    return blogs.sort((a, b) => new Date(b.created_at) - new Date(a.created_at));
});

const paginatedBlogs = computed(() => {
    const start = (props.blogs.current_page - 1) * props.blogs.per_page;
    const end = start + props.blogs.per_page;
    return filteredBlogs.value.slice(start, end);
});

const popularBlogs = computed(() => props.todosLosBlogs.slice(0, 6));

const groupedBlogs = computed(() => {
    const pairs = [];
    for (let i = 0; i < paginatedBlogs.value.length; i += 2) {
        pairs.push(paginatedBlogs.value.slice(i, i + 2));
    }
    return pairs;
});

const loadPage = async (url) => {
    if (!url) return;
    try {
        const response = await fetch(url, {
            headers: { "Accept": "application/json" }
        });

        const text = await response.text();
        if (!response.ok) {
            throw new Error(`Error HTTP ${response.status}: ${text}`);
        }

        try {
            const data = JSON.parse(text);
            blogs.value = data;
            currentPage.value = data.current_page;
        } catch (jsonError) {
            console.error('Error al parsear la respuesta JSON:', jsonError);
            console.error('Respuesta de la API:', text);
        }
    } catch (error) {
        console.error("Error al cargar la página:", error);
    }
};
</script>