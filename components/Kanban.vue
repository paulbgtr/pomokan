<script setup>
import { ref } from 'vue'

const columns = ref([
    {
        id: 1,
        name: 'Todo',
        tasks: [
            {
                id: 1,
                name: 'Task 1',
                done: false
            }
        ],
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
        const maxTaskId = Math.max(0, ...columns.value.flatMap(col => col.tasks.map(t => t.id)))
        task.id = maxTaskId + 1
        column.tasks.push(task)
    }
}

const deleteTask = (taskId) => {
    const task = columns.value.find(col => col.tasks.find(t => t.id === taskId))
    if (task) {
        task.tasks = task.tasks.filter(t => t.id !== taskId)
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
            @deleteTask="deleteTask" @toggleDone="toggleDone" />
        <NewColumn @addColumn="addColumn" />
    </section>
</template>
