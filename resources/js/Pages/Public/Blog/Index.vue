<template>
    <div class="container-fluid px-0 d-flex flex-column align-items-center">
        <!-- Verificar si blogs contiene datos -->
        <div class="w-100 d-flex justify-center" 
            v-if="blogs.data && blogs.data.length">
            <BlogActualidad :blogs="blogs" :todosLosBlogs="todosLosBlogs" :categorias-unicas="categoriasUnicas" />
        </div>
        <div v-else>
            Cargando datos...
        </div>
    </div>
</template>

<script setup>
import BlogActualidad from "@/Components/Home/BlogActualidad.vue";


// Definir la prop blogs como un objeto
const props = defineProps({
    blogs: {
        type: Object,
        required: true,
    },
    categoriasUnicas: {
        type: Object,
        required: true,
    },
    todosLosBlogs: {
        type: Array,
        required: true,
    },
});

</script>
