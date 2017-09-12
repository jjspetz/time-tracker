<template>
  <div class="jumbotron">
    <h1>Time Tracker</h1>
    <p>
      <strong>
        Get started by <router-link tag="a" to="/time-entries/log-time">creating a time entry</router-link>.
      </strong>
    </p>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
</style>
