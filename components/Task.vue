<script setup>
const emit = defineEmits(['toggleDone'])

defineProps({
    task: {
        type: Object,
        required: true
    },
    isDone: {
        type: Boolean,
        default: false
    }
})

const toggleDone = (taskId) => {
    emit('toggleDone', taskId)
}
</script>

<template>
    <div class="p-2 border-2 border-gray-300 rounded-md">
        <div class="flex items-center gap-1">
            <input type="checkbox" :checked="task.done" class="checkbox checkbox-xs" @change="toggleDone(task.id)" />
            <p :class="{ 'line-through text-gray-500': task.done }">{{ task.name }}</p>
        </div>
    </div>
</template>