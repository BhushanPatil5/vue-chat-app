<template>
  <div id="app">
    <ChatBox />
  </div>
</template>

<script>
import ChatBox from "./components/ChatBox";

export default {
  name: "App",
  components: {
    ChatBox,
  },
};
</script>

<style>
body,
html {
  font-family: sans-serif;
  font-weight: 100;
  background: #7b4397;
  background: -webkit-linear-gradient(
    to right,
    #dc2430,
    #7b4397
  );
  background: linear-gradient(
    to right,
    #dc2430,
    #7b4397
  );
}

.headline {
  text-align: center;
  font-weight: 100;
  color: white;
}
.chat-area {
  background: white;
  height: 50vh;
  margin-bottom: 1em;
  padding: 1em;
  overflow: auto;
  max-width: 350px;
  margin: 0 auto 2em auto;
  box-shadow: 2px 2px 5px 2px rgba(0, 0, 0, 0.3);
}
.message {
  width: 45%;
  border-radius: 10px;
  padding: 0.5em;
  font-size: 0.8em;
}
.message-out {
  background: #407fff;
  color: white;
  margin-left: 50%;
}
.message-in {
  background: #f1f0f0;
  color: black;
}
.chat-inputs {
  display: flex;
  justify-content: space-between;
}
#person1-input {
  padding: 0.5em;
}
#person2-input {
  padding: 0.5em;
}
</style>
