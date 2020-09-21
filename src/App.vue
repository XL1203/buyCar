<template>
  <div id="app">
    <my-car></my-car>
  </div>
</template>

<script>
import myCar from './components/myCar'

export default {
  components: {
    'my-car':myCar
  }
}

</script>

<style lang="less" scoped>
#app {
  position: relative;
  width: 400px;
  margin: 0 auto;
}
</style>