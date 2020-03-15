<template>
  <div>
    <SearchJokes v-on:search-text="SearchText"/>
    <div class="bg-gray-100 content-center p-5 m-auto">
      <Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"/>
    </div>

      <JokePageNav v-on:page-to-show="getJokes" :totalPages="totalPages" />
  </div>
</template>

<script>
  import axios from 'axios';
  import Joke from '~/components/Joke'
  import SearchJokes from '~/components/SearchJokes'
  import JokePageNav from '~/components/JokePageNav'

  export default {
    components: {
      Joke,
      SearchJokes,
      JokePageNav
    },
    data() {
      return {
        jokes: [],
        totalJokes: 0,
        totalPages: 0,
        page: 1
      }
    },

    methods: {
      async getJokes(pagenum) {
        let response;

        try {
          response = await this.$axios({
            method: 'get',
            url: 'https://icanhazdadjoke.com/search',
            headers: {
              Accept: 'application/json'
            },
            params: {
              page: pagenum,
              limit: '10'
            }
          });
        } catch (e) {
          console.log(e);
          return;
        }
        this.page = pagenum;
        console.log(response);
        this.totalJokes = response.data.total_jokes;
        this.jokes = response.data.results;

        this.totalPages = Math.floor(this.totalJokes / 10);
      },

      async SearchText(text) {
        let response;

        try {
          response = await this.$axios({
            method: 'get',
            url: 'https://icanhazdadjoke.com/search',
            headers: {
              Accept: 'application/json'
            },
            params: {
              term: text,
            }
          });
        } catch (e) {
          console.log(e);
          return;
        }
        console.log(response.data.results);
        this.jokes = response.data.results;
      },




    },
    mounted() {
      this.getJokes(this.page);
    },


    head() {
      return {
        title: 'Dad Jokes',
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: 'Best place for dad jokes'
          }
        ]
      }
    }
  }


</script>
