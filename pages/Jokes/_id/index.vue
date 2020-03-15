<template>
  <div>
    <div><nuxt-link to="/jokes">Back to Jokes</nuxt-link></div>
    <div>{{ joke }}</div>
    <div>Joke ID: {{ $route.params.id }}</div>
  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    data() {
      return {
        id: '',
        joke: ''
      }
    },

    methods: {
      async getJoke() {
        let response;

        try {
          response = await this.$axios({
            method: 'get',
            url: `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
            headers: {
              Accept: 'application/json'
            }
          });
        } catch (e) {
          console.log(e);
          return;
        }
        console.log(response.data.id);
        this.joke = response.data.joke;
      }
    },

    mounted() {
      //this.id = this.$route.params.id;
      //console.log(this.id);
      this.getJoke();
    },
  }


</script>
