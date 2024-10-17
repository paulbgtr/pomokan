<script setup>
defineProps({
    column: {
        type: Object,
        required: true
    }
})
</script>

<template>
    <div class="border-2 w-80 flex-shrink-0 flex flex-col rounded-md p-2 border-gray-300 mr-4">
        <h2 class="text-center text-lg font-bold mb-2">{{ column.name }}</h2>
        <button class="w-full btn btn-primary mb-2">New Task</button>
        <div class="flex-grow overflow-y-auto">
            <!-- Task list will go here -->
        </div>
    </div>
</template>
