<template>
    <div class="new-post-container">
        <h2 class="new-post-title">Nueva Publicación</h2>

        <form @submit.prevent="submit" enctype="multipart/form-data" class="new-post-form">
            <!-- Campo Foto -->
            <div class="new-post-field">
                <label for="foto" class="new-post-label">Imagen de la publicación</label>
                <input type="file" id="foto" @change="handleFileUpload" class="new-post-input-file" accept="image/*" />
                <small class="new-post-hint">
                    Solo se permiten archivos de imagen (JPG, JPEG, PNG).
                </small>
                <div v-if="form.errors.foto && !form.foto" class="new-post-error">
                    {{ form.errors.foto }}
                </div>

                <!-- Vista previa de la imagen -->
                <div v-if="imagePreview || form.foto" class="new-post-preview-container">
                    <h5 class="new-post-preview-title">Vista previa de la imagen:</h5>
                    <img :src="imagePreview || `/storage/blog/${form.foto}`" class="new-post-preview-image"
                        :alt="form.titulo" />
                </div>
            </div>

            <!-- Campo Título -->
            <div class="new-post-field">
                <label for="titulo" class="new-post-label">Título</label>
                <input type="text" id="titulo" v-model="form.titulo" class="new-post-input-text" required
                    placeholder="Ingrese el título de la publicación" />
                <div class="new-post-error" v-if="form.errors.titulo">
                    {{ form.errors.titulo }}
                </div>
            </div>

            <!-- Campo Subtítulo -->
            <div class="new-post-field">
                <label for="subtitulo" class="new-post-label">Subtítulo</label>
                <input type="text" id="subtitulo" v-model="form.subtitulo" class="new-post-input-text" required
                    placeholder="Ingrese el subtítulo de la publicación" />
                <div class="new-post-error" v-if="form.errors.subtitulo">
                    {{ form.errors.subtitulo }}
                </div>
            </div>

            <!-- Campo Categoría -->
            <div class="new-post-field">
                <label for="categoria" class="new-post-label">Categoría</label>
                <input type="text" id="categoria" v-model="form.categoria" class="new-post-input-text" required
                    placeholder="Ingrese la categoría de la publicación" />
                <div class="new-post-error" v-if="form.errors.categoria">
                    {{ form.errors.categoria }}
                </div>
            </div>

            <!-- Campo Descripción -->
            <div class="new-post-field">
                <label for="descripcion" class="new-post-label">Descripción</label>
                <textarea id="descripcion" v-model="form.descripcion" class="new-post-textarea"
                    placeholder="Ingrese la descripción de la publicación"></textarea>
                <div class="new-post-error" v-if="form.errors.descripcion">
                    {{ form.errors.descripcion }}
                </div>
            </div>

            <!-- Botones de acción -->
            <div class="new-post-actions">
                <NavLink :href="route('admin.blog.index')" class="new-post-back-button">
                    <span class="new-post-back-icon">
                        <i class="bi bi-arrow-left-circle"></i>
                    </span>
                    <span class="new-post-back-text">Volver a la lista</span>
                </NavLink>
                <button type="submit" class="new-post-submit-button"
                    :disabled="form.processing">
                    <span class="new-post-submit-icon">
                        <i class="bi bi-plus-circle"></i>
                    </span>
                    <span class="new-post-submit-text">
                        Crear Publicación
                    </span>
                </button>
            </div>
        </form>
    </div>
</template>

<script setup>
import { useForm } from "@inertiajs/vue3";
import { ref } from "vue";
import NavLink from "@/Components/NavLink.vue";
import Swal from "sweetalert2";

// Configuración inicial del formulario
const form = useForm({
    foto: null,
    titulo: "",
    subtitulo: "",
    descripcion: "",
    categoria: "",
});

// Referencia para la vista previa de la imagen
const imagePreview = ref(null);

// Función para manejar la carga del archivo y mostrar la vista previa
const handleFileUpload = (event) => {
    const file = event.target.files[0];
    if (file) {
        const allowedTypes = ["image/jpeg", "image/png", "image/jpg"];
        if (!allowedTypes.includes(file.type)) {
            Swal.fire({
                title: "Archivo no permitido",
                text: "Solo puedes subir imágenes en formato JPG, JPEG, PNG o GIF.",
                icon: "warning",
                confirmButtonText: "Aceptar",
                confirmButtonColor: "#dc3545",
            });
            event.target.value = ""; // Limpiar el input
            return;
        }

        form.foto = file;
        imagePreview.value = URL.createObjectURL(file);
    }
};

// Función para enviar el formulario
const submit = () => {
    // Validación para el título
    if (form.titulo.length > 500) {
        // Mostrar el error visual en el input de título
        document.getElementById("titulo").classList.add("is-invalid");

        // Mostrar el mensaje de error en SweetAlert
        Swal.fire({
            title: "Error",
            text: "El título no puede superar los 500 caracteres.",
            icon: "error",
            confirmButtonText: "Aceptar",
            confirmButtonColor: "#dc3545",
        });

        return; // Detener el submit si el título es inválido
    } else {
        // Remover la clase de error si la longitud es válida
        document.getElementById("titulo").classList.remove("is-invalid");
    }

    // Validación para el subtítulo
    if (form.subtitulo.length > 500) {
        // Mostrar el error visual en el input de subtítulo
        document.getElementById("subtitulo").classList.add("is-invalid");

        // Mostrar el mensaje de error en SweetAlert
        Swal.fire({
            title: "Error",
            text: "El subtítulo no puede superar los 500 caracteres.",
            icon: "error",
            confirmButtonText: "Aceptar",
            confirmButtonColor: "#dc3545",
        });

        return; // Detener el submit si el subtítulo es inválido
    } else {
        // Remover la clase de error si la longitud es válida
        document.getElementById("subtitulo").classList.remove("is-invalid");
    }

    // Si la validación es correcta, continuar con el envio del formulario
    form.post(route("admin.blog.store"), {
        onSuccess: () => {
            Swal.fire({
                title: "¡Blog Creado!",
                text: "El blog se ha creado correctamente.",
                icon: "success",
                confirmButtonText: "Ir al índice de blogs",
                confirmButtonColor: "#198754",
            }).then((result) => {
                if (result.isConfirmed) {
                    window.location.href = '/admin/blog';
                }
            });
        },
        onError: (errors) => {
            // Mostrar errores de validación si los hay
            if (errors.titulo) {
                Swal.fire({
                    title: "Error",
                    text: errors.titulo[0], // Mensaje de error para título
                    icon: "error",
                    confirmButtonText: "Aceptar",
                    confirmButtonColor: "#dc3545",
                });
                document.getElementById("titulo").classList.add("is-invalid"); // Resaltar campo título
            }
            if (errors.subtitulo) {
                Swal.fire({
                    title: "Error",
                    text: errors.subtitulo[0], // Mensaje de error para subtítulo
                    icon: "error",
                    confirmButtonText: "Aceptar",
                    confirmButtonColor: "#dc3545",
                });
                document.getElementById("subtitulo").classList.add("is-invalid"); // Resaltar campo subtítulo
            }
        },
        onFinish: () => {
            form.reset(); // Resetear el formulario después de completar el proceso
        },
    });
};
</script>
