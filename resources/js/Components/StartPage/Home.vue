<template>
    <div class="home-container">
      <!-- Hero Section -->
      <section class="hero-section bg-dark text-white py-5">
        <div class="container py-5">
          <div class="row align-items-center">
            <div class="col-lg-6">
              <h1 class="display-4 fw-bold mb-4">Bienvenido a <span class="text-primary">Nuestra Plataforma</span></h1>
              <p class="lead mb-4">Descubre las mejores soluciones para tus necesidades digitales con nuestra tecnología de vanguardia.</p>
              <div class="d-flex gap-3">
                <button class="btn btn-primary btn-lg px-4 py-2">Comenzar</button>
                <button class="btn btn-outline-light btn-lg px-4 py-2">Saber más</button>
              </div>
            </div>
          </div>
        </div>
      </section>
  
      <!-- Features Section -->
      <section class="features-section py-5 bg-light max-width">
        <div class="container py-5">
          <div class="text-center mb-5">
            <h2 class="fw-bold">Nuestras <span class="text-primary">Características</span></h2>
            <p class="text-muted lead">Descubre lo que nos hace diferentes</p>
          </div>
          
          <div class="row g-4">
            <div class="col-md-4">
              <div class="card h-100 border-0 shadow-sm hover-effect">
                <div class="card-body text-center p-4">
                  <div class="icon-box bg-primary bg-opacity-10 text-primary rounded-circle mx-auto mb-4">
                    <i class="bi bi-speedometer2 fs-3"></i>
                  </div>
                  <h5 class="fw-bold">Rendimiento Óptimo</h5>
                  <p class="text-muted">Tecnología de última generación para máxima velocidad y eficiencia.</p>
                </div>
              </div>
            </div>
            
            <div class="col-md-4">
              <div class="card h-100 border-0 shadow-sm hover-effect">
                <div class="card-body text-center p-4">
                  <div class="icon-box bg-success bg-opacity-10 text-success rounded-circle mx-auto mb-4">
                    <i class="bi bi-shield-check fs-3"></i>
                  </div>
                  <h5 class="fw-bold">Seguridad Robust</h5>
                  <p class="text-muted">Protección de datos con los más altos estándares de seguridad.</p>
                </div>
              </div>
            </div>
            
            <div class="col-md-4">
              <div class="card h-100 border-0 shadow-sm hover-effect">
                <div class="card-body text-center p-4">
                  <div class="icon-box bg-info bg-opacity-10 text-info rounded-circle mx-auto mb-4">
                    <i class="bi bi-people fs-3"></i>
                  </div>
                  <h5 class="fw-bold">Soporte 24/7</h5>
                  <p class="text-muted">Equipo de soporte disponible en todo momento para ayudarte.</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
  
      <!-- Testimonials -->
      <section class="testimonials-section py-5 max-width">
        <div class="container py-5">
          <div class="text-center mb-5">
            <h2 class="fw-bold">Lo que dicen <span class="text-primary">nuestros clientes</span></h2>
            <p class="text-muted lead">Experiencias reales de nuestros usuarios</p>
          </div>
          
          <div class="row g-4">
            <div class="col-md-4" v-for="(testimonial, index) in testimonials" :key="index">
              <div class="card h-100 border-0 shadow-sm">
                <div class="card-body p-4">
                  <div class="d-flex align-items-center mb-3">
                    <img :src="testimonial.avatar" class="rounded-circle me-3" width="60" height="60" alt="Avatar">
                    <div>
                      <h6 class="mb-0 fw-bold">{{ testimonial.name }}</h6>
                      <small class="text-muted">{{ testimonial.position }}</small>
                    </div>
                  </div>
                  <p class="mb-0">{{ testimonial.comment }}</p>
                  <div class="mt-3 text-warning">
                    <i class="bi bi-star-fill" v-for="n in testimonial.rating" :key="n"></i>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
  
      <!-- CTA Section -->
      <section class="cta-section bg-primary text-white py-5">
        <div class="container py-5 text-center">
          <h2 class="display-5 fw-bold mb-4">¿Listo para comenzar?</h2>
          <p class="lead mb-5">Únete a miles de usuarios satisfechos y lleva tu experiencia al siguiente nivel.</p>
          <button class="btn btn-light btn-lg px-5 py-3 fw-bold">Regístrate Gratis</button>
        </div>
      </section>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const testimonials = ref([
    {
      name: 'María González',
      position: 'CEO, TechSolutions',
      comment: 'Increíble plataforma que ha transformado nuestro flujo de trabajo. ¡Altamente recomendado!',
      rating: 5,
      avatar: 'https://randomuser.me/api/portraits/women/32.jpg'
    },
    {
      name: 'Carlos Mendoza',
      position: 'Director de Marketing',
      comment: 'La mejor decisión que hemos tomado para nuestro equipo. Soporte excepcional.',
      rating: 4,
      avatar: 'https://randomuser.me/api/portraits/men/75.jpg'
    },
    {
      name: 'Laura Fernández',
      position: 'Desarrolladora Frontend',
      comment: 'Herramientas intuitivas y documentación clara. Me encanta trabajar con este stack.',
      rating: 5,
      avatar: 'https://randomuser.me/api/portraits/women/63.jpg'
    }
  ]);
  </script>
  
  <style scoped>
  .home-container {
    overflow-x: hidden;
  }
  
  .hero-section {
    background: linear-gradient(135deg, #1e3a8a 0%, #1e40af 100%);
  }
  
  .icon-box {
    width: 70px;
    height: 70px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .hover-effect {
    transition: all 0.3s ease;
  }
  
  .hover-effect:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1) !important;
  }
  
  .cta-section {
    background: linear-gradient(135deg, #2563eb 0%, #1d4ed8 100%);
  }
  
  .testimonials-section {
    background-color: #f8f9fa;
  }
  </style>