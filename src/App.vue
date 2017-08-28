<template>
  <div id="app">
    <input type="button" value="Get Request" @click="get">
    <div name="result"></div>
  </div>
</template>

<script>
export default {
  methods: {
    get () {
      this.$http.get('/api/ajax', { params: { sendMsg: 'Get request here' } }).then(
        (r) => {
          if (r.body.msg) {
            this.$el.querySelector('div[name=result]').innerText = r.body.msg;
          }
        },
        (r) => {
          console.log('fail');
        }
      )
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
div[name=result] {
  margin-top: 10px;
}
</style>
