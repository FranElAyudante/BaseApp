<template>
    <footer class="bg-dark text-white pt-5 pb-4">
        <div class="container">
            <div class="row g-4">
                <!-- Company Info -->
                <div class="col-lg-4 col-md-6 text-white">
                    <div class="mb-4">
                        <Link to="/" class="d-flex align-items-center text-decoration-none">
                        <img src="" alt="Logo" height="40" class="me-2">
                        <span class="fs-4 fw-bold text-white">MiApp</span>
                        </Link>
                    </div>
                    <p class="text-hite">Transformando ideas en soluciones digitales innovadoras desde 2023.</p>
                    <div class="social-icons d-flex gap-3 mt-4">
                        <a href="#" class="text-white"><i class="bi bi-facebook fs-5"></i></a>
                        <a href="#" class="text-white"><i class="bi bi-twitter fs-5"></i></a>
                        <a href="#" class="text-white"><i class="bi bi-linkedin fs-5"></i></a>
                        <a href="#" class="text-white"><i class="bi bi-instagram fs-5"></i></a>
                    </div>
                </div>

                <!-- Quick Links -->
                <div class="col-lg-2 col-md-6">
                    <h5 class="mb-4 fw-bold">Enlaces Rápidos</h5>
                    <ul class="list-unstyled">
                        <li class="mb-2"><router-link to="/"
                                class="text-muted text-decoration-none hover-effect">Inicio</router-link></li>
                        <li class="mb-2"><router-link to="/about"
                                class="text-muted text-decoration-none hover-effect">Nosotros</router-link></li>
                        <li class="mb-2"><router-link to="/services"
                                class="text-muted text-decoration-none hover-effect">Servicios</router-link></li>
                        <li class="mb-2"><router-link to="/pricing"
                                class="text-muted text-decoration-none hover-effect">Precios</router-link></li>
                        <li class="mb-2"><router-link to="/contact"
                                class="text-muted text-decoration-none hover-effect">Contacto</router-link></li>
                    </ul>
                </div>

                <!-- Services -->
                <div class="col-lg-2 col-md-6">
                    <h5 class="mb-4 fw-bold">Servicios</h5>
                    <ul class="list-unstyled">
                        <li class="mb-2"><a href="#" class="text-muted text-decoration-none hover-effect">Desarrollo
                                Web</a></li>
                        <li class="mb-2"><a href="#" class="text-muted text-decoration-none hover-effect">App
                                Móviles</a></li>
                        <li class="mb-2"><a href="#" class="text-muted text-decoration-none hover-effect">Diseño
                                UI/UX</a></li>
                        <li class="mb-2"><a href="#" class="text-muted text-decoration-none hover-effect">Marketing
                                Digital</a></li>
                        <li class="mb-2"><a href="#"
                                class="text-muted text-decoration-none hover-effect">Consultoría</a></li>
                    </ul>
                </div>

                <!-- Contact Info -->
                <div class="col-lg-4 col-md-6">
                    <h5 class="mb-4 fw-bold">Contacto</h5>
                    <ul class="list-unstyled text-muted">
                        <li class="mb-3 d-flex">
                            <i class="bi bi-geo-alt-fill me-3 mt-1"></i>
                            <span>Av. Principal 123, Ciudad, País</span>
                        </li>
                        <li class="mb-3 d-flex">
                            <i class="bi bi-telephone-fill me-3 mt-1"></i>
                            <span>+1 234 567 890</span>
                        </li>
                        <li class="mb-3 d-flex">
                            <i class="bi bi-envelope-fill me-3 mt-1"></i>
                            <span>info@miapp.com</span>
                        </li>
                        <li class="mb-3 d-flex">
                            <i class="bi bi-clock-fill me-3 mt-1"></i>
                            <span>Lun-Vie: 9:00 - 18:00</span>
                        </li>
                    </ul>
                </div>
            </div>

            <hr class="my-4 bg-secondary">

            <div class="row">
                <div class="col-md-6 text-center text-md-start">
                    <p class="mb-0 text-muted">&copy; 2023 MiApp. Todos los derechos reservados.</p>
                </div>
                <div class="col-md-6 text-center text-md-end">
                    <ul class="list-inline mb-0">
                        <li class="list-inline-item"><a href="#" class="text-muted text-decoration-none">Términos</a>
                        </li>
                        <li class="list-inline-item"><span class="text-muted">•</span></li>
                        <li class="list-inline-item"><a href="#" class="text-muted text-decoration-none">Privacidad</a>
                        </li>
                        <li class="list-inline-item"><span class="text-muted">•</span></li>
                        <li class="list-inline-item"><a href="#" class="text-muted text-decoration-none">Cookies</a>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </footer>
</template>

<script setup>
import { Link } from '@inertiajs/vue3';
// No se necesitan scripts complejos para el footer básico
// Para versión avanzada podrías añadir un store para los datos dinámicos
</script>

<style scoped>
footer {
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
    color: white !important;
}

.hover-effect {
    transition: all 0.3s ease;
    color: white !important;
}

.hover-effect:hover {
    color: white !important;
    padding-left: 5px;
}

.social-icons a {
    transition: all 0.3s ease;
    opacity: 0.7;
    color: white !important;
}

.social-icons a:hover {
    opacity: 1;
    transform: translateY(-3px);
    color: white !important;
}

.list-unstyled li {
    transition: all 0.3s ease;
    color: white !important;
}
</style>