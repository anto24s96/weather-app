<script>
import axios from "axios";

export default {
    name: "SearchInput",
    data() {
        return {
            searchTerm: "",
            timeout: null,
            results: null,
            apiKey: import.meta.env.VITE_API_KEY,
        };
    },
    methods: {
        handleSearch() {
            clearTimeout(this.timeout);
            this.timeout = setTimeout(async () => {
                try {
                    if (this.searchTerm !== "") {
                        const response = await axios.get(
                            `http://api.weatherapi.com/v1/search.json?key=${this.apiKey}&q=${this.searchTerm}`
                        );
                        const data = response.data;
                        this.results = data;
                    } else {
                        this.results = null;
                    }
                } catch (error) {
                    console.error(
                        "Errore durante il recupero dei dati:",
                        error
                    );
                }
            }, 500);
        },
        async getWeather(id) {
            try {
                const response = await axios.get(
                    `http://api.weatherapi.com/v1/forecast.json?key=${this.apiKey}&q=id:${id}&days=3&aqi=no&alerts=no`
                );

                const data = response.data;
                this.$emit("place-data", data);

                this.searchTerm = "";
                this.results = null;
            } catch (error) {
                console.error("Errore durante il recupero dei dati:", error);
            }
        },
    },
    mounted() {
        this.getWeather("Rome");
    },
};
</script>

<template>
    <section>
        <div class="flex flex-col items-center">
            <!-- Search Field -->
            <form class="w-4/12">
                <div
                    class="bg-white border border-indigo-600/30 rounded-lg shadow-lg flex items-center"
                >
                    <i
                        class="fa-solid fa-magnifying-glass p-2 text-indigo-600"
                    ></i>
                    <input
                        type="text"
                        placeholder="Search for a place"
                        class="rounded-r-lg p-2 border-0 outline-0 focus:ring-2 focus:ring-indigo-600 ring-inset w-full"
                        v-model="searchTerm"
                        @input="handleSearch"
                    />
                </div>
            </form>
            <!-- Search Suggestions -->
            <div class="bg-white my-2 rounded-lg shadow-lg w-4/12">
                <div v-if="results !== null">
                    <div v-for="place in results" :key="place.id">
                        <button
                            class="px-3 my-2 hover:text-indigo-600 hover:font-bold w-full text-left"
                            @click="getWeather(place.id)"
                        >
                            {{ place.name }}, {{ place.region }},
                            {{ place.country }}
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>
