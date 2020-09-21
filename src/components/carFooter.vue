<template>
  <footer id="footer">
    <div class="total">
      <span>总价: {{sum}}</span>
      <button>结算</button>
    </div>
  </footer>
</template>

<script>
export default {
  props: ["list"],
  data(){
      return {
          shopList:this.list
      }
  },
  computed: {
    sum() {
      var sum = 0;
      this.shopList.forEach((item) => {
        sum += item.price * item.num;
      });
      return sum;
    },
  },
};
</script>

<style lang="less" scoped>
#footer {
  width: 100%;
  height: 60px;
  line-height: 60px;
  background-color: #ffce46;

  .total {
    width: 100%;
    text-align: right;
    background-color: #ffce46;

    span {
      font-size: 20px;
      color: #ff2726;
    }

    button {
      margin: 0 20px;
      width: 80px;
      height: 30px;
      border: none;
      background-color: #dc4c40;
    }
  }
}
</style>