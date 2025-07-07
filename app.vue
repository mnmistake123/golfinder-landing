<script setup>
useHead({
  htmlAttrs: { lang: "en-US" },
  title: "GolFinder - Encuentra y únete a partidos deportivos cerca",
  meta: [
    {
      name: "description",
      content:
        "GolFinder te permite descubrir partidos deportivos cerca de ti y unirte a juegos con otras personas. Conecta, juega y mantente activo donde estés",
    },
  ],
  bodyAttrs: {
    class: "font-display",
  },
});
</script>

<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
