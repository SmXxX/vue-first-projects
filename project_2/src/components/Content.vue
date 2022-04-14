<template>
  <div class="main">
    <br />
    <h1 v-bind:class="color">This is website Content</h1>
    <br />
    <label for="green">Green</label>
    <input
      v-model="color"
      type="radio"
      id="green"
      name="color"
      value="greenColor"
    />
    <br />
    <label for="orange">Orange</label>
    <input
      v-model="color"
      type="radio"
      id="orange"
      name="color"
      value="orangeColor"
    />
    <br />
    <label for="black">Disable button</label>
    <input v-on:click="isDisabled = !isDisabled" type="checkbox" />
    <br />
    <button v-on:click="color = 'black'" type="submit" :disabled="!isDisabled">
      Reset color
    </button>
    <br />
    <br />

    <div v-if="!result">
      <ul>
        <li v-for="item in data" :key="item">
          {{ item }}
        </li>
      </ul>
    </div>
    <br />
    <button v-on:click="result = !result">Show/Hide Text</button>
  </div>
</template>
<script>
export default {
  name: "Content",
  data() {
    return {
      data: ["Ivan", "Petyr", "Stoqn", "Andrei", "Georgi"],
      result: true,
      color: "",
      isDisabled: true,
      clicked: false,
    };
  },
};
</script>

<style scoped>
.greenColor {
  color: green;
}
.orangeColor {
  color: orange;
}
li {
  list-style-type: none;
}
li::before {
  content: "♪ ";
}
li::after {
  content: " ♫";
}
</style>
