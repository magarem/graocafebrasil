<template>
  <section class="py-16 px-5 bg-[#f2e4d3]">
    <div class="max-w-[1500px] mx-auto">
      
      <div class="mb-12 border-b border-[#3a2216]/10 pb-6">
        <h2 class="text-4xl font-serif text-[#3a2216] font-bold">Nossos Produtores</h2>
        <p class="text-[#A67C52] font-medium uppercase tracking-widest text-sm mt-2">
          As mãos por trás de cada grão especial
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        
        <div v-for="producer in producers" :key="producer.id" 
             class="group relative bg-white rounded-3xl overflow-hidden shadow-sm hover:shadow-2xl transition-all duration-500 border border-black/5 flex flex-col md:flex-row h-full md:h-[350px]">
          
          <div class="md:w-1/2 overflow-hidden relative">
            <img :src="producer.image" :alt="producer.name" 
                 class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110" />
            <div class="absolute bottom-4 left-4">
              <span class="bg-black/60 backdrop-blur-md text-white text-[10px] px-3 py-1 rounded-full uppercase font-bold tracking-widest">
                <i class="pi pi-map-marker mr-1"></i>{{ producer.location }}
              </span>
            </div>
          </div>

          <div class="md:w-1/2 p-8 flex flex-col justify-center bg-white">
            <h3 class="text-2xl font-serif font-bold text-[#3a2216] mb-2">{{ producer.farm }}</h3>
            <h4 class="text-[#A67C52] font-bold text-sm uppercase tracking-tighter mb-4">Produtor: {{ producer.name }}</h4>
            
            <p class="text-gray-600 text-sm leading-relaxed mb-6 line-clamp-3">
              "{{ producer.story }}"
            </p>

            <div class="mt-auto flex items-center justify-between border-t border-gray-100 pt-4">
              <div class="flex flex-col">
                <span class="text-[10px] text-gray-400 font-bold uppercase">Altitude</span>
                <span class="text-lg font-bold text-[#3a2216]">{{ producer.altitude }}</span>
              </div>
              <NuxtLink :to="`/produtores/${producer.id}`" 
                        class="text-[#3a2216] font-bold text-xs uppercase border-b-2 border-[#A67C52] pb-1 hover:text-[#A67C52] transition-colors">
                Ver História
              </NuxtLink>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const producers = ref([
  {
    id: 1,
    name: "Seu Sebastião",
    farm: "Fazenda Ouro Verde",
    location: "Carmo de Minas, MG",
    altitude: "1.250m",
    story: "Com mais de 40 anos dedicados ao café, Sebastião é pioneiro em processos naturais na região, focando na doçura extrema dos frutos.",
    image: "https://www.portalvaledocafe.com.br/images/tourexperiencia/produto2/capa.jpg" // Foto representando produtor/fazenda
  },
  {
    id: 2,
    name: "Dona Maria Helena",
    farm: "Sítio Vista Alegre",
    location: "Mogiana, SP",
    altitude: "1.100m",
    story: "Maria Helena lidera uma cooperativa feminina focada em variedades exóticas e sustentabilidade, produzindo cafés com notas florais únicas.",
    image: "https://www.conceicaodocastelo.es.gov.br/uploads/images/11425447_454963417998298_1375370185717733950_n.jpg"
  },
  {
    id: 3,
    name: "Ricardo & Família",
    farm: "Chácara Santa Fé",
    location: "Cerrado Mineiro",
    altitude: "1.050m",
    story: "A família trabalha unida no manejo preciso do solo, resultando em cafés encorpados com notas marcantes de chocolate e avelã.",
    image: "produtor_cafe.png"
  },
  {
    id: 4,
    name: "João Silva",
    farm: "Veredas do Sol",
    location: "Espírito Santo",
    altitude: "1.400m",
    story: "Especialista em colheita tardia, João produz alguns dos cafés mais pontuados da região das montanhas capixabas.",
    image: "https://rondonia.ro.gov.br/wp-content/uploads/2017/03/Abilio-God%C3%AAncio-Visita-Alvorada-Caf%C3%A9_-Foto-Dhiony-Costa-e-Silva.jpg"
  }
]);
</script>

<style scoped>
.line-clamp-3 {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>