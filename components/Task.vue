<script setup>
defineProps({
    task: {
        type: String,
        required: true
    },
    isDone: {
        type: Boolean,
        default: false
    }
})
</script>

<template>
    <div class="p-2 border-2 border-gray-300 rounded-md">
        <p>{{ task }}</p>
    </div>
</template>