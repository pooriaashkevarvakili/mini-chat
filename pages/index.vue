<template>
    <div>
      <Chat  :user="user1" :otherUser="user2" />
      <Chat :user="user2" :otherUser="user3" />
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  import Chat from './Chat.vue';
  
  export default {
    components: {
      Chat
    },
    setup() {
      const user1 = ref('User 1');
      const user2 = ref('User 2');
      const user3 = ref('User 3');
  
      return {
        user1,
        user2,
        user3
      };
    }
  };
  </script>