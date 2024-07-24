<template>
  <div class="max-w-[225px] flex flex-col">
    <img :src="img" class="max-w-[225px] h-full max-h-[256px] w-full object-cover rounded-[20px] " alt="">
    <div class="py-5 rounded-b-lg space-y-1">
      <h3 class="text-white text-[23px] font-semibold font-jakarta">{{ name }}</h3>
      <p class="text-main_dark-300 leading-[20px] text-[16px] font-medium font-jakarta">{{ description }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  img: {
    type: String,
    required: true
  },
  name: {
    type: String,
    required: true
  },
  description: {
    type: String,
    required: true
  },
});
</script>
