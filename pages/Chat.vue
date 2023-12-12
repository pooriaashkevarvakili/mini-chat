<template>
  <div class="">
    <h2 class="ml-4">{{ user }}</h2>
    <div class="">
      <div v-for="message in messages" :key="message.id" >
        <span class="ml-4">{{ message.sender }}:</span>
        <p class="ml-4">{{ message.text }}</p>
      </div>
    </div>
    <form class="  text-white   " @submit.prevent="sendMessage">
      <input class="bg-red-400 border w-56 h-20 rounded-xl ml-4 placeholder-zinc-950 border-blue-400 p-3" v-model="newMessage" type="text" placeholder="Enter your message" />
      <button class="bg-green-400  rounded-xl ml-10 w-56 h-20" type="submit">Send</button>
    </form>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  props: {
    user: {
      type: String,
      required: true
    },
    otherUser: {
      type: String,
      required: true
    }
  },
  setup(props) {
    const messages = ref([]);
    const newMessage = ref('');

    const sendMessage = () => {
      const message = {
        id: Date.now(),
        sender: props.user,
        text: newMessage.value
      };
      messages.value.push(message);
      newMessage.value = '';
    };

    return {
      messages,
      newMessage,
      sendMessage
    };
  }
};
</script>