<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <router-view></router-view> -->
    <p>{{ title }} <a v-bind:href="link">google</a></p>
    <hr>
    <!-- Using v-html method to create an ancor tag within the p tag -->
    <p v-html="toGoogle"></p>
    <hr>
    <!-- Changing State via on click method and displaying it on page -->
    <button v-on:click="addition">Button</button>
    <p>{{ myNum }}</p>
    <hr>
    <!-- using other v-on methods to minipluate displayed data -->
    <p v-on:mousemove="coordinates">X and Y Coordinates are: X: {{ x }} Y: {{ y }}
      <span v-on:mousemove.stop="">STOP LISTENING TO COORDINATES</span>
   </p>
   <input type="text" v-on:keyup.enter="alertUser">
   <hr>
   <input type="text" v-on:keyup.enter="submit">
   <p>{{ value }}</p>
   <hr>
   <!-- Using v-model for 2 way data binding -->
   <input type="text" v-model="title">
   <p>{{ title }}</p>
   <hr>
   <!-- Trying v-if and v-else methods to minipluate the DOM -->
   <p v-if="show">Show Some Text</p>
   <p v-else>Show some Different Text</p>
   <button @click="show = !show">Button</button>
   <hr>
   <!-- Using v-for to map out an array and displaying them in li tags -->
   <ul>
      <li v-for="(person, index) in people">{{ index }}. {{ person }}</li>
      <span v-for="n in 10">{{ n }}</span>
   </ul>
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
      value: '',
      show: true,
      people: ['David', 'Nick', 'Garrett', 'Danielle']
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
}
</style>
