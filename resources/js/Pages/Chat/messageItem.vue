<template>
    <div>
        <span class="font-semibold text-lg text-gray-800">{{ message.user.name}}</span>: {{ message.message}}
    </div>
</template>

<script setup>
const props = defineProps({
    message: {
        type: Object,
        default: {},
    }
})
</script>

<style>

</style>
