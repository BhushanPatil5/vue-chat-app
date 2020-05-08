<template>
  <section ref="chatArea" class="chat-area">
    <p
      v-for="(message,i) in messages"
      :key="i"
      class="message"
      :class="{ 'message-out': message.author === 'you', 'message-in': message.author !== 'you' }"
    >{{ message.body }}</p>
  </section>
</template>

<script>
export default {
  name: "ChatArea",
  props: {
    messages: {
      type: Array,
      required: true
    }
  }
};
</script>