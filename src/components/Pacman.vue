<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div id="pacman"></div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #pacman {
    width: 0;
    height: 0;
    border-right: 70px solid transparent;
    border-top: 70px solid #ffde00;
    border-left: 70px solid #ffde00;
    border-bottom: 70px solid #ffde00;
    border-top-left-radius: 70px;
    border-top-right-radius: 70px;
    border-bottom-left-radius: 70px;
    border-bottom-right-radius: 70px;
  }
</style>
