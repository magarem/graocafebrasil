<template>
  <section class="w-full  py-4 flex justify-center mt-1">
    <div class="w-full max-w-[1500px] h-[500px] grid grid-cols-1 lg:grid-cols-10 gap-4 px-4">
      
      <div class="lg:col-span-7 relative group overflow-hidden rounded-2xl border border-[#333]">
        <img 
          src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?q=80&w=1500&h=350&fit=crop" 
          alt="Banner Principal" 
          class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105"
        />
        <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/20 to-transparent flex flex-col justify-end p-10">
          <Tag value="RESERVA ESPECIAL" severity="warning" class="w-fit mb-4" />
          <h1 class="text-5xl font-bold text-white mb-4 leading-tight">A Experiência do <br/> Café de Origem</h1>
          <p class="text-gray-300 text-lg max-w-xl">Notas sensoriais complexas e torra artesanal para os paladares mais exigentes.</p>
          <Button label="Explorar Coleção" class="mt-6 w-fit p-button-raised" />
        </div>
      </div>

      <div class="lg:col-span-3 flex flex-col gap-4">
        
        <div class="flex-1 relative group overflow-hidden rounded-2xl border border-[#333]">
          <img 
            src="https://images.unsplash.com/photo-1514432324607-a09d9b4aefdd?q=80&w=600&h=100&fit=crop" 
            alt="Promo 1" 
            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
          />
          <div class="absolute inset-0 bg-black/40 flex flex-col items-center justify-center p-4 text-center hover:bg-black/20 transition-all">
            <span class="text-orange-400 text-sm font-bold tracking-widest uppercase mb-2">Equipamentos</span>
            <h3 class="text-white font-bold text-2xl">Moedores Pro</h3>
          </div>
        </div>

        <div class="flex-1 relative group overflow-hidden rounded-2xl border border-[#333]">
          <img 
            src="https://images.unsplash.com/photo-1509042239860-f550ce710b93?q=80&w=600&h=100&fit=crop" 
            alt="Promo 2" 
            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
          />
          <div class="absolute inset-0 bg-black/40 flex flex-col items-center justify-center p-4 text-center hover:bg-black/20 transition-all">
            <span class="text-orange-400 text-sm font-bold tracking-widest uppercase mb-2">Clube de Assinatura</span>
            <h3 class="text-white font-bold text-2xl">Receba em Casa</h3>
          </div>
        </div>

      </div>

    </div>
  </section>
</template>

<script setup lang="ts">
// Adicione aqui qualquer lógica de navegação se necessário
</script>

<style scoped>
/* Garante que o PrimeVue Tag ou outros componentes não quebrem o layout */
:deep(.p-tag) {
  font-family: sans-serif;
}
</style>