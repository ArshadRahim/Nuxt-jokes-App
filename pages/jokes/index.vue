<template>
  <div>
<h1>Lame Jokes</h1>

<Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke" />
  </div>
</template>

<script>
import axios from "axios";
import Joke from "../../components/Joke.vue";
  export default {
    components: { 
      Joke
      },
    data () {
      return {
        jokes: []
      }
    },

     async created () {
      const config = {
        headers : {
          'Accept': 'application/json'
        }
      }
      try {
        const response = await axios.get('https://icanhazdadjoke.com/search', config);
        this.jokes = response.data.results;
      }
      catch(err) {
        console.log(err)
      }
    },
      head() {
      return {
        title: 'Jokes'
      }
      },
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Jokes you need are here !"
        }
      ]
  }
</script>

<style lang="scss" scoped>

</style>