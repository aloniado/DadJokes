<template>

  <nuxt-link :to="'jokes/' + id">
    <div class="bg-gray-200 border border-gray-500 rounded shadow-lg p-6 py-3 m-auto mb-5">


      {{ joke }}


    </div>
  </nuxt-link>


</template>

<script>
  export default {
    name: 'Joke',
    props: ['joke', 'id']
  }


</script>
