<script setup lang="ts">
useHead({
  link: [
    { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
    { rel: 'preconnect', href: 'https://fonts.gstatic.com', crossorigin: 'anonymous' },
    { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css2?family=Indie+Flower&display=swap' }
  ]
})
</script>

<template>
  <div>
    <NuxtPage></NuxtPage>
  </div>
</template>

<style>
.indie-flower-regular {
  font-family: "Indie Flower", cursive;
  font-weight: 400;
  font-style: normal;
}

:root {
  background: #0a0000;
  font-family: "Indie Flower", cursive;
  color: linen;
  height: 100dvh;
  overflow: hidden;
}

html, body {
  margin: 0;
  padding: 0;
}
</style>
