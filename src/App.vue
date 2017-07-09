<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <router-view></router-view> -->
    <p>{{ title }} <a v-bind:href="link">google</a></p>
    <hr>
    <p v-html="toGoogle"></p>
    <hr>
    <button v-on:click="addition">Button</button>
    <p>{{ myNum }}</p>
    <hr>
    <p v-on:mousemove="coordinates">X and Y Coordinates are: X: {{ x }} Y: {{ y }}
      <span v-on:mousemove.stop="">STOP LISTENING TO COORDINATES</span>
   </p>
   <input type="text" v-on:keyup.enter="alertUser">
   <hr>
   <input type="text" v-on:keyup.enter="submit">
   <p>{{ value }}</p>
  </div>

</template>

<script>
export default {
  data: () => {
    return {
      title: 'hello from the other side',
      link: 'http://www.google.com',
      toGoogle: '<a href="http://www.google.com">Google</a>',
      myNum: 0,
      x: 0,
      y: 0,
      value: ''
    }
  },
  methods: {
     addition() {
        this.myNum++
     },
     coordinates(event) {
        this.x = event.clientX;
        this.y = event.clientY;
     },
     stop(event) {
        event.stopPropagation();
     },
     alertUser() {
        alert('STOP')
     },
     submit(event) {
        this.value = event.target.value
     }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
