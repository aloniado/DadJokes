<template>
  <div>
    <header class="header">
      <div class="flex justify-center title w-full bg-orange-300 shadow-lg p-3 text-2xl font-bold font-mono">DadJokes</div>

      <div class="flex justify-center bg-orange-200 p-3">
        <div class="rounded-full text-gray-700 text-center bg-orange-300 shadow-lg px-4 py-2 m-2">
          <nuxt-link to="/">Home</nuxt-link>
        </div>
        <div class="rounded-full text-gray-700 text-center bg-orange-300 shadow-lg px-4 py-2 m-2">
          <nuxt-link to="/jokes">Jokes</nuxt-link>
        </div>
        <div class="rounded-full text-gray-700 text-center bg-orange-300 shadow-lg px-4 py-2 m-2">
          <nuxt-link to="/about">About</nuxt-link>
        </div>
      </div>
    </header>

  </div>
</template>

<script>
  export default {
    name: 'AppHeader'
  };


</script>
