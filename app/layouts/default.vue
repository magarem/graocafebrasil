<template>
  <div class="min-h-screen flex flex-col bg-[#f2e4d3] selection:bg-[#A67C52] selection:text-white">
    
    <header class="fixed top-0 left-0 right-0 z-[100]">
      <TopBar />
    </header>

    <main class="max-w-[1500px] mx-auto px-5 md:px-10 md:py-20 md:pt-30">
      <slot />
    </main>

    <footer>
      <Footer />
    </footer>

    <div class="fixed bottom-8 right-8 z-50">
       </div>

  </div>
</template>

<script setup lang="ts">
// O layout default carrega automaticamente em todas as páginas, 
// exceto onde você definir definePageMeta({ layout: false }) como no Sirius.
</script>

<style>
/* Smooth Scroll Global para as âncoras funcionarem suavemente */
html {
  scroll-behavior: smooth;
}

/* Offset para as âncoras não pararem atrás do header fixo */
:target {
  scroll-margin-top: 100px;
}

/* Tipografia global para o projeto Gran Café Brasil */
body {
  font-family: 'Inter', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #3a2216;
}

h1, h2, h3, .font-serif {
  font-family: 'Playfair Display', serif; /* Ou a fonte serifada do seu projeto */
}

/* Transições de página suaves (Nuxt 3/4) */
.page-enter-active,
.page-leave-active {
  transition: all 0.3s;
}
.page-enter-from,
.page-leave-to {
  opacity: 0;
  filter: blur(0.5rem);
}
</style>