<script setup>
import { FeEdit2 } from '@kalimahapps/vue-icons';

const isEditing = ref(false)

const header = ref('My Super Board')

const handleMouseEnter = () => {
    isEditing.value = true
}

const handleMouseLeave = () => {
    isEditing.value = false
}

const handleEdit = () => {
    const newHeader = prompt('Enter new header')
    if (newHeader) {
        header.value = newHeader
    }
}
</script>

<template>
    <div @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave" class="flex items-center justify-center gap-2">
        <h1 class="text-6xl font-black text-primary">{{ header }}</h1>
        <FeEdit2 v-if="isEditing" class="w-6 h-6 cursor-pointer" @click="handleEdit" />
    </div>
</template>