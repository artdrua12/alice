<template>
  <div class="wrapper">
    <input v-model="text" />
    <button @click="onClick">Расшифровать</button>
    <h2>{{ message }}</h2>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      text: "wwaldaadicffenn",
      message: "",
    };
  },
  methods: {
    decrypt(str) {
      return str.replace(/(.)\1(?<!\1{3})(?!\1)/g, "");
    },
    onClick() {
      this.message = this.text;
      while (/(.)\1(?<!\1{3})(?!\1)/g.test(this.message)) {
        this.message = this.decrypt(this.message);
      }
    },
  },
};
</script>

<style scoped>
.wrapper {
  margin: auto;
}
</style>
