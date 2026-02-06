<script setup>
import { ref } from 'vue';

const products = ref([
  {
    id: 1,
    name: "Fazenda Santa Maria",
    region: "Sul de Minas",
    altitude: "1.200m",
    variety: "Arábica - Catuaí Amarelo",
    process: "Natural",
    sca_score: 86,
    roast_level: "Média",
    notes: ["Chocolate", "Caramelo", "Nozes"],
    price: 65.00,
    weight: "250g",
    image: "https://images.unsplash.com/photo-1559056199-641a0ac8b55e?q=80&w=500",
    in_stock: true
  },
  {
    id: 2,
    name: "Sítio das Flores",
    region: "Mogiana Paulista",
    altitude: "1.150m",
    variety: "Bourbon Amarelo",
    process: "Cereja Descascado",
    sca_score: 84,
    roast_level: "Clara",
    notes: ["Frutas Amarelas", "Acidez Cítrica", "Mel"],
    price: 72.00,
    weight: "250g",
    image: "https://images.unsplash.com/photo-1580915411954-282cb1b0d780?q=80&w=500",
    in_stock: true
  },
  {
    id: 3,
    name: "Reserva do Produtor",
    region: "Cerrado Mineiro",
    altitude: "1.000m",
    variety: "Mundo Novo",
    process: "Natural",
    sca_score: 82,
    roast_level: "Média-Escura",
    notes: ["Cacau", "Encorpado", "Finalização Longa"],
    price: 58.00,
    weight: "250g",
    image: "https://images.unsplash.com/photo-1611854779393-1b2da9d400fe?q=80&w=500",
    in_stock: false
  },
  {
    id: 4,
    name: "Grão de Ouro",
    region: "Espírito Santo",
    altitude: "1.300m",
    variety: "Catuaí Vermelho",
    process: "Honey Process",
    sca_score: 88,
    roast_level: "Média-Clara",
    notes: ["Frutas Vermelhas", "Vinho", "Açúcar Mascavo"],
    price: 89.90,
    weight: "250g",
    image: "https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?q=80&w=500",
    in_stock: true
  },
  {
    id: 1,
    name: "Fazenda Santa Maria",
    region: "Sul de Minas",
    altitude: "1.200m",
    variety: "Arábica - Catuaí Amarelo",
    process: "Natural",
    sca_score: 86,
    roast_level: "Média",
    notes: ["Chocolate", "Caramelo", "Nozes"],
    price: 65.00,
    weight: "250g",
    image: "https://images.unsplash.com/photo-1559056199-641a0ac8b55e?q=80&w=500",
    in_stock: true
  },
  {
    id: 2,
    name: "Sítio das Flores",
    region: "Mogiana Paulista",
    altitude: "1.150m",
    variety: "Bourbon Amarelo",
    process: "Cereja Descascado",
    sca_score: 84,
    roast_level: "Clara",
    notes: ["Frutas Amarelas", "Acidez Cítrica", "Mel"],
    price: 72.00,
    weight: "250g",
    image: "https://images.unsplash.com/photo-1580915411954-282cb1b0d780?q=80&w=500",
    in_stock: true
  },
  {
    id: 3,
    name: "Reserva do Produtor",
    region: "Cerrado Mineiro",
    altitude: "1.000m",
    variety: "Mundo Novo",
    process: "Natural",
    sca_score: 82,
    roast_level: "Média-Escura",
    notes: ["Cacau", "Encorpado", "Finalização Longa"],
    price: 58.00,
    weight: "250g",
    image: "https://images.unsplash.com/photo-1611854779393-1b2da9d400fe?q=80&w=500",
    in_stock: false
  },
  {
    id: 4,
    name: "Grão de Ouro",
    region: "Espírito Santo",
    altitude: "1.300m",
    variety: "Catuaí Vermelho",
    process: "Honey Process",
    sca_score: 88,
    roast_level: "Média-Clara",
    notes: ["Frutas Vermelhas", "Vinho", "Açúcar Mascavo"],
    price: 89.90,
    weight: "250g",
    image: "https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?q=80&w=500",
    in_stock: true
  }
]);

const formatCurrency = (value) => {
  return value.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
};
// --- Lógica de Filtro ---
const selectedCategory = ref('Todos');
const categories = ref(['Todos', 'SCA 85+', 'Torra Clara', 'Torra Média', 'Promoções']);

const filteredProducts = computed(() => {
  if (selectedCategory.value === 'Todos') return products.value;
  
  if (selectedCategory.value === 'SCA 85+') {
    return products.value.filter(p => p.sca_score >= 85);
  }
  if (selectedCategory.value === 'Torra Clara') {
    return products.value.filter(p => p.roast_level.includes('Clara'));
  }
  if (selectedCategory.value === 'Torra Média') {
    return products.value.filter(p => p.roast_level === 'Média');
  }
  if (selectedCategory.value === 'Promoções') {
    return products.value.filter(p => p.price < 60);
  }
  return products.value;
});


</script>
<template>
  <div class="m-5 min-h-screen mt-7">
    
    <div class="flex flex-col md:flex-row justify-between items-center mb-10 gap-4 border-b border-[#3a2216]/10 pb-6">
      <h2 class="text-4xl font-serif text-[#3a2216] m-0 font-bold">Micro-lotes</h2>
      
      <div class="flex flex-wrap gap-2">
        <button 
          v-for="cat in categories" :key="cat"
          @click="selectedCategory = cat"
          :class="[
            'px-5 py-2 rounded-full text-xs font-bold uppercase tracking-wider transition-all duration-300 border',
            selectedCategory === cat 
              ? 'bg-[#3a2216] text-[#f2e4d3] border-[#3a2216] shadow-md' 
              : 'bg-white/50 text-[#3a2216] border-[#3a2216]/20 hover:border-[#3a2216] hover:bg-white'
          ]"
        >
          {{ cat }}
        </button>
      </div>
    </div>
    
    <DataView :value="filteredProducts" layout="grid">
      <template #grid="slotProps">
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8 p-2">
          <div v-for="(item, index) in slotProps.items" :key="index">
            
            <div class="bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-500 border border-black/5 h-full flex flex-col">
              
              <div class="relative overflow-hidden aspect-[4/5]">
                <img :src="item.image" :alt="item.name" class="w-full h-full object-cover transition-transform duration-700 hover:scale-110" />
                
                <div class="absolute top-4 right-4">
                  <div class="bg-[#A67C52] text-white px-3 py-1 rounded-md shadow-lg flex flex-col items-center justify-center">
                    <span class="text-[10px] uppercase font-bold leading-none opacity-80">Score</span>
                    <span class="text-sm font-black">{{ item.sca_score }}</span>
                  </div>
                </div>

                <div v-if="!item.in_stock" class="absolute inset-0 bg-black/40 backdrop-blur-[1px] flex items-center justify-center">
                   <span class="bg-white text-black px-4 py-1 text-xs font-black uppercase tracking-widest rounded">Esgotado</span>
                </div>
              </div>

              <div class="p-5 flex flex-col flex-grow bg-white">
                <div class="flex justify-between items-start mb-1">
                  <h3 class="text-xl font-serif font-bold text-[#3a2216] leading-tight">{{ item.name }}</h3>
                </div>
                
                <div class="flex items-center gap-1 text-[#A67C52] text-[10px] font-bold uppercase tracking-widest mb-4">
                  <i class="pi pi-map-marker text-[10px]"></i>
                  <span>{{ item.region }}</span>
                </div>

                <div class="flex flex-wrap gap-1 mb-6">
                  <span 
                    v-for="note in item.notes.slice(0, 3)" :key="note"
                    class="bg-[#f2e4d3] text-[#3a2216] text-[9px] px-2 py-1 rounded font-bold border border-[#3a2216]/5"
                  >
                    {{ note }}
                  </span>
                </div>

                <div class="mt-auto pt-4 border-t border-gray-100">
                  <div class="flex justify-between items-end">
                    <div class="flex flex-col">
                      <span class="text-[10px] text-gray-400 font-bold uppercase tracking-tighter">Variedade: {{ item.variety }}</span>
                      <span class="text-2xl font-black text-[#3a2216] mt-1">{{ formatCurrency(item.price) }}</span>
                    </div>
                    <span class="text-[10px] text-gray-400 font-bold mb-1">{{ item.weight }}</span>
                  </div>
                </div>

                <button 
                  class="w-full mt-5 py-3 rounded-xl font-bold text-xs tracking-widest transition-all duration-300 flex items-center justify-center gap-2"
                  :class="item.in_stock 
                    ? 'bg-[#3a2216] text-white hover:bg-[#5d3a2a] shadow-md hover:shadow-lg' 
                    : 'bg-gray-100 text-gray-400 cursor-not-allowed'"
                  :disabled="!item.in_stock"
                >
                  <i class="pi pi-shopping-bag text-sm"></i>
                  ADICIONAR
                </button>
              </div>
            </div>

          </div>
        </div>
      </template>
    </DataView>
  </div>
</template>

<style scoped>
/* Removi o componente Card do PrimeVue e usei Divs para controle total do design */
.font-serif {
  font-family: 'Playfair Display', serif; /* Ou a fonte do seu logo */
}
</style>