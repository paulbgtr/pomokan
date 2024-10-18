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

const toggleDone = (columnId, taskId) => {
    const column = columns.value.find(col => col.id === columnId)
    if (column) {
        const task = column.tasks.find(t => t.id === taskId)
        if (task) {
            task.done = !task.done
        }
    }
}
</script>

<template>
    <section class="flex flex-grow mt-6 overflow-x-auto">
        <Column v-for="column in columns" :key="column.id" :column="column" :tasks="column.tasks" @addTask="addTask"
            @toggleDone="toggleDone" />
        <NewColumn @addColumn="addColumn" />
    </section>
</template>
