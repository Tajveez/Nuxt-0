<template>
  <form @submit.prevent="OnSubmit">
    <input type="text" v-model="text" placeholder="Search Quotes by Author" />
    <input type="submit" class="btn" value="Search Quotes" />
  </form>
</template>

<script>
export default {
  data() {
    return {
      text: ""
    };
  },
  methods: {
    OnSubmit() {
      this.$emit("search-text", this.text);
      this.text = "";
    }
  }
};
</script>

<style>
input[type="text"] {
  width: 50%;
  height: 30px;
}
.btn {
  height: 30px;
  padding: 5px;
  background: gray;
  border: 0px;
  color: white;
}
</style>