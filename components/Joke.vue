<template>
  <div class="joke">
    <nuxt-link :to="'jokes/' + id">
      <p>
        {{ joke }}
      </p>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'JokeComponent',
  props: {
    joke: {
      type: String,
      default: ''
    },
    id: {
      type: String,
      default: ''
    }
  }
}
</script>

<style>
  .joke {
    padding: 1rem;
    border: 1px dotted #ccc;
    margin: 1rem 0;
  }
</style>
