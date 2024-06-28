<script>
import SearchInput from "./components/SearchInput.vue";
import WeatherCard from "./components/WeatherCard.vue";
import Header from "./components/Header/Header.vue";
import Hero from "./components/Hero/Hero.vue";
import Footer from "./components/Footer/Footer.vue";

export default {
    components: {
        SearchInput,
        WeatherCard,
        Header,
        Hero,
        Footer,
    },
    data() {
        return {
            places: [],
        };
    },
    methods: {
        addPlace(data) {
            this.places.push(data);
        },
        deletePlace(name) {
            this.places = this.places.filter((p) => p.location.name !== name);
        },
    },
};
</script>

<template>
    <Header />
    <div class="overflow-y-auto">
        <Hero />
        <main class="container mx-auto my-14">
            <h1
                class="text-center text-3xl md:text-5xl text-[#e63946] tracking-loose font-bold my-5"
            >
                Search Your Location
            </h1>
            <!-- Date -->
            <div class="text-center mb-6">
                {{
                    new Date().toLocaleDateString("en-us", {
                        weekday: "long",
                        year: "numeric",
                        month: "long",
                        day: "numeric",
                    })
                }}
            </div>

            <!-- Searchbar -->
            <div>
                <SearchInput @place-data="addPlace" />
            </div>

            <!-- Wheater Card -->
            <div class="grid grid-cols-3 gap-6 mt-5">
                <div v-for="(place, index) in places" :key="index">
                    <WeatherCard :place="place" @delete-place="deletePlace" />
                </div>
            </div>
        </main>
        <Footer />
    </div>
</template>
