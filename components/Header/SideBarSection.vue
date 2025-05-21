<template>

<section class="w-full flex flex-col gap-4 " id="sidebarSection" >
          <button @click="isDropped = !isDropped" class="text-black flex items-center h-20 w-full justify-between pr-8 pl-5 cursor-pointer hover:bg-gray-100">
            <span class="flex items-center gap-5  ">

              <Icon :name="`${props.icon}`" class="text-2xl"></Icon>
              <h2 class="  text-start">
                {{ props.categoryName }}
              </h2>
            </span>
            
            <Icon v-if="!isDropped" class="text-2xl" name="ri:arrow-drop-right-line"></Icon>
            <Icon v-if="isDropped" class="text-2xl" name="ri:arrow-drop-down-line"></Icon>
        </button>
          <Transition name="drop" @before-enter="beforeEnter" @after-enter="afterEnter" @enter="enter" @before-leave="beforeLeave" @leave="leave" @after-leave="afterLeave">

            <ul v-if="isDropped" :ref="dropdown"  class="text-black   flex flex-col items-center p-2 gap-5 h-auto overflow-" >
              <li v-for="(Subcategory,index) in props.subcategories"  @mouseenter="setActiveHover(Subcategory,$event)" :key="index" class="cursor-pointer flex items-center gap-4 relative w-full text-start pl-15  hover:text-blue-500">
                <Icon :name="Subcategory.icon"></Icon>
                <p >{{ Subcategory.name }} </p>
                
                <Teleport defer to="body">
                  <Transition name="show">

                    <div v-if="isHover" :style="activeStyle" @mouseenter="isHover=true"  class="absolute w-80  h-auto  text-black p-5 z-[105]  ">
                     <ul class="bg-white p-5 rounded-xl">
                      <li v-for="(subContent,index) in activeInHover" class="" :key="index"> {{ subContent.name }} </li>
                     </ul>
                    </div>
                  </Transition>
                </Teleport>

              </li>
              
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

    },
    icon : {
      type : String,
      default : "lucide:package"
    }
})

const isDropped = ref(false);

const dropdown = ref(null)

const isHover = ref(false);
const activeInHover = ref('');
const activeStyle = ref({});
const liActive = ref({});

function setActiveHover(Subcategory,event){
  activeInHover.value = Subcategory.subsubcategories
  const rect = event.currentTarget.getBoundingClientRect()
  
  activeStyle.value = {
    left: `${rect.right + 5}px`, 
    top: `${rect.top}px`,
    minWidth: '240px'
  }

  
  isHover.value = true
}

function beforeEnter(el) {
  el.style.height = '0'
  el.style.overflow = 'hidden'
}

function enter(el) {
  el.style.height = `${el.scrollHeight}px`
}

function afterEnter(el) {
  el.style.height = 'auto'
  el.style.overflow = ''
}

function beforeLeave(el) {
  el.style.height = `${el.scrollHeight}px`
  el.style.overflow = 'hidden'
}

function leave(el) {
  requestAnimationFrame(() => {
    el.style.height = '0'
  })
}

function afterLeave(el) {
  el.style.height = ''
}
</script>
<style>
.drop-enter-active,.drop-leave-active{
    transition: all .5s ease-in-out;
}

.show-enter-from,.show-leave-to{
  transform: translateX(-100%);
  opacity: 0;
  visibility: hidden;
  /* z-index: -10; */
}
.show-enter-active,.show-leave-active{
  transition: all .9s ease;
}

</style>