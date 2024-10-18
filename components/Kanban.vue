<script setup>
import { ref } from 'vue'

const columns = ref([
    {
        id: 1,
        name: 'Todo',
        tasks: [],
    },
])

const addColumn = (name) => {
    columns.value.push({
        id: columns.value.length + 1,
        name,
        tasks: [],
    })
}

const addTask = (columnId, task) => {
    const column = columns.value.find(col => col.id === columnId)
    if (column) {
        column.tasks.push(task)
    }
}
</script>

<template>
    <section class="flex flex-grow mt-6 overflow-x-auto">
        <Column v-for="column in columns" :key="column.id" :column="column" :tasks="column.tasks" @addTask="addTask" />
        <NewColumn @addColumn="addColumn" />
    </section>
</template>
