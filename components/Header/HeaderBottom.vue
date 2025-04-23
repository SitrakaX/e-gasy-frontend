<template>
  <div class="w-full h-1/3 bg-white border-t-2 flex items-center px-2 max-[1100px]:hidden">
    <button
      @click="isShowed = true"
      class="flex items-center justify-center gap-2 text-blue-950 text-xl w-1/6 cursor-pointer hover:bg-gray-100 p-2 transition-all"
    >
      <Icon name="fluent:align-left-16-regular" class="text-xl"></Icon>
      <p class="">all categories</p>
    </button>
    <ul class="flex items-center w-4/6 justify-around text-black h-full ">
      <li class="h-full flex items-center hover:border-b-2 cursor-pointer">
        category 1
      </li>
      <li class="h-full flex items-center hover:border-b-2 cursor-pointer">
        category 2
      </li>
      <li class="h-full flex items-center hover:border-b-2 cursor-pointer">
        category 3
      </li>
      <li class="h-full flex items-center hover:border-b-2 cursor-pointer">
        category 4
      </li>
      <li class="h-full flex items-center hover:border-b-2 cursor-pointer">
        category 5
      </li>
      <li
        class="border-b-2 h-full flex items-center hover:border-b-2 cursor-pointer"
      >
        category 6
      </li>
      <li class="h-full flex items-center hover:border-b-2 cursor-pointer">
        category 7
      </li>
    </ul>
        <HeaderSideBar v-model="isShowed" ></HeaderSideBar>

      
  </div>
</template>
<script setup>
const isShowed = ref(false);

const setIsShowed = async () => {
  isShowed.value = !isShowed.value;
};
</script>

