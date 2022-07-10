<template>
    <div class="relative h-10 m-1">
        <div style="border-top: 1px solid #e6e6e6;" class="grid grid-cols-6">
            <input
                type="text"
                v-model="message"
                @keyup.enter="sendMessage()"
                placeholder="Say something..."
                class="col-span-5 !outline-none p-1"
                style="border: none;"
            />
            <button
                @click="sendMessage()"
                class="place-self-end bg-gray-500 hover:bg-blue-700 p-1 mt-1 rounded text-white"
            >Send</button>
        </div>
    </div>
</template>

<script setup>
import { ref } from "@vue/reactivity"
import axios from "axios"

const props =  defineProps({
    room: {
        type: Object,
        default: {}
    }
})
const emit = defineEmits(['messagesent'])

const message = ref('')

const sendMessage = () => {
    if ( message.value === '') return

    axios.post(`/chat/room/${props.room.id}/message`, { message: message.value})
    .then( res => {
        if( res.status === 201) {
            message.value = ''
            emit('messagesent')
        }
    })
    .catch( error => {
        console.log(error)
    })
}
</script>

<style>

</style>
