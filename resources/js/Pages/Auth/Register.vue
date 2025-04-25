<template>
    <Head title="Register" />
        <form @submit.prevent="submit" class="p-4 p-md-5 border rounded-3 bg-light shadow-sm mx-auto" style="max-width: 500px;">
            <h2 class="mb-4 text-center">Crear cuenta</h2>

            <!-- Nombre -->
            <div class="mb-3">
                <label for="name" class="form-label">Nombre</label>
                <input
                    id="name"
                    type="text"
                    class="form-control"
                    v-model="form.name"
                    required
                    autofocus
                    autocomplete="name"
                />
                <div v-if="form.errors.name" class="text-danger mt-1">{{ form.errors.name }}</div>
            </div>

            <!-- Email -->
            <div class="mb-3">
                <label for="email" class="form-label">Correo electrónico</label>
                <input
                    id="email"
                    type="email"
                    class="form-control"
                    v-model="form.email"
                    required
                    autocomplete="username"
                />
                <div v-if="form.errors.email" class="text-danger mt-1">{{ form.errors.email }}</div>
            </div>

            <!-- Contraseña -->
            <div class="mb-3">
                <label for="password" class="form-label">Contraseña</label>
                <input
                    id="password"
                    type="password"
                    class="form-control"
                    v-model="form.password"
                    required
                    autocomplete="new-password"
                />
                <div v-if="form.errors.password" class="text-danger mt-1">{{ form.errors.password }}</div>
            </div>

            <!-- Confirmación -->
            <div class="mb-3">
                <label for="password_confirmation" class="form-label">Confirmar contraseña</label>
                <input
                    id="password_confirmation"
                    type="password"
                    class="form-control"
                    v-model="form.password_confirmation"
                    required
                    autocomplete="new-password"
                />
                <div v-if="form.errors.password_confirmation" class="text-danger mt-1">{{ form.errors.password_confirmation }}</div>
            </div>

            <!-- Enlace + Botón -->
            <div class="d-flex justify-content-between align-items-center mt-4">
                <Link :href="route('login')" class="text-decoration-none small">
                    ¿Ya tienes una cuenta?
                </Link>

                <button
                    type="submit"
                    class="btn btn-primary"
                    :disabled="form.processing"
                >
                    Crear cuenta
                </button>
            </div>
        </form>
</template>

<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>
