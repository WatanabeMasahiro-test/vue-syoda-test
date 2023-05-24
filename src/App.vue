<template>
  <div class="container">
    <h1>Vue3</h1>
    <div class="scss-border alert-warning">
      <p>{{ message.toUpperCase() }}
        <span class="mx-1 bg-info">【{{ new Date().toLocaleString() }}】</span>
      </p>
      <button
        @click='(stop=true)'
        class="scss-border--button">
        <span class="scss-border--button__text">Stop</span>
      </button>
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

<style lang="scss" scoped>
$border-color: red;

@mixin modifier($color){
  color: $color;
  font-size: 1.5em;
}
.scss-border {
  border: 3px double $border-color;
  border-radius: 1em;
  padding: 10px;
  &--button {
    background-color: rgb(255, 136, 0);
    &__text {
      @include modifier(blue);
    }
  }
}
</style>
