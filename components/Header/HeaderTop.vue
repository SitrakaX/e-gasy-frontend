<template>
  <div class="bg-black w-full h-1/4 flex items-center justify-around px-1">
    <div class="w-70 flex gap-1.5 items-center">
      <Icon
        name="fluent:vehicle-truck-profile-24-regular"
        class="text-yellow-300"
      ></Icon>
      <p class="text-sm">FREE Express Shipping On Orders 570+</p>
    </div>
    <div class="w-1/4 flex items-center justify-center">
      <div class="w-30 relative border-gray-400  border-r-1">
        <span @click="setIsDropped()" class=" flex items-center gap-5 cursor-pointer">
            <p>

                {{ selectedLanguage }}
            </p>
            <Icon name="fluent:chevron-down-16-regular" class="text-white" ></Icon>
        </span>
        <Transition name="fade" mode="out-in" >

            <ul  v-if="isDropped"  class="absolute bg-white w-full top-8  shadow-xl  p-3 z-4 text-black " >
                <li class="cursor-pointer hover:bg-gray-100 w-full p-1" @click="setSelectedLanguage(lg)" v-for="(lg , index) in languages"  > {{ lg }} </li>
            </ul>
        </Transition>
      </div>
    </div>
  </div>
</template>

<script setup>

    const languages = ref(["ENG","FR"])
    const selectedLanguage = ref("ENG")
    const isDropped = ref(false)

    const setSelectedLanguage = (lg)=>{
            selectedLanguage = lg
    }
    const setIsDropped = ()=>{
        // alert('clicked')
        isDropped.value = !isDropped.value
        // alert(""+isDropped)
    }

</script>
<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: all 0.3s ease-in-out;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
  transform: translateY(30px);
  
}

</style>
