<script>
import Borderline from "./Borderline.vue";
import WeatherForcastDay from "./WeatherForcastDay.vue";
import WeatherInfo from "./WeatherInfo.vue";

export default {
    name: "WeatherCard",
    components: {
        Borderline,
        WeatherForcastDay,
        WeatherInfo,
    },
    props: {
        place: Object,
    },
    data() {
        return {
            showDetails: false,
        };
    },
    methods: {
        removePlace(placeName) {
            this.$emit("delete-place", placeName);
            this.showDetails = false;
        },
    },
};
</script>

<template>
    <div
        class="text-white p-10 rounded-lg shadow-lg gap-6 mb-6 relative overflow-hidden min"
        :class="place.current.is_day === 1 ? 'bg-day' : 'bg-night'"
    >
        <!-- Location & time -->
        <div class="mb-2 flex justify-between items-center">
            <div class="flex items-center justify-center gap-2">
                <i class="fa-solid fa-location-dot"></i>
                <h1 class="text-3xl">{{ place.location.name }}</h1>
            </div>
            <div class="flex items-center justify-center gap-2">
                <i class="fa-solid fa-clock"></i>
                <h1 class="text-3xl">
                    {{ new Date(place.location.localtime).getHours() }}:{{
                        new Date(place.location.localtime).getMinutes()
                    }}
                </h1>
            </div>
        </div>

        <!-- Current weather -->
        <div class="text-center flex-1">
            <img
                :src="place.current.condition.icon"
                alt="icon"
                width="200"
                class="mx-auto"
            />
            <h1 class="text-9xl mb-2">
                {{ Math.round(place.current.temp_c) }}&deg;
            </h1>
            <p class="text-2xl min-h-16">{{ place.current.condition.text }}</p>
        </div>

        <Borderline />

        <!-- forecast -->
        <div v-for="(day, index) in place.forecast.forecastday" :key="index">
            <WeatherForcastDay :day="day" />
        </div>

        <!-- info -->
        <Transition name="fade">
            <div v-show="showDetails">
                <WeatherInfo
                    :place="place"
                    @close-info="showDetails = false"
                    @remove-place="removePlace(place.location.name)"
                />
            </div>
        </Transition>

        <!-- forecast btn -->
        <div class="flex justify-end items-center gap-1 mt-10">
            <button @click="showDetails = true">
                More <i class="fa-solid fa-arrow-right text-sm -mb-px"></i>
            </button>
        </div>
    </div>
</template>

<style scoped>
.bg-day {
    background-color: #8ec5fc;
    background-image: linear-gradient(62deg, #8ec5fc 0%, #e0c3fc 100%);
}
.bg-night {
    background-color: #07223d;
    background-image: linear-gradient(62deg, #0a2a4a 0%, #270845 100%);
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.2s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>
