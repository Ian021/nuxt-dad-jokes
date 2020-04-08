<template>
  <div>
    <SearchInput
      @search-text="SearchInput"
    />
    <JokeComponent
      v-for="joke in jokes"
      :id="joke.id"
      :key="joke.id"
      :joke="joke.joke"
    />
    <!-- <div v-for="joke in jokes" :key="joke.id">
      {{ joke.joke }}
    </div> -->
  </div>
</template>

<script>
import axios from 'axios'
import JokeComponent from '../../components/Joke'
import SearchInput from '../../components/SearchInput'

export default {
  components: {
    JokeComponent,
    SearchInput
  },

  data () {
    return {
      jokes: []
    }
  },

  async created () {
    const config = {
      headers: {
        Accept: 'application/json'
      }
    }

    try {
      const res = await axios.get('https://icanhazdadjoke.com/search', config)

      this.jokes = res.data.results
    } catch (err) {
      alert(err)
    }
  },

  methods: {
    async SearchInput (text) {
      const config = {
        headers: {
          Accept: 'application/json'
        }
      }
      try {
        const res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config)
        this.jokes = res.data.results
      } catch (err) {
        alert(err)
      }
    }
  },

  head () {
    return {
      title: 'Jokes',
      meta: [
        {
          hid: 'description-jokes',
          name: 'description-name',
          content: 'Best place for dad jokes'
        }
      ]
    }
  }
}
</script>

<style>

</style>
