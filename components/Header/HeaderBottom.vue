<template>
  <div class="w-full h-[10dvh] bg-white border-t-2 flex items-center px-2 max-[1100px]:hidden">
    <button
      @click="isShowed = true"
      class="flex items-center justify-center gap-2 text-blue-950 text-xl w-1/6 cursor-pointer hover:bg-gray-100 p-2 transition-all"
    >
      <Icon name="fluent:align-left-16-regular" class="text-xl"></Icon>
      <p class="">all categories</p>
    </button>
    <ul class="flex items-center w-4/6 justify-around text-black h-full ">
      <li v-for="(trendCategory,index) in trendCategories" :key="index" @mouseenter="isDropped=true" @mouseleave="isDropped=false" class="h-full flex items-center hover:border-b-2 cursor-pointer z-[100]">
        <p>
          {{ trendCategory.name }}
        </p>
        <div v-if="isDropped" class="absolute left-0 top-[25dvh]  w-[100%] h-[35dvh] flex items-center bg-gray-100 p-2">
              <ul class="w-full h-full flex flex-col flex-wrap gap-3">
                <li v-for="(sub,subindex) in trendCategory.subcategories"  :key="subindex"   class=""></li>
                <HeaderCategoryDropDown :subcategory="sub" ></HeaderCategoryDropDown>
              </ul>
              
            </div>

          
      </li>
      
    </ul>
        <HeaderSideBar v-model="isShowed" :categories="categories" ></HeaderSideBar>

      
  </div>
</template>
<script setup>

//import { categories } from './SideBar.vue';

const categories = [
  {
    name: "Electronics",
    icon: "ph:device-mobile-camera-light", 
    subcategories: [
      {
        name: "Phones",
        icon: "lucide:smartphone",
        subsubcategories: [
          { name: "Smartphones", icon: "lucide:smartphone" },
          { name: "Cases & Covers", icon: "mdi:phone-case" }, 
          { name: "Refurbished", icon: "lucide:refresh-cw" }
        ]
      },
      {
        name: "Computers",
        icon: "lucide:laptop",
        subsubcategories: [
          { name: "Laptops", icon: "lucide:laptop-2" },
          { name: "PC Components", icon: "mdi:chip" },
          { name: "Monitors", icon: "lucide:monitor" }
        ]
      },
      {
        name: "TV & Home Theater",
        icon: "material-symbols:tv-with-assistant", 
        subsubcategories: [
          { name: "4K TVs", icon: "mdi:television-4k" },
          { name: "Soundbars", icon: "lucide:speaker" },
          { name: "Streaming Devices", icon: "lucide:cast" }
        ]
      },
      {
        name: "Audio",
        icon: "lucide:headphones",
        subsubcategories: [
          { name: "Headphones", icon: "lucide:headphones" },
          { name: "Bluetooth Speakers", icon: "material-symbols:speaker" },
          { name: "Home Audio", icon: "mdi:surround-sound" }
        ]
      },
      {
        name: "Cameras & Drones",
        icon: "material-symbols:camera-video",
        subsubcategories: [
          { name: "DSLR Cameras", icon: "lucide:camera" },
          { name: "Mirrorless", icon: "mdi:camera-iris" },
          { name: "Drones", icon: "lucide:drone" }
        ]
      }
    ]
  },
  {
    name: "Clothing & Apparel",
    icon: "mdi:bow-tie", // MingCute icon
    subcategories: [
      {
        name: "Men's Fashion",
        icon: "lucide:shirt",
        subsubcategories: [
          { name: "T-Shirts", icon: "lucide:tshirt" },
          { name: "Jeans", icon: "icon-park-outline:jeans" },
          { name: "Suits", icon: "mdi:account-tie" }
        ]
      },
      {
        name: "Women's Fashion",
        icon: "mdi:shoe-heel",
        subsubcategories: [
          { name: "Dresses", icon: "icon-park-outline:dress" },
          { name: "Blouses", icon: "mdi:tshirt-crew" },
          { name: "Skirts", icon: "mdi:skirt" }
        ]
      },
      {
        name: "Kids & Baby",
        icon: "lucide-lab:bottle-baby",
        subsubcategories: [
          { name: "Baby Clothing", icon: "mdi:baby-clothes" },
          { name: "Boys' Apparel", icon: "mdi:human-male-child" },
          { name: "Girls' Apparel", icon: "mdi:human-female-child" }
        ]
      },
      {
        name: "Activewear",
        icon: "material-symbols:sports-gymnastics",
        subsubcategories: [
          { name: "Yoga Pants", icon: "material-symbols:yoga" },
          { name: "Running Shoes", icon: "mdi:run" },
          { name: "Gym Shorts", icon: "mdi:tshirt-crew-outline" }
        ]
      },
      {
        name: "Seasonal",
        icon: "lucide:calendar",
        subsubcategories: [
          { name: "Winter Coats", icon: "mdi:coat-rack" },
          { name: "Summer Dresses", icon: "mdi:weather-sunny" },
          { name: "Rain Gear", icon: "lucide:umbrella" }
        ]
      }
    ]
  },
  {
    name: "Home & Kitchen",
    icon: "material-symbols:home-outline",
    subcategories: [
      {
        name: "Furniture",
        icon: "bx:chair",
        subsubcategories: [
          { name: "Living Room", icon: "mdi:sofa" },
          { name: "Bedroom", icon: "lucide:bed" },
          { name: "Home Office", icon: "mdi:desk" }
        ]
      },
      {
        name: "Kitchen Essentials",
        icon: "lucide:utensils",
        subsubcategories: [
          { name: "Cookware", icon: "mdi:pot" },
          { name: "Cutlery", icon: "mdi:silverware" },
          { name: "Small Appliances", icon: "mdi:toaster" }
        ]
      },
      {
        name: "Home Improvement",
        icon: "lucide:hammer",
        subsubcategories: [
          { name: "Lighting", icon: "lucide:lamp" },
          { name: "Storage", icon: "mdi:wardrobe" },
          { name: "Tools", icon: "lucide:wrench" }
        ]
      },
      {
        name: "Bed & Bath",
        icon: "material-symbols:bed-outline",
        subsubcategories: [
          { name: "Bedding", icon: "lucide:bed" },
          { name: "Bath Towels", icon: "mdi:bathtub" },
          { name: "Shower Curtains", icon: "mdi:shower" }
        ]
      },
      {
        name: "Outdoor Living",
        icon: "lucide:tree-pine",
        subsubcategories: [
          { name: "Patio Furniture", icon: "mdi:chair-rolling" },
          { name: "Grills", icon: "mdi:grill" },
          { name: "Gardening", icon: "lucide:flower-2" }
        ]
      }
    ]
  },
  {
    name: "Beauty & Personal Care",
    icon: "material-symbols:health-and-beauty-outline",
    subcategories: [
      {
        name: "Skincare",
        icon: "material-symbols-light:comedy-mask-outline-rounded",
        subsubcategories: [
          { name: "Moisturizers", icon: "mdi:lotion" },
          { name: "Cleansers", icon: "mdi:face-woman-shimmer" },
          { name: "Sunscreen", icon: "mdi:weather-sunny" }
        ]
      },
      {
        name: "Makeup",
        icon: "lucide:brush",
        subsubcategories: [
          { name: "Foundation", icon: "mdi:makeup-brush" },
          { name: "Lipstick", icon: "mdi:lipstick" },
          { name: "Eyeshadow", icon: "mdi:eye" }
        ]
      },
      {
        name: "Fragrance",
        icon: "lucide:spray-can",
        subsubcategories: [
          { name: "Perfume", icon: "mdi:spray-bottle" },
          { name: "Cologne", icon: "mdi:spray" },
          { name: "Body Spray", icon: "mdi:bottle-tonic" }
        ]
      },
      {
        name: "Hair Care",
        icon: "lucide:scissors",
        subsubcategories: [
          { name: "Shampoo", icon: "mdi:bottle-tonic-outline" },
          { name: "Styling Tools", icon: "mdi:hair-dryer" },
          { name: "Hair Color", icon: "mdi:palette" }
        ]
      },
      {
        name: "Grooming",
        icon: "lucide-lab:razor",
        subsubcategories: [
          { name: "Shaving", icon: "mdi:razor-double" },
          { name: "Oral Care", icon: "mdi:toothbrush" },
          { name: "Deodorant", icon: "mdi:spray" }
        ]
      }
    ]
  },
  {
    name: "Sports & Outdoors",
    icon: "lucide:dumbbell",
    subcategories: [
      {
        name: "Exercise Equipment",
        icon: "material-symbols:exercise",
        subsubcategories: [
          { name: "Treadmills", icon: "mdi:run" },
          { name: "Weights", icon: "lucide:dumbbell" },
          { name: "Yoga Mats", icon: "material-symbols:yoga" }
        ]
      },
      {
        name: "Team Sports",
        icon: "mdi:soccer",
        subsubcategories: [
          { name: "Soccer", icon: "mdi:soccer" },
          { name: "Basketball", icon: "mdi:basketball" },
          { name: "Baseball", icon: "mdi:baseball" }
        ]
      },
      {
        name: "Outdoor Recreation",
        icon: "lucide:tent",
        subsubcategories: [
          { name: "Camping", icon: "lucide:tent" },
          { name: "Hiking", icon: "mdi:hiking" },
          { name: "Fishing", icon: "mdi:fish" }
        ]
      },
      {
        name: "Cycling",
        icon: "lucide:bike",
        subsubcategories: [
          { name: "Mountain Bikes", icon: "mdi:bicycle" },
          { name: "Accessories", icon: "mdi:basket" },
          { name: "Repair Kits", icon: "mdi:wrench" }
        ]
      },
      {
        name: "Water Sports",
        icon: "mdi:surfing",
        subsubcategories: [
          { name: "Swimming", icon: "mdi:swim" },
          { name: "Surfing", icon: "mdi:surfing" },
          { name: "Kayaking", icon: "mdi:kayaking" }
        ]
      }
    ]
  },
  {
    name: "Toys & Games",
    icon: "lucide:toy-brick",
    subcategories: [
      {
        name: "Kids' Toys",
        icon: "mdi:toy-brick",
        subsubcategories: [
          { name: "Building Sets", icon: "mdi:toy-brick" },
          { name: "Dolls", icon: "mdi:doll" },
          { name: "Action Figures", icon: "mdi:robot" }
        ]
      },
      {
        name: "Board Games",
        icon: "lucide:dices",
        subsubcategories: [
          { name: "Strategy Games", icon: "mdi:chess-knight" },
          { name: "Family Games", icon: "mdi:account-group" },
          { name: "Party Games", icon: "mdi:party-popper" }
        ]
      },
      {
        name: "Video Games",
        icon: "lucide:gamepad-2",
        subsubcategories: [
          { name: "Console Games", icon: "mdi:microsoft-xbox" },
          { name: "PC Games", icon: "mdi:desktop-classic" },
          { name: "Accessories", icon: "mdi:joystick" }
        ]
      },
      {
        name: "Puzzles",
        icon: "mdi:puzzle",
        subsubcategories: [
          { name: "Jigsaw Puzzles", icon: "mdi:puzzle" },
          { name: "Brain Teasers", icon: "mdi:head-cog" },
          { name: "3D Puzzles", icon: "mdi:cube" }
        ]
      },
      {
        name: "Outdoor Play",
        icon: "mdi:slide",
        subsubcategories: [
          { name: "Playhouses", icon: "mdi:home" },
          { name: "Swing Sets", icon: "mdi:swing" },
          { name: "Trampolines", icon: "mdi:jump-rope" }
        ]
      }
    ]
  },
  {
    name: "Groceries & Household",
    icon: "lucide:shopping-cart",
    subcategories: [
      {
        name: "Fresh Food",
        icon: "mdi:food-apple",
        subsubcategories: [
          { name: "Fruits", icon: "mdi:food-apple" },
          { name: "Vegetables", icon: "mdi:carrot" },
          { name: "Meat", icon: "mdi:food-drumstick" }
        ]
      },
      {
        name: "Pantry Staples",
        icon: "mdi:barley",
        subsubcategories: [
          { name: "Pasta", icon: "mdi:food-variant" },
          { name: "Rice", icon: "mdi:rice" },
          { name: "Canned Goods", icon: "mdi:can" }
        ]
      },
      {
        name: "Beverages",
        icon: "lucide:glass-water",
        subsubcategories: [
          { name: "Water", icon: "mdi:cup-water" },
          { name: "Juice", icon: "mdi:glass-cocktail" },
          { name: "Soda", icon: "mdi:cup" }
        ]
      },
      {
        name: "Cleaning Supplies",
        icon: "mdi:broom",
        subsubcategories: [
          { name: "Detergents", icon: "mdi:washing-machine" },
          { name: "Disinfectants", icon: "mdi:spray" },
          { name: "Paper Goods", icon: "mdi:paper-roll" }
        ]
      },
      {
        name: "Pet Care",
        icon: "mdi:dog",
        subsubcategories: [
          { name: "Dog Food", icon: "mdi:dog" },
          { name: "Cat Food", icon: "mdi:cat" },
          { name: "Pet Toys", icon: "mdi:toy-brick" }
        ]
      }
    ]
  }
];
const trendCategories = categories.slice(0,5);

const isShowed = ref(false);
const isDropped = ref(false);

const setIsShowed = async () => {
  isShowed.value = !isShowed.value;
};
</script>

