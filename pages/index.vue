<template>
  <div>
    <div>
      <h1 class="title">Welcome to Inspirational Quote App</h1>
      <p>Quote of the Day:</p>
      <Quote :id="id" :quote="quote" :author="author" />
    </div>
  </div>
</template>

<script>
import Quote from "~/components/Quote.vue";
import axios from "axios";

export default {
  head() {
    return {
      title: "Welcome to Inspirational Quote App",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Cool site for inspirational quotes"
        }
      ]
    };
  },
  data() {
    return {
      id: null,
      quote: null,
      author: null
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
        "https://api.quotable.io/random?limit=10",
        config
      );
      console.log(result);
      this.author = result.data.author;
      this.quote = result.data.content;
      this.id = result.data._id;
    } catch (error) {
      console.log(error);
    }
  },
  components: {
    Quote
  }
};
</script>

<style>
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 35px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
