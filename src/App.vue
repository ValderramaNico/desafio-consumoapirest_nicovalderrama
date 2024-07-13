<template>
  <CardRandom1
    :class="textAlignLeft"
    v-if="users.length"
    :picture="users[0].picture.medium"
    :name="users[0].name"
    position="left"
    :colorValue="backgroundColor"
    @send-text="updateChatText"
  />
  <ChatWindow
    :chatArray="chatArray"
    :messageBackgroundColor="displayColor"
  />
  <CardRandom1
    :class="textAlignRight"
    v-if="users.length"
    :picture="users[1].picture.medium"
    :name="users[1].name"
    position="right"
    @send-text="updateChatText"
  />
</template>

<script>
import ChatWindow from "./components/ChatWindow.vue";
import CardRandom1 from "./components/CardRandom1.vue";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      users: [],
      chatArray: [],
      displayColor: "",
      backgroundColor: ""
    };
  },
  components: {
    ChatWindow,
    CardRandom1,
  },
  async created() {
    try {
      const url = `https://randomuser.me/api/?results=2`;
      const { data } = await axios.get(url);
      console.log(data);
      this.users.push(data.results[0], data.results[1]);
    } catch (error) {
      console.log(error);
    }
  },
  methods: {
    updateChatText(msg, color) {
      this.chatArray.push(msg);
      this.displayColor = color;
    },
    // colorBackground(color) {
    //   this.backgroundText = color;
    // },
  },
};
</script>

<style>
#app {
  margin-top: 3rem;
  max-width: 100%;
  display: flex;
  align-items: stretch;
  gap: 1.5rem;
}
</style>
