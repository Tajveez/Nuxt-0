<template>
  <div>
    <SearchByAuthor @search-text="searchByAuthor" />
    <div class="title" style="font-size: 32px">List of Quotes</div>
    <Quote
      v-for="quote in quotes"
      :key="quote._id"
      :id="quote._id"
      :quote="quote.content"
      :author="quote.author"
    />
  </div>
</template>

<script>
import axios from "axios";
import Quote from "~/components/Quote";
import SearchByAuthor from "~/components/SearchByAuthor";

export default {
  components: {
    Quote,
    SearchByAuthor
  },
  data() {
    return {
      quotes: []
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
        "https://api.quotable.io/quotes?limit=10",
        config
      );
      console.log(result);
      this.quotes = result.data.results;
    } catch (error) {
      console.log(error);
    }
  },
  methods: {
    async searchByAuthor(text) {
      const config = {
        header: {
          Accept: "application/json"
        }
      };
      try {
        const result = await axios.get(
          `https://api.quotable.io/quotes?author=${text}`,
          config
        );
        console.log(result);
        this.quotes = result.data.results;
      } catch (error) {
        console.log(error);
      }
    }
  },
  head() {
    return {
      title: "Inspirational Quote",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Cool site for inspirational quotes"
        }
      ]
    };
  },
  name: "quote"
};
</script>

<style>
</style>