<template>
    <footer class="custom-footer">
        <div class="custom-footer__container">
            <div class="custom-footer__row">
                <!-- Company Info -->
                <div class="custom-footer__company">
                    <div class="custom-footer__logo-container">
                        <Link href="/" class="custom-footer__logo-link">
                        <img src="" alt="Logo" height="40" class="custom-footer__logo-image">
                        <span class="custom-footer__logo-text">MiApp</span>
                        </Link>
                    </div>
                    <p class="custom-footer__description">Transformando ideas en soluciones digitales innovadoras desde 2023.</p>
                    <div class="custom-footer__social-icons">
                        <Link href="#" class="custom-footer__social-link"><i class="bi bi-facebook"></i></Link>
                        <Link href="#" class="custom-footer__social-link"><i class="bi bi-twitter"></i></Link>
                        <Link href="#" class="custom-footer__social-link"><i class="bi bi-linkedin"></i></Link>
                        <Link href="#" class="custom-footer__social-link"><i class="bi bi-instagram"></i></Link>
                    </div>
                </div>

                <!-- Quick Links -->
                <div class="custom-footer__links">
                    <h5 class="custom-footer__title">Enlaces Rápidos</h5>
                    <ul class="custom-footer__list">
                        <li class="custom-footer__list-item"><Link href="/"
                                class="custom-footer__link">Inicio</Link></li>
                        <li class="custom-footer__list-item"><Link href="/about"
                                class="custom-footer__link">Nosotros</Link></li>
                        <li class="custom-footer__list-item"><Link href="/services"
                                class="custom-footer__link">Servicios</Link></li>
                        <li class="custom-footer__list-item"><Link href="/pricing"
                                class="custom-footer__link">Precios</Link></li>
                        <li class="custom-footer__list-item"><Link href="/contact"
                                class="custom-footer__link">Contacto</Link></li>
                    </ul>
                </div>

                <!-- Services -->
                <div class="custom-footer__services">
                    <h5 class="custom-footer__title">Servicios</h5>
                    <ul class="custom-footer__list">
                        <li class="custom-footer__list-item"><Link href="#" class="custom-footer__link">Desarrollo
                                Web</Link></li>
                        <li class="custom-footer__list-item"><Link href="#" class="custom-footer__link">App
                                Móviles</Link></li>
                        <li class="custom-footer__list-item"><Link href="#" class="custom-footer__link">Diseño
                                UI/UX</Link></li>
                        <li class="custom-footer__list-item"><Link href="#" class="custom-footer__link">Marketing
                                Digital</Link></li>
                        <li class="custom-footer__list-item"><Link href="#"
                                class="custom-footer__link">Consultoría</Link></li>
                    </ul>
                </div>

                <!-- Contact Info -->
                <div class="custom-footer__contact">
                    <h5 class="custom-footer__title">Contacto</h5>
                    <ul class="custom-footer__contact-list">
                        <li class="custom-footer__contact-item">
                            <i class="bi bi-geo-alt-fill custom-footer__contact-icon"></i>
                            <span>Av. Principal 123, Ciudad, País</span>
                        </li>
                        <li class="custom-footer__contact-item">
                            <i class="bi bi-telephone-fill custom-footer__contact-icon"></i>
                            <span>+1 234 567 890</span>
                        </li>
                        <li class="custom-footer__contact-item">
                            <i class="bi bi-envelope-fill custom-footer__contact-icon"></i>
                            <span>info@miapp.com</span>
                        </li>
                        <li class="custom-footer__contact-item">
                            <i class="bi bi-clock-fill custom-footer__contact-icon"></i>
                            <span>Lun-Vie: 9:00 - 18:00</span>
                        </li>
                    </ul>
                </div>
            </div>

            <hr class="custom-footer__divider">

            <div class="custom-footer__bottom-row">
                <div class="custom-footer__copyright">
                    <p class="custom-footer__copyright-text">&copy; 2023 MiApp. Todos los derechos reservados.</p>
                </div>
                <div class="custom-footer__legal-links">
                    <ul class="custom-footer__legal-list">
                        <li class="custom-footer__legal-item"><Link href="#" class="custom-footer__legal-link">Términos</Link>
                        </li>
                        <li class="custom-footer__legal-separator"><span>•</span></li>
                        <li class="custom-footer__legal-item"><Link href="#" class="custom-footer__legal-link">Privacidad</Link>
                        </li>
                        <li class="custom-footer__legal-separator"><span>•</span></li>
                        <li class="custom-footer__legal-item"><Link href="#" class="custom-footer__legal-link">Cookies</Link>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </footer>
</template>

<script setup>
import { Link } from '@inertiajs/vue3';
</script>
