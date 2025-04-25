<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link } from '@inertiajs/vue3';
</script>

<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            <div class="flex items-center justify-between">
                <h2 class="text-2xl font-bold leading-tight text-gray-800">
                    Panel de Administración
                </h2>
                <Link
                    href="/admin/blog/create"
                    class="inline-block px-4 py-2 bg-indigo-600 text-white text-sm font-semibold rounded-md shadow hover:bg-indigo-700 transition"
                >
                    Crear Blog
                </Link>
            </div>
        </template>

        <div class="py-12">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8 grid gap-6">
                <!-- Mensaje de bienvenida -->
                <div class="overflow-hidden rounded-lg bg-white shadow-md">
                    <div class="p-6 text-gray-800 text-lg">
                        Bienvenido/a, estás autenticado correctamente.
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
