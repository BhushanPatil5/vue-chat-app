<template>
  <div class="hello">
    <h1 class="headline">Vue.js Chat Box</h1>
    <main id="app">
      <!-- CHAT AREA -->
      <ChatArea :messages="messages" ref="chatArea" />

      <!-- CHAT INPUTS -->
      <ChatInputs
        @sendMessage="sendMessage"
        @clearAllMessages="clearAllMessages"
        @changeMsgBob="changeMsgBob"
        @changeMsgYou="changeMsgYou"
      />
    </main>
  </div>
</template>

<script>
import ChatArea from "./ChatArea";
import ChatInputs from "./ChatInputs";

export default {
  name: "ChatBox",
  components: {
    ChatArea,
    ChatInputs
  },
  data() {
    return {
      bobMessage: "",
      youMessage: "",
      // default chat history
      messages: [
        {
          body: "Welcome to the chat, I'm Bob!",
          author: "bob"
        },
        {
          body: "Thank you Bob",
          author: "you"
        },
        {
          body: "You're most welcome",
          author: "bob"
        }
      ]
    };
  },
  methods: {
    // handleChatMsg() {
    //   new Promise((resolve, reject) => {
    //     setTimeout(function() {
    //       resolve("Success!");
    //     }, 1000);
    //   });
    // },
    // Sending messages to Server
    sendMessage(direction) {
      this.handleServiceCallMsg(1000).then(() => {
        if (!this.youMessage && !this.bobMessage) {
          return;
        }
        if (direction === "out") {
          this.messages.push({ body: this.youMessage, author: "you" });
          this.youMessage = "";
        } else if (direction === "in") {
          this.messages.push({ body: this.bobMessage, author: "bob" });
          this.bobMessage = "";
        } else {
          alert("something went wrong");
        }
        this.$nextTick(() => {
          let messageDisplay = this.$refs.chatArea;
          messageDisplay.scrollTop = messageDisplay.scrollHeight;
        });
      });
    },

    handleServiceCallMsg(time) {
      return new Promise(resolve => setTimeout(resolve, time));
    },
    // clear all chat history
    clearAllMessages() {
      this.messages = [];
    },
    // getting message from bob
    changeMsgBob(msg) {
      this.bobMessage = msg;
    },
    // getting message of you
    changeMsgYou(msg) {
      this.youMessage = msg;
    }
  }
};
</script>
