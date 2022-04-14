<template>
  <div class="main">
    <h1>Content</h1>
    <br /><br />
    <button v-on:click="addToCount()">Click to add 1</button>
    <button v-on:click="removeFromCount()">Click to remove 1</button>
    <button v-on:click="resetCount()">Click to reset</button>
    <h1>{{ count }}</h1>
    <br />
    <br />
    <button v-on:click="isHidden = true">Show name</button>
    <br />
    <h1>
      Name: <span v-if="isHidden">{{ showName() }}</span>
    </h1>
  </div>
</template>

<script>
export default {
  name: "Content",
  data() {
    return {
      isHidden: false,
      count: 0,
    };
  },
  methods: {
    addToCount() {
      this.count += 1;
    },
    removeFromCount() {
      this.count -= 1;
    },
    resetCount() {
      this.count = 0;
    },
    showName() {
      return "Shener";
    },
  },
};
</script>

<style scoped>
button {
  padding: 15px;
  border-radius: 10px;
  background-color: green;
  color: blue;
  font-size: 15px;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  margin: 0 15px 0 0;
  cursor: pointer;
}
button:hover {
  background-color: red;
}
.main {
  margin: 80px 0 80px 0;
}
</style>
