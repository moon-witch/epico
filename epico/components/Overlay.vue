<script setup lang="ts">
const emit = defineEmits(['closed'])
const showOverlay = ref(true)

const playAnimation = ref(false)

const closeOverlay = (): void => {
  playAnimation.value= true
  emit('closed')
  setTimeout(() => {
    showOverlay.value = false
    playAnimation.value = false
  }, 1900)
}
</script>

<template>
  <div v-if="showOverlay" class="overlay-wrapper" :class="{'slide-out': playAnimation}">
    <h1>Yo, epico!</h1>
    <h2>It's your birthday, island chief!</h2>
    <button @click="closeOverlay">What's this?</button>
    <h3>(Careful, there might be sound playing)</h3>
  </div>
</template>

<style scoped>
.overlay-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 0;
  bottom: 0;
  height: 100dvh;
  width: 100dvw;
  background-image: url("../public/Screenshot from 2024-09-03 11-50-32.png");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  z-index: 10;
}

.slide-out {
  animation: slide 2s;
}

h1 {
  font-size: 4rem;
}

h2 {
  text-align: center;
  font-size: 2rem;
}

button {
  margin-top: 5rem;
  background: linen;
  border: none;
  border-radius: 5px;
  padding: .5rem 1rem;
  color: #330303;
  font-size: 2rem;
  animation: pulse 1s linear infinite;
  font-family: "Indie Flower", cursive;
  transition: .3s ease-in-out;
  cursor: pointer;
}

button:hover {
  animation: none;
  width: 100%;
  background: indianred;
}

@keyframes pulse {
  0% {
    width: 70%;
    font-size: 1.8rem;
    margin-top: 5rem;
    background: linen;
  }
  50% {
    width: 60%;
    font-size: 2rem;
    margin-top: 7rem;
    background: #c3f7ff;
  }
  100% {
    width: 70%;
    font-size: 1.8rem;
    margin-top: 5rem;
    background: linen;
  }
}

@keyframes slide {
  from {
    top: 0;
  }
  to {
    top: -100dvh;
  }
}
</style>