<template>
  <div>
<h1>Jokes</h1>
  </div>
</template>

<script>
import axios from "axios"
  export default {
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