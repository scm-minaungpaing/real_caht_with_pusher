<template>
    <div class="grid grid-cols-2">
        <div class="font-bold text-xl">
            {{ selected.name }} Chat
        </div>
        <div>
            <select
                v-model="selected"
                class="float-right"
            >
                <option
                    v-for="(room, index) in rooms"
                    :key="index"
                    :value="room"
                >
                    {{ room.name }}
                </option>
            </select>
        </div>
    </div>
</template>

<script setup>
import { ref } from "@vue/reactivity"
import { onMounted } from "@vue/runtime-core"

const props = defineProps({
    rooms: {
        type: Object,
        default: {},
    },
    currentRoom: {
        type: Object,
        default: {},
    }
})

const selected = ref('')

onMounted(() => {
    selected.value = props.currentRoom
})
</script>

<style>

</style>
