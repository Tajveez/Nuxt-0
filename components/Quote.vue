<template>
  <nuxt-link :to="'quotes/'+id">
    <div class="quote">
      <p>
        <i>{{quote}}</i> -
        <strong>{{author}}</strong>
      </p>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: "Quote",
  props: ["id", "quote", "author"]
};
</script>

<style>
.quote {
  padding: 1rem;
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
</style>