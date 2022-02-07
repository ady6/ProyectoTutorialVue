<template>
  <h2>Grandes jugadores NBA</h2>
  <p>{{msg}} - {{autor}}</p>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    autor: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h2 {
    color:magenta;
  }
</style>
