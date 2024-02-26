<script setup>
import { ref, onMounted } from 'vue'

const days = ref(12)
const hours = ref(23)
const minutes = ref(45)

function updateTime() {
    if (minutes.value > 0) {
        minutes.value--;
    } else if (hours.value > 0) {
        hours.value--;
        minutes.value = 59;
    } else if (days.value > 0) {
        days.value--;
        hours.value = 23;
        minutes.value = 59;
    }
}

onMounted(() => {
    setInterval(updateTime, 60000); // Update time every minute (60000 milliseconds)
});
</script>

<template>
    <h2 class="text-center mb-3 font-extrabold text-3xl lg:text-6xl">JUST A LITTLE MORE...</h2>
    <div class="flex flex-col lg:flex-row gap-8  text-rose-800 items-center justify-center">
        <div class="bg-[#173f27] p-14 relative">
            <p class="font-medium text-8xl">{{ days }}</p>
            <p class="absolute  font-semibold left-0 bottom-4 -translate-x-6 tracking-wide -rotate-90 text-3xl leading-loose">DAYS</p>
        </div>
        <div class="bg-[#173f27] p-14 relative">
            <p class="font-medium text-8xl">{{ hours }}</p>
            <p class="absolute  font-semibold left-0 bottom-7 -translate-x-9 tracking-wide -rotate-90 text-3xl leading-loose">HOURS</p>
        </div>
        <div class="bg-[#173f27] p-14 relative w-56">
            <p class="font-medium text-8xl">{{ minutes }}</p>
            <p class="absolute  font-semibold left-0 bottom-11 -translate-x-12 tracking-wide -rotate-90 text-3xl leading-loose">MINUTES</p>
        </div>
       
    </div>
</template>
