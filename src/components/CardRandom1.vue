<template>
  <div class="card-body">
    <img :src="picture" alt="" />
    <div class="name">
      <p>{{ nombreCompleto }}</p>
    </div>
    <form @submit.prevent="sendText">
      <div class="input">
        <input
          v-model="color"
          value="#ffffff"
          type="color"
          name="colorChoice"
          id="input"
        />
      </div>
      <textarea
        v-model="chatText"
        name=""
        id=""
        placeholder=" Comienza a escribir..."
        rows="10"
        cols="25"
      ></textarea>
      <div>
        <button type="submit" >Enviar</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "CardRandom1",
  props: {
    picture: [],
    name: [],
    position: [],
    colorValue: [],
  },
  data() {
    return {
      chatText: [""],
      color: this.colorValue || "#ffffff",
    };
  },
  methods: {
    sendText() {
      const message = {
        author: this.nombreCompleto,
        contentText: this.chatText,
        position: this.position,
        color: this.color
      };
      this.$emit("send-text", message, this.color);
      this.chatText = "";
    },
  },
  computed: {
    nombreCompleto() {
      return `${this.name.first} ${this.name.last}`;
    },
  },
};
</script>

<style scoped>
.card-body {
  display: flex;
  flex-direction: column;
  flex-grow: 0.65;
  align-items: center;
  border-radius: 0.75rem;
  font-family: sans-serif;
}

.name {
  text-align: start;
  width: 50%;
  margin-top: 10px;
}

img {
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -2px rgba(0, 0, 0, 0.1);
  border-radius: 15px;
}

form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 8px;
  width: 65%;
  background-clip: border-box;
  padding-top: 1rem;
  margin-top: 1rem;
  margin-left: 1rem;
  margin-right: 1rem;
  border-radius: 0.75rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -2px rgba(0, 0, 0, 0.1);
  height: 14rem;
}

button {
  margin-bottom: 1rem;
  border: none;
  outline: none;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -2px rgba(0, 0, 0, 0.1);
  color: rgb(255 255 255);
  font-weight: 700;
  font-size: 0.85rem;
  padding: 0.75rem 1.5rem;
  background-color: rgb(10, 56, 94);
  border-radius: 0.5rem;
}

textarea {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen",
    "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  font-weight: 500;
  font-size: 1rem;
  color: #fff;
  background-color: rgb(28, 28, 30);
  box-shadow: 0 0 0.4vw rgba(0, 0, 0, 0.5), 0 0 0 0.15vw transparent;
  border-radius: 0.4vw;
  border: none;
  outline: none;
  resize: none;
}

img {
  width: 50%;
}

.input {
  width: 80%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1.5rem;
  color: white;
  font-weight: 600;
}
</style>
