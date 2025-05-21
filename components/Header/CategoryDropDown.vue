<template>
  <div
    v-for="(subcategory, index) in props.subcategory"
    :key="index"
    class="p-3"
  >
    <h3 class="font-bold">{{ subcategory.name }}</h3>
    <ul class="">
      <li
        v-for="(subsubcategory, index) in subcategory.subsubcategories"
        :key="index"
        class=""
      >
        <p>{{ subsubcategory.name }}</p>
      </li>
    </ul>
  </div>
</template>

<script setup>
const props = defineProps({
  subcategory: Array,
});
//defineEmits(["update:modelValue"])
</script>
