<script setup>
const columnName = ref('')
const isInputOpen = ref(false)

const emit = defineEmits(['addColumn'])

const addColumn = (name) => {
    if (name.length > 0) {
        emit('addColumn', name)
        columnName.value = ''
        isInputOpen.value = false
    }
}
</script>

<template>
    <div class="w-80">
        <button v-if="!isInputOpen" class="w-full border-2 border-gray-300 border-dashed btn hover:border-primary"
            @click="isInputOpen = true">
            + New Column
        </button>
        <div v-else class="w-full join">
            <input type="text" placeholder="Type here"
                class="flex-grow input input-bordered join-item focus:outline-none" v-model="columnName"
                @keyup.enter="addColumn(columnName)" />
            <button class="btn btn-primary join-item" @click="addColumn(columnName)">+</button>
        </div>
    </div>
</template>
