<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
<style>
body {
  background-color: #fae9d7;
  color: #f3f4f6;
  margin: 40px;
}

/* Se estiver usando PrimeVue, remova as bordas brancas dos cards */
.p-card {
  background: #242426 !important;
  color: #fff !important;
  border: 1px solid #333;
}

.p-dataview .p-dataview-content {
  background: transparent !important;
}
</style>