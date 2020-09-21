<template>
  <header id="header">
    <h2>{{uname}}的商品列表</h2>
  </header>
</template>

<script>
export default {
  props: ["uname"]
};
</script>

<style lang="less" scoped>
#header {
  width: 100%;
  height: 60px;
  line-height: 60px;
  text-align: center;
  background-color: #add8e6;
}
</style>