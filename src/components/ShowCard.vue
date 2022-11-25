
<template>
    <div 
    class="border-2 border-black rounded-lg m-1 p-2 w-auto"
    :class="{ 'bg-slate-200': true }">
        <h2>{{ props.cardData.className }}</h2>
        <h2>{{ props.cardData.classType }}</h2>
        <div class="flex gap-1">
            <h2 class="flex gap-1 " v-for="speaker in cardData.speaker" :key="speaker">{{ speaker }}</h2>
        </div>
    </div>
</template>

<script setup>
const props = defineProps(["cardData"])
</script>
