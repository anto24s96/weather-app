<script>
export default {
    name: "Hero",
};
</script>

<template>
    <section
        class="relative bg-cover bg-center bg-no-repeat"
        style="
            background-image: url('https://images.unsplash.com/photo-1659579331500-77411dc30fca?q=80&w=2574&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');
        "
    >
        <div
            class="absolute inset-0 bg-gradient-to-r from-transparent to-white/25 pointer-events-none"
        ></div>
        <div class="text-white py-5 relative z-10">
            <div
                class="container mx-auto flex flex-col md:flex-row items-center my-12 md:my-24"
            >
                <div
                    class="flex flex-col w-full lg:w-1/3 justify-center items-start p-8"
                >
                    <h1
                        class="text-3xl md:text-5xl text-[#e63946] tracking-loose font-bold"
                    >
                        WEATHER NOW
                    </h1>
                    <h2
                        class="text-3xl md:text-5xl leading-relaxed md:leading-snug mb-2"
                    >
                        Forecasts to keep you ready for anything.
                    </h2>
                    <p class="text-sm md:text-base text-gray-50 mb-4">
                        Discover accurate and up-to-date forecasts, always
                        within reach. Whether for work or leisure, Weather Now
                        keeps you informed.
                    </p>
                    <a
                        href="#"
                        class="bg-transparent hover:bg-[#e63946] text-[#e63946] hover:text-white rounded shadow hover:shadow-lg py-2 px-4 border border-[#e63946] hover:border-transparent"
                        >Explore Now</a
                    >
                </div>
                <div
                    class="p-8 mt-12 mb-6 md:mb-0 md:mt-0 ml-0 md:ml-12 lg:w-2/3 justify-center"
                ></div>
            </div>
        </div>
    </section>
</template>
