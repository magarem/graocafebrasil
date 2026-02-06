<template>
  <header
    v-if="settings?.data?.topbar"
    class="fixed top-0 left-0 w-full z-50 transition-all duration-300"
    :class="{
      'bg-[#f2e4d3] shadow-sm': !scrolled,   
      'bg-[#f2e4d3] shadow-md': scrolled
    }"
    :style="{ color: mainColor }"
  >
    <div class="flex items-center py-3 px-5 md:px-8 max-w-[1800px] mx-6">
      
      <div class="flex-1 flex justify-start items-center">
        <nav class="hidden lg:flex items-center space-x-6">
          <template v-for="(item, index) in settings.data.topbar.menu" :key="index">
            <div v-if="item.sub && item.sub.length > 0" class="relative group/dropdown py-4">
              <button class="flex items-center text-[18px] font-serif font-medium hover:opacity-70 transition-opacity gap-1">
                {{ item.name }}
                <i class="fas fa-chevron-down text-[10px] opacity-70 mt-1"></i>
              </button>
              <div class="absolute left-0 top-full pt-2 opacity-0 invisible group-hover/dropdown:opacity-100 group-hover/dropdown:visible transition-all duration-300 transform origin-top">
                <div class="bg-[#fdfcf0] rounded shadow-xl border border-[#d1b253]/20 py-2 min-w-[200px]">
                  <NuxtLink v-for="(subItem, subIndex) in item.sub" :key="subIndex" :to="resolveLink(subItem.link)" class="block px-6 py-2 text-md font-serif text-[#431407] hover:bg-[#f9d7c0]/30">
                    {{ subItem.name }}
                  </NuxtLink>
                </div>
              </div>
            </div>
            <NuxtLink v-else :to="resolveLink(item.link)" class="relative text-[22px] font-serif font-medium tracking-tight group/link whitespace-nowrap">
              {{ item.name }}
              <span class="absolute -bottom-1 left-0 w-0 h-[2px] transition-all duration-300 bg-black opacity-40 group-hover/link:w-full"></span>
            </NuxtLink>
          </template>
        </nav>
      </div>

      <div class="flex-none flex justify-center z-50 mx-4">
        <NuxtLink to="/" class="group flex flex-col items-center no-underline">
          <div class="inline-flex flex-col items-center border border-[#A67C52] p-2 md:p-3 rounded-lg bg-[#2C241F] shadow-lg">
            <h1 class="text-xl md:text-2xl font-serif font-bold text-[#FDFBF7] tracking-tight">
              Gran Café <span class="italic text-[#A67C52]">Brasil</span>
            </h1>
            <p class="text-[7px] md:text-[8px] uppercase tracking-[0.3em] text-[#FDFBF7]/60 mt-1">
              Origin Selection • Est. 2026
            </p>
          </div>
        </NuxtLink>
      </div>

      <div class="flex-1 flex justify-end items-center gap-4 md:gap-6 relative z-50">
        
        <div class="hidden sm:flex items-center relative">
          <input 
            type="text" 
            placeholder="Buscar cafés..." 
            class="bg-white/50 border border-[#A67C52]/30 rounded-full py-1.5 px-4 pl-10 text-sm focus:outline-none focus:ring-1 focus:ring-[#A67C52] w-40 md:w-64 transition-all"
          />
          <i class="fas fa-search absolute left-3 text-[#A67C52] text-xs"></i>
        </div>

        <div class="flex items-center gap-4">
          <NuxtLink to="/account" class="hover:text-[#A67C52] transition-colors">
            <i class="far fa-user text-xl"></i>
          </NuxtLink>

          <NuxtLink to="/checkout" class="relative hover:text-[#A67C52] transition-colors">
            <i class="fas fa-shopping-bag text-xl"></i>
            <span class="absolute -top-2 -right-2 bg-[#A67C52] text-white text-[10px] font-bold w-4 h-4 flex items-center justify-center rounded-full">
              0
            </span>
          </NuxtLink>
        </div>

        <div class="lg:hidden">
          <button @click="toggleMenu" class="focus:outline-none ml-2">
            <i v-if="!menuOpen" class="fas fa-bars text-xl"></i>
            <i v-else class="fas fa-times text-xl"></i>
          </button>
        </div>
      </div>

    </div>
  </header>
</template>
<script setup lang="ts">
// (O seu script pode continuar exatamente igual, não precisa mudar nada nele)
import { ref, onMounted, onBeforeUnmount, computed, watchEffect } from 'vue'

const mainColor = 'black'
const menuOpen = ref(false)
const scrolled = ref(false)
const activeMobileSubmenu = ref<number | null>(null)
import { useRoute } from 'vue-router' // Importe o useRoute

const route = useRoute()
const isPreview = computed(() => route.query.preview === 'true')

// 2. Define o caminho do arquivo baseado no modo
const settingsPath = computed(() => {
  return isPreview.value 
    ? 'content/settings.toml' 
    : 'data/settings.json'
})

// 3. Faz a busca na API passando o path dinâmico
const { data: settings, refresh } = await useFetch('/api/readfile', {
    params: { path: settingsPath.value },
    lazy: true,
    server: false,
    watch: [settingsPath] // Reexecuta se o path mudar (ex: ao entrar/sair do preview)
})

watchEffect(() => {
  if (!settings.value) {
    console.warn("Aviso: settings.md não encontrado ou vazio.")
  }
})

console.log('TopBar settings:', settings.value)

const topbar = computed(() => {
  // 1. Tenta pegar direto da raiz (Padrão novo do useSmartContent)
  if (settings.value?.topbar) return settings.value.topbar
  
  // 2. Tenta pegar de 'meta' (caso o frontmatter esteja aninhado)
  if (settings.value?.data?.topbar) return settings.value.data.topbar
  
  // 3. Fallback se não encontrar nada
  return {
    logo: { img: '', link: '/' },
    menu: []
  }
})

const resolveLink = (link: string) => {
  if (!link) return '#'
  
  // 1. Se for uma âncora pura (ex: #catalogo), retorna direto
  if (link.startsWith('#')) return link

  // 2. Limpeza padrão de caracteres e extensões
  let cleanLink = link.replace(/:/g, '/').replace('_index', '').replace('.md', '')

  // 3. Garante que comece com / se não for link externo
  if (!cleanLink.startsWith('/') && !cleanLink.startsWith('http')) {
    cleanLink = '/' + cleanLink
  }

  // 4. REMOVE a barra final APENAS se não houver uma âncora no link
  // Isso evita que /#catalogo vire /#catalog (quebraria a âncora)
  if (!cleanLink.includes('#')) {
    if (cleanLink.length > 1 && cleanLink.endsWith('/')) {
      cleanLink = cleanLink.slice(0, -1)
    }
  }

  return cleanLink
}

const toggleMenu = () => { menuOpen.value = !menuOpen.value }
const toggleMobileSubmenu = (index: number) => {
  activeMobileSubmenu.value = activeMobileSubmenu.value === index ? null : index
}

const onScroll = () => { scrolled.value = window.scrollY > 50 }

onMounted(() => { window.addEventListener('scroll', onScroll) })
onBeforeUnmount(() => { window.removeEventListener('scroll', onScroll) })
</script>