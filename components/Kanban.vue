<script setup>
import { ref } from 'vue'

const columns = ref([
    {
        name: 'Todo',
        tasks: [
            "buy pepperoni",
            "buy cheese",
            "buy bread",
            "buy butter",
            "buy milk",
            "buy eggs",
            "buy flour",
            "buy sugar",
            "buy salt",
        ],
    },
])

const addColumn = (name) => {
    columns.value.push({
        name,
        tasks: [],
    })
}
</script>

<template>
    <section class="flex flex-grow mt-6 overflow-x-auto">
        <Column v-for="column in columns" :key="column.name" :column="column" :tasks="column.tasks" />
        <NewColumn @addColumn="addColumn" />
    </section>
</template>
