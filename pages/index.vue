<script setup>
import { ref } from 'vue'

const columns = ref([
    {
        name: 'Todo',
        tasks: [],
    },
])
</script>

<template>
    <Header />

    <section class="mt-6 flex-grow flex overflow-x-auto">
        <Column v-for="column in columns" :key="column.name" :column="column" />
        <NewColumn />
    </section>
</template>
