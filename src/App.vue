<template>
  <div id="app">

    <h1>Vuemon</h1>

    <div id="simon">

      <div class="row">
        <div id="green" class="button col"></div>
        <div id="red" class="button col"></div>
      </div>

      <div class="row">
        <div id="yellow" class="button col"></div>
        <div id="blue" class="button col"></div>
      </div>

    </div>

    <div id="status">
      <p><strong>Current Sequence:</strong> {{ current }}</p>
      <p><strong>Longest Sequence:</strong> {{ longest }}</p>
    </div>

  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

#simon {
  padding: 20px;
}

.row {

}

.col {
  display: inline-block;
}

.button {
  margin: 20px;
}

#red {
  height: 100px;
  width: 100px;
  background: #E53A40;
}

#yellow {
  height: 100px;
  width: 100px;
  background: #EFDC05;
}

#green {
  height: 100px;
  width: 100px;
  background: #75D701;
}

#blue {
  height: 100px;
  width: 100px;
  background: #30A9DE;
}




</style>
