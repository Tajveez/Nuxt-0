<template>
  <div>
    <nuxt-link to="/quotes">Back to quotes</nuxt-link>
    <div class="title" v-if="id">
      <i>{{quote}}</i>
      <br />by
      <strong>{{author}}</strong>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      id: null,
      author: null,
      quote: null
    };
  },
  head() {
    return {
      title: this.quote,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Cool site for inspirational quotes"
        }
      ]
    };
  },
  async created() {
    const config = {
      header: {
        Accept: "application/json"
      }
    };
    try {
      const result = await axios.get(
        `https://api.quotable.io/quotes/${this.$route.params.id}`,
        config
      );
      console.log(result);
      this.author = result.data.author;
      this.quote = result.data.content;
      this.id = result.data._id;
    } catch (error) {
      console.log(error);
    }
  }
};
</script>

<style>
</style>