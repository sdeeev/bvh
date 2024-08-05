<template>
  <div class=" flex flex-col w-auto max-w-[219px] bg-[#2E2C2C] rounded-2xl relative ">
    <NuxtLink to="" class="flex justify-start rounded-2xl w-[219px] h-[187px]">
      <div class="absolute w-full h-full top-0 left-0 rounded-2xl bg-gradient-to-t from-[#000000] via-[#23212199] to-transparent z-10"></div>
      <Icon name="media/update" class="absolute right-4 top-3 text-xl"/>
      <div class="grid  grid-cols-[39px_1fr_1fr] gap-2 overflow-hidden w-full h-full pt-4 px-4 rounded-2xl ">
        <div class="flex flex-col gap-3 h-full ">
          <img class="w-full h-[51px] rounded-lg object-cover" :src="avatarsImages[6]" alt="">
          <img class="w-full h-[43px] rounded-lg object-cover" :src="avatarsImages[7]" alt="">
          <img class="w-full h-[51px] rounded-lg object-cover" :src="avatarsImages[7]" alt="">
        </div>
        <div class="flex flex-col gap-3 h-full">
          <img class="w-full h-11 rounded-lg object-cover" :src="avatarsImages[0]" alt="">
          <img class="w-full h-11 rounded-lg object-cover" :src="avatarsImages[1]" alt="">
          <img class="w-full h-17 rounded-lg object-cover" :src="avatarsImages[2]" alt="">
        </div>
        <div class="flex flex-col gap-3 h-full">
          <img class="w-full h-11 rounded-lg object-cover" :src="avatarsImages[3]" alt="">
          <img class="w-full h-[68px] rounded-lg object-cover" :src="avatarsImages[4]" alt="">
          <img class="w-full h-[68px] rounded-lg object-cover" :src="avatarsImages[5]" alt="">
        </div>
      </div>

    </NuxtLink>
    <div class="flex  flex-col items-center gap-y-1.5 relative bg-main-dark-800">
      <h1 class="text-[16px] text-white font-jakarta font-bold leading-6">Facebook</h1>

      <div class="flex items-center text-main-dark-500 gap-x-3 font-light">
        <div class="flex items-center gap-x-2">
          <Icon name="media/gallery" class="size-3  text-sm content-center"/>
          <span class="text-xs ">782,818</span>
        </div>
        <div class="h-2.5 w-[0.5px] bg-main-dark-500"></div>
        <div class="flex items-center gap-x-2">
          <Icon name="media/video" class="size-3 text-sm content-center"/>
          <span class="text-xs">291,928</span>
        </div>
      </div>

      <div class="text-2xs text-main-dark-400 font-jakarta font-light leading-normal">
        Last Update : 25/10/2024 16:05 PM
      </div>
    </div>
  </div>

</template>

<script setup>
import {Icon} from "@/components";

const props = defineProps({
  data: {
    type: Array,
    default: () => []
  },
  groupId: {
    type: String
  }
})


const avatarsImages = computed(() => {
  const images = props.data?.filter(avatar => avatar.medium.length > 0 && avatar.medium?.find(image => image.is_primary)).map((avatar => {
    return avatar.medium?.find(image => image.is_primary)?.url
  }))
  while (images.length < 13) {
    const index = Math.floor(Math.random() * (13));
    images.push(`/_nuxt/assets/images/avatars/avatars/avatar${index}.jpg`)
  }
  return images
})


</script>

<style scoped>
/*.bg-gradient-custom {
  border-radius: 15px;
  background: linear-gradient(180deg, rgba(0, 0, 0, 0.00)0.09%, #23212199.91%);
  !*
  background: linear-gradient(180deg, rgba(0, 0, 0, 0.00) 0.09%, #232121 99.91%);
  *!
}

.bg-gradient-custom2 {
  background: linear-gradient(180deg, #232121 0%, #000000 100%);
}*/
</style>
<!-- TODO: add border to img -->
