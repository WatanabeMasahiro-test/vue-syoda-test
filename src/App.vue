<template>
  <div class="container">
    <h1>Vue3</h1>
    <div>
      <p>{{ message.toUpperCase() }}<span class="mx-1 bg-info">【{{ new Date().toLocaleString() }}】</span></p>
      <button @click='stop = true'>Stop</button>
    </div>
  </div>
</template>

<script>
  import './assets/animate.css/animate.min.css'
  import './assets/css/style.css'

  export default {
    name: 'App',
    components: {

    },
    data: () => ({
      message : 'Hello Vue!',
      count   : 0,
      stop    : false,
    }),
    computed: {},
    methods: {
    },
    mounted() {
      let countUp = setInterval(() => {
        this.count++;
        this.message = 'Count: ' + this.count;
        if(this.stop) clearInterval(countUp);
        if(this.count > 10) {
          clearInterval(countUp);
          this.message = 'Hello Vue!';
        }
      }, 1000)

    }
  }
</script>

<style scoped>
</style>
