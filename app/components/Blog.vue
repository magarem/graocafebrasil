<template>
  <section class="py-2 px-5 bg-transparent">
    <div class="max-w-[1500px] mx-auto">
      
      <div class="mb-12 border-b border-[#3a2216]/10 pb-6 flex justify-between items-end">
        <div>
          <h2 class="text-4xl font-serif text-[#3a2216] font-bold">Conteúdo & Cultura</h2>
          <p class="text-[#A67C52] font-medium uppercase tracking-widest text-sm mt-2">
            Aprenda mais sobre o universo dos cafés especiais
          </p>
        </div>
        <NuxtLink to="/blog" class="hidden md:block text-[#3a2216] font-bold text-sm uppercase border-b-2 border-[#A67C52] pb-1 hover:opacity-70 transition-all">
          Ver todos os artigos
        </NuxtLink>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-10">
        
        <article v-for="post in posts" :key="post.id" 
                 class="group cursor-pointer">
          
          <div class="relative overflow-hidden rounded-2xl aspect-video mb-6 shadow-sm group-hover:shadow-xl transition-all duration-500">
            <img :src="post.image" :alt="post.title" 
                 class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
            <div class="absolute top-4 left-4">
              <span class="bg-[#3a2216] text-[#f2e4d3] text-[10px] px-3 py-1 rounded-full uppercase font-bold tracking-widest">
                {{ post.category }}
              </span>
            </div>
          </div>

          <div class="space-y-3">
            <div class="flex items-center gap-4 text-xs text-gray-400 font-bold uppercase tracking-tighter">
              <span>{{ post.date }}</span>
              <span class="w-1 h-1 bg-[#A67C52] rounded-full"></span>
              <span>Por {{ post.author }}</span>
            </div>
            
            <h3 class="text-3xl font-serif font-bold text-[#3a2216] group-hover:text-[#A67C52] transition-colors duration-300 leading-tight">
              {{ post.title }}
            </h3>
            
            <p class="text-gray-600 leading-relaxed line-clamp-2">
              {{ post.excerpt }}
            </p>

            <NuxtLink :to="`/blog/${post.id}`" class="inline-flex items-center gap-2 text-[#3a2216] font-black text-sm uppercase tracking-widest group-hover:gap-4 transition-all duration-300 mt-4">
              Ler artigo completo 
              <i class="pi pi-arrow-right text-xs text-[#A67C52]"></i>
            </NuxtLink>
          </div>
        </article>

      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const posts = ref([
  {
    id: 1,
    title: "Como identificar notas sensoriais no seu café matinal",
    excerpt: "Você sabia que o café pode ter notas de frutas vermelhas, chocolate ou até flores? Aprenda a treinar seu paladar para descobrir a complexidade dos grãos especiais.",
    category: "Guia de Preparo",
    date: "05 Fev, 2026",
    author: "Mestre Torrador",
    image: "https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?q=80&w=1200"
  },
  {
    id: 2,
    title: "A importância da moagem correta para cada método",
    excerpt: "Do Espresso à Prensa Francesa, o tamanho do grão moído muda tudo. Descubra como ajustar seu moedor para extrair o melhor sabor de cada café.",
    category: "Dicas Técnicas",
    date: "01 Fev, 2026",
    author: "Barista Pro",
    image: "https://images.unsplash.com/photo-1559056199-641a0ac8b55e?q=80&w=1200"
  }
]);
</script>

<style scoped>
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>