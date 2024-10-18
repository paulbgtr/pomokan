<script setup>
defineProps({
    column: {
        type: Object,
        required: true
    },
    tasks: {
        type: Array,
        required: true
    }
})
</script>

<template>
    <div class="flex flex-col flex-shrink-0 p-2 mr-4 border-2 border-gray-300 rounded-md w-80">
        <h2 class="mb-2 text-lg font-bold text-center">{{ column.name }}</h2>
        <button class="w-full mb-2 btn btn-primary">New Task</button>
        <div class="flex-grow space-y-2 overflow-y-auto">
            <Task v-for="task in tasks" :key="task" :task="task" />
        </div>
    </div>
</template>
