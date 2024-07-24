<template>
  <div class="bg-main_dark-800 max-w-[285px] ps-4 max-h-[475px] h-full rounded-[10px] overflow-hidden">
    <h1 class="text-xl text-white font-bold py-4 font-jakarta">Profile</h1>
    <div class="relative">
      <div class="overflow-hidden h-[256px]">
        <div class="flex transition-transform duration-300 ease-in-out"
             :style="{ transform: `translateX(-${currentSlide * 80}%)` }">
          <div v-for="(slide, index) in profiles" :key="index" class="w-[90%] flex-shrink-0 mr-[5%] relative">
            <img :src="slide.image" class="w-[225px] h-[256px] object-cover rounded-[20px]" :alt="slide.name">
            <div v-if="index === getNextIndex()" class="absolute inset-0 bg-black bg-opacity-50 rounded-[20px]"></div>
          </div>
        </div>
      </div>

      <div class="py-5 rounded-b-lg space-y-1">
        <h3 class="text-white text-[23px] font-semibold font-jakarta">{{ currentProfile.name }}</h3>
        <p class="text-main_dark-300 leading-[20px] text-[16px] font-medium font-jakarta">{{ currentProfile.description }}</p>
      </div>
      <div class="absolute top-[35%] z-10 flex justify-between w-full -translate-y-1/2 max-w-[225px] ">
        <button
            class="h-[35px] w-[35px] bg-[#232121]/60 backdrop-grayscale-0 border border-main_dark-700 text-white px-3 py-1 rounded-[5px] flex justify-center items-center"
            @click="prevProfile"
        >
          <Icon name="prev" class="text-[10px]"/>
        </button>
        <button
            class="h-[35px] w-[35px] bg-[#232121]/60 backdrop-grayscale-0 border border-main_dark-700 text-white px-3 py-1 rounded-[5px] flex justify-center items-center"
            @click="nextProfile"
        >
          <Icon name="next" class="text-[12px]"/>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import { Icon } from '~/components';
import cr7 from 'assets/images/cr7.png';

const currentSlide = ref(0);

const profiles = ref([
  {
    name: 'Cristiano Ronaldo',
    description: 'Football Player',
    image: cr7
  },
  {
    name: 'Messi',
    description: 'Football Player',
    image: cr7
  },  {
    name: 'Messi2',
    description: 'Football Player',
    image: cr7
  },  {
    name: 'Messi3',
    description: 'Football Player',
    image: cr7
  },  {
    name: 'Messi4',
    description: 'Football Player',
    image: cr7
  },
]);

const currentProfile = computed(() => profiles.value[currentSlide.value]);

const nextProfile = () => {
  currentSlide.value = (currentSlide.value + 1) % profiles.value.length;
};

const prevProfile = () => {
  currentSlide.value = (currentSlide.value - 1 + profiles.value.length) % profiles.value.length;
};

const getNextIndex = () => {
  return (currentSlide.value + 1) % profiles.value.length;
};
</script>
