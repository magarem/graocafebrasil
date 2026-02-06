<template>
  <section class="py-16 px-5 bg-transparent"> <div class="max-w-[1500px] mx-auto grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
      
      <div class="relative overflow-hidden rounded-2xl shadow-xl border border-black/5 aspect-video lg:aspect-[4/3]">
        <img src="https://agro2.com.br/wp-content/uploads/2021/10/235371.jpg" 
             alt="Pessoas conversando sobre café em uma fazenda" 
             class="w-full h-full object-cover transition-transform duration-700 hover:scale-105" />
        <div class="absolute inset-0 bg-gradient-to-t from-black/40 to-transparent"></div>
        <span class="absolute bottom-4 left-4 text-white text-xs font-bold uppercase tracking-widest bg-black/50 px-3 py-1 rounded-full">Nossa História</span>
      </div>

      <div class="space-y-6">
        <h2 class="text-4xl font-serif text-[#3a2216] font-bold leading-tight">
          Nossa paixão por cafés especiais e o cuidado em cada xícara.
        </h2>
        
        <p class="text-gray-700 leading-relaxed text-lg">
          Na Gran Café Brasil, acreditamos que cada xícara de café conta uma história. Desde 20XX, temos a missão de conectar amantes de café aos melhores micro-lotes do Brasil, trazidos diretamente de produtores que compartilham nossa paixão pela qualidade e sustentabilidade.
        </p>
        
        <p class="text-gray-700 leading-relaxed text-lg">
          Selecionamos a dedo cada grão, acompanhamos o processo de torra e garantimos que você receba um café fresco, aromático e repleto de sabor. Mais do que vender café, queremos proporcionar uma experiência única e educar sobre o fascinante universo dos cafés especiais.
        </p>

        <NuxtLink to="/sobre" 
                  class="inline-flex items-center gap-2 text-[#A67C52] font-black text-sm uppercase tracking-widest hover:gap-4 transition-all duration-300 pt-4">
          Conheça nossa equipe 
          <i class="pi pi-arrow-right text-xs"></i>
        </NuxtLink>
      </div>
    </div>
  </section>
</template>

<script setup>
// Não precisa de script adicional para esta seção
</script>

<style scoped>
/* Estilos específicos se necessário */
.font-serif {
  font-family: 'Playfair Display', serif; /* Ou a fonte do seu logo */
}
</style>