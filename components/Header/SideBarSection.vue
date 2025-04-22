<template>

<section class="w-full flex flex-col gap-4 ">
          <button @click="isDropped = !isDropped" class="text-black flex items-center w-full justify-between px-5 cursor-pointer hover:bg-gray-100">
            <h2 class="">
              {{ props.categoryName }}
            </h2>
            
            <Icon v-if="!isDropped" class="text-2xl" name="ri:arrow-drop-right-line"></Icon>
            <Icon v-if="isDropped" class="text-2xl" name="ri:arrow-drop-down-line"></Icon>
        </button>
          <Transition name="drop" @before-enter="beforeEnter" @enter="enter" @leave="leave">

            <ul v-if="isDropped" :ref="dropdown" class="text-black  bg-gray-200 flex flex-col items-center p-2 gap-5 h-auto" >
              <li v-for="(Subcategory,index) in props.subcategories" :key="index" class=""><p> {{ Subcategory }} </p></li>
              
          </ul>
        </Transition>
        </section>
</template>

<script setup>

const props = defineProps({
    categoryName : {
        default : "category",
        type : String,
    },
    subcategories : {
        type : Array,
        default : [
            "sub 1",
            "sub 2",
            "sub 3",
            "sub 4",
            "sub 5",
            "sub 6",
            "sub 7",
        ]

    }
})

const isDropped = ref(false);

const dropdown = ref(null)

function beforeEnter(el) {
  el.style.height = '0'
}

function enter(el) {
  const height = el.scrollHeight
  el.style.transition = 'height 0.4s ease'
  requestAnimationFrame(() => {
    el.style.height = height + 'px'
  })
}

function leave(el) {
  el.style.height = el.scrollHeight + 'px'
  el.style.transition = 'height 0.4s ease'
  requestAnimationFrame(() => {
    el.style.height = '0'
  })
}

</script>
<style>

.drop-enter-from,.drop-leave-to{

   height: 0;
    opacity: 0;
    /* z-index: -20; */
}
.drop-enter-active,.drop-leave-active{
    transition: all .5s ease-in-out;
}
</style>