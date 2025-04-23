<template>
  <Teleport to="body">
    <Transition name="slide">
      <aside
        v-if="modelValue"
        class="fixed top-0 left-0 w-92 h-full bg-white shadow-lg z-50 pt-15 gap-5 "
      >
        <button
          @click="$emit('update:modelValue', false)"
          class="absolute top-3 right-3 flex items-center justify-center text-black text-2xl hover:bg-gray-100 rounded-4xl w-10 h-10 cursor-pointer z-100"
        >
          <Icon name="material-symbols:close-rounded"></Icon>
        </button>
        <div class="w-full h-full gap-5 flex flex-col overflow-y-scroll
        [&::-webkit-scrollbar]:w-2
  [&::-webkit-scrollbar-track]:bg-white
  [&::-webkit-scrollbar-thumb]:bg-black
  dark:[&::-webkit-scrollbar-track]:bg-white
  dark:[&::-webkit-scrollbar-thumb]:bg-gray-200 ">

          <HeaderSideBarSection category-name="Gaming" ></HeaderSideBarSection>
          <HeaderSideBarSection category-name="Services" ></HeaderSideBarSection>
        </div>
      </aside>
    </Transition>
    <div
      v-if="modelValue"
      class="fixed inset-0 bg-black bg-low-op z-40"
      @click="$emit('update:modelValue', false)"
    ></div>
  </Teleport>
</template>

<script setup>
defineProps({
  modelValue: Boolean,
});
defineEmits(["update:modelValue"]);
</script>

<style scoped>
.slide-enter-from,
.slide-leave-to {
  transform: translateX(-100%);
  opacity: 0;
}
.slide-enter-to,
.slide-leave-from {
  transform: translateX(0);
  opacity: 1;
}
.slide-enter-active,
.slide-leave-active {
  transition: all 0.4s ease-in-out;
}
.bg-low-op {
  background: #00000073;
}

</style>
