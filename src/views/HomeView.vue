<script setup lang="ts">
import MainMenu from '@/components/MainMenu.vue';
import menuBg from '@/assets/rocket-bg.png';
import splashBg from '@/assets/splash-bg.png';
import splashLogo from '@/assets/splash-logo.png';
import Footer from '@/components/Footer.vue';
import FriendsButton from '@/components/FriendsButton.vue';
import { onMounted, ref } from 'vue';

const showMenuScreen = ref(false);
const startFlashing = ref(false);

const enterGame = () => {
  showMenuScreen.value = true;
}

onMounted(() => {
  setTimeout(() => {
    startFlashing.value = true;
  }, 2800);
})

</script>

<template>
  <div :style="`background-image: url(${showMenuScreen ? menuBg : splashBg});`" :class="`h-[100vh] bg bg-center bg-cover`" @click="enterGame">
    <div v-if="!showMenuScreen">
      <div class="flex items-center justify-center h-[100vh]">
        <img class="fade-in-down opacity-0 w-[80vw] h-[auto] mb-[200px]" :src="splashLogo" />
      </div>
  
      <div :class="`font-[1000] uppercase text-sky-500 electrolize-bold text-5xl absolute bottom-[300px] text-center w-[100%] slide-up ${startFlashing ? 'pulse-shadow' : 'custom-shadow'}`">
        Don't Pause, Press Play
      </div>
    </div>
    <Transition>
      <div v-if="showMenuScreen">
        <MainMenu />
    
        <FriendsButton />
    
        <Footer />
      </div>
    </Transition>
  </div>
</template>

<style scoped>
.bg {
  transition-property: background-image;
  transition-duration: .2s;
  transition-behavior: allow-discrete;
}

.slide-up {
  animation: slideUp 2s forwards;
}

@keyframes slideUp {
  from {
    transform: translate3d(0, 300px, 0);
  }
  to {
    transform: translate3d(0,0,0);
  }
}

.fade-in-down {
  animation: fadeInDown 2s forwards;
  animation-delay: 2s;
}

@keyframes fadeInDown {
  0% {
    transform: translate3d(0, -200px, 0);
    opacity: 0;
  }
  100% {
    transform: translate3d(0,0,0);
    opacity: 100;
  }
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.custom-shadow {
  filter: drop-shadow(0px 0px 12px #000000);
}

.pulse-shadow {
  animation: pulseShadow 2.5s ease-in-out infinite;
}

@keyframes pulseShadow {
  0% {
    filter: drop-shadow(0px 0px 12px #000000);
    color: #0ea5e9;
  }
  30% {
    filter: drop-shadow(0px 0px 16px #C1E3EE);
    color: #e0f2fe; 
  }
  60% {
    filter: drop-shadow(0px 0px 16px #C1E3EE);
    color: #e0f2fe; 
  }
  100% {
    filter: drop-shadow(0px 0px 12px #000000);
    color: #0ea5e9;
  }
}

</style>
