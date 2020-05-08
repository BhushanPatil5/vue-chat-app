<template>
  <section class="chat-inputs">
    <form @submit.prevent="$emit('sendMessage', 'in')" id="person1-form">
      <label for="person1-input">Bob</label>
      <input
        type="text"
        placeholder="Type your message"
        id="person1-input"
        :value="bobMessage"
        @input="$emit('changeMsgBob', $event.target.value)"
      />
      <button type="submit">Send</button>
    </form>
    <button @click="$emit('clearAllMessages')">Clear All</button>
    <form @submit.prevent="$emit('sendMessage', 'out')" id="person2-form">
      <label for="person2-input">You</label>
      <input
        type="text"
        placeholder="Type your message"
        id="person2-input"
        :value="youMessage"
        @input="$emit('changeMsgYou', $event.target.value)"
      />
      <button type="submit">Send</button>
    </form>
  </section>
</template>

<script>
export default {
  name: "ChatInputs",
  data() {
    return {
      bobMessage: "",
      youMessage: ""
    };
  }
};
</script>