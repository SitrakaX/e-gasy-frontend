<template>
    <div class="flex items-center w-45 gap-2  justify-between cursor-pointer hover:bg-gray-100 p-2 max-[1100px]:hidden">
        <div class=" border-2 border-gray-300 w-12 h-12 grid place-content-center rounded-4xl text-black font-light"><Icon name="heroicons-outline:user" class="text-3xl" ></Icon></div>
        <div class="">
            <p class="text-gray-400">hello user</p>
            <p class="text-black font-semibold">Your Account</p>
        </div>
    </div>
    <div class="w-30 h-10 rounded-3xl hidden">
        <button class="border text-blue-950 w-full h-full rounded-4xl hover:bg-blue-950 hover:text-white cursor-pointer">signin</button>
    </div>
</template>