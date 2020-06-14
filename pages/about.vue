<template>
  <div>
    <h1>This is about page</h1>
    <p>This App is about Some daily qoutes</p>
    <!-- <a href="/">Home</a> -->
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "About Page",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Cool site for inspirational quotes"
        }
      ]
    };
  },
  name: "about"
};
</script>

<style>
body {
  padding: 5px;
}
</style>