<template>
    <nav class="flex items-center w-full h-2/3 bg-white p-3 justify-around ">
        <h1 class="text-3xl text-black font-bold tracking-wider">Logo.</h1>
        <HeaderSearchBar/>
        <div class="w-1/4 justify-sel flex items-center justify-around ">

            <HeaderAccountPreview/>
            <div class="text-black text-3xl flex items-center justify-between w-20">
                <div class="relative ">
                    <Icon name="heroicons-outline:heart" />
                    <p class="text-sm absolute top-0 -right-3 border-2  p-2.5 z-3 text-white bg-red-400 w-5 h-5 rounded-xl grid place-content-center font-semibold">10</p>
                </div>
                <div class="relative">
                    <Icon name="system-uicons:bag" />
                    <p class="text-sm absolute top-0 -right-3 border-2  p-2.5 z-3 text-white bg-red-400 w-5 h-5 rounded-xl grid place-content-center font-semibold">10</p>
                    
                </div>
            </div>
        </div>
    </nav>
</template>