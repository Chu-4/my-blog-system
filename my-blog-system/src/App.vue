<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  mounted () {
    this.$http.post(process.webServerHost + '/api/auth/current')
      .then(res => {
        const {data} = res
        this.$store.commit('SET_USER', data)
      })
      .catch(err => {
        console.error(err)
        this.$store.commit('SET_USER', null)
      })
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
