<template>

  <div class="flex mb-10 justify-center bottom-0 flex-wrap">
<!--    <div @click="previousPage()" class="rounded-full bg-color-blue"> <<</div>-->
    <div class="p-1 m-1 rounded-full bg-blue-400" v-for="pg in totalPages" @click="goToPage(pg)">{{ pg }}</div>
<!--    <div @click="nextPage()"> >></div>-->
  </div>


</template>

<script>
  export default {
    name: 'JokePageNav',
    props: ['page', 'totalPages'],
    data() {
      return {
        gotopage: ''
      }

    },
    methods: {
      nextPage() {
        this.gotopage = this.props.page +1;
        this.sendResp();
      },
      previousPage() {
        this.gotopage = this.props.page;
        if (this.page > 1) {
          this.gotopage = this.props.page -1;
        }
        this.sendResp();
      },
      goToPage(num){
        this.gotopage = num;
        this.sendResp();
      },

      sendResp(){
        this.$emit('page-to-show', this.gotopage);
      }
    }
  }


</script>
