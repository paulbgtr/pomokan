<script setup>
const emit = defineEmits(['addTask', 'toggleDone'])

const props = defineProps({
    column: {
        type: Object,
        required: true
    },
    tasks: {
        type: Array,
        required: true
    }
})

const addTask = () => {
    const taskName = prompt("Enter task name:");
    if (taskName === null || taskName.trim() === "") {
        return;
    }

    emit('addTask', props.column.id, {
        id: props.tasks.length + 1,
        name: taskName,
        done: false
    })
}

const toggleDone = (taskId) => {
    emit('toggleDone', props.column.id, taskId)
}
</script>

<template>
    <div class="flex flex-col flex-shrink-0 p-2 mr-4 border-2 border-gray-300 rounded-md w-80">
        <h2 class="mb-2 text-lg font-bold text-center">{{ column.name }}</h2>
        <button class="w-full mb-2 btn btn-primary" @click="addTask">New Task</button>
        <div class="flex-grow space-y-2 overflow-y-auto">
            <Task v-for="task in tasks.reverse()" :key="task" :task="task" @toggleDone="toggleDone" />
        </div>
    </div>
</template>
