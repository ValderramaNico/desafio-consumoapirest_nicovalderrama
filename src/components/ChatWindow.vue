<template>
  <div class="chatWindow">
    <div
      class="authorMessage"
      v-for="(message, index) in chatArray"
      :key="index"
      :class="[
        'message',
        message.position === 'right' ? 'text-right' : 'text-left',
        'color-',
        message.displayColor,
      ]"
    >
      <span class="message">{{ message.author }}</span>
      <span class="message">{{ message.contentText }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "ChatWindow",
  props: ["chatArray"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.chatWindow {
  overflow: scroll;
  flex-grow: 2;
  border-radius: 50px;
  background: #e0e0e0;
  padding: 20px;
}

.authorMessage {
  display: flex;
  flex-direction: column;
  /* background-color: white; */
  border-radius: 50px 0px 50px 50px / 50px 1px 50px 50px;
  padding: 0 15px;
  margin-bottom: 15px;
}

::-webkit-scrollbar {
  display: none;
}

.text-left {
  text-align: left;
}

.text-right {
  text-align: right;
  border-radius: 0px 50px 50px 50px / 1px 50px 50px 50px;
}
</style>
