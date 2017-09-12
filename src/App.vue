<template>
  <div id="wrapper">
    <nav class="navbar navbar-default">
      <div class="container">
        <a class="navbar-brand" href="#">
          <i class="glyphicon glyphicon-time"></i>
          Vue Time Tracker
        </a>
        <ul class="nav navbar-nav">
          <router-link tag="li" to="/"><a>Home</a></router-link>
          <router-link tag="li" to="/time-entries"><a>Time Entries</a></router-link>
        </ul>
      </div>
    </nav>
    <div class="container">
      <div class="col-sm-3">
        <sidebar v-bind:time="totalTime"></sidebar>
      </div>
      <div class="col-sm-9">
        <router-view></router-view>
      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from './components/Sidebar'
import eventHub from './EventHub'

  export default {
    components: { 'sidebar': Sidebar },
    data () {
      return {
        totalTime: 0
      }
    },
    created: function () {
      eventHub.$on('save', this.count)
      eventHub.$on('delete-time', this.deleteTime)
    },
    beforeDestroy: function () {
      eventHub.$off('save', this.count)
      eventHub.$off('delete-time', this.deleteTime)
    },
    methods: {
      count(timeEntry) {
        this.totalTime += parseFloat(timeEntry.totalTime)
      },
      deleteTime(time) {
        this.totalTime -= parseFloat(time)
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
