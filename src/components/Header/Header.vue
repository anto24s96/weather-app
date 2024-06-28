<script>
export default {
    name: "Header",
};
</script>

<template>
    <header
        class="header fixed w-full top-0 bg-[#e63946] shadow-md flex items-center justify-between px-8 py-02"
        style="height: 80px; z-index: 999"
    >
        <!-- logo -->
        <h1 class="w-3/12">
            <a href="">
                <img
                    src="../../assets/logo-weather.png"
                    alt="logo"
                    class="w-52 h-auto"
                />
            </a>
        </h1>

        <!-- navigation -->
        <nav class="nav font-semibold text-lg text-white">
            <ul class="flex items-center">
                <li
                    class="p-6 border-b-4 border-[#a8dadc] border-opacity-0 hover:border-opacity-100 hover:text-[#a8dadc] duration-200 cursor-pointer active"
                >
                    <a href="">Home</a>
                </li>
                <li
                    class="p-6 border-b-4 border-[#a8dadc] border-opacity-0 hover:border-opacity-100 hover:text-[#a8dadc] duration-200 cursor-pointer"
                >
                    <a href="">Weekly Forecast</a>
                </li>
                <li
                    class="p-6 border-b-4 border-[#a8dadc] border-opacity-0 hover:border-opacity-100 hover:text-[#a8dadc] duration-200 cursor-pointer"
                >
                    <a href="">Favorites</a>
                </li>
                <li
                    class="p-6 border-b-4 border-[#a8dadc] border-opacity-0 hover:border-opacity-100 hover:text-[#a8dadc] duration-200 cursor-pointer"
                >
                    <a href="">Settings</a>
                </li>
            </ul>
        </nav>

        <!-- buttons --->
        <div class="w-3/12 flex justify-end"></div>
    </header>
</template>
