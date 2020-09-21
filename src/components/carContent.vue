<template>
  <section id="content">
    <div class="item" v-for="item in shopping" :key="item.id">
      <img src="item.img" />
      <div class="name">{{item.name}}</div>
      <div class="change">
        <button @click.prevent="sub(item.id)">-</button>
        <input class="ipt" type="text" :value="item.num" @blur="changeNum(item.id,$event)"/>
        <button @click.prevent="add(item.id)">+</button>
      </div>
      <div class="del" @click.prevent="del(item.id)">x</div>
    </div>
  </section>
</template>

<script>
export default {
  props: ["list"],
  data() {
    return {
        shopping:this.list
    }
  },
  methods:{
      sub(id){
          this.$emit('change-num',{
              type:'sub',
              id:id
          })
      },
      add(id){
           this.$emit('change-num',{
              type:'add',
              id:id
          })
      },
      changeNum(id,params){
          this.$emit('change-num',{
              id:id,
              type:'change',
              num:params.target.value
          })
      },
      del(id){
          this.$emit('car-del',id)
      }
  }
};
</script>

<style lang="less" scoped>
ul {
  padding: 0;
  margin: 0;
}

li {
  list-style: none;
}

#content {
  width: 100%;

  .item {
    position: relative;
    height: 60px;
    line-height: 60px;
    border-bottom: 1px solid #add8e6;

    img {
      width: 50px;
      height: 50px;
      margin: 5px;
    }

    .name {
      position: absolute;
      top: 0;
      left: 70px;
      width: 80px;
    }

    .change {
      position: absolute;
      top: 0;
      left: 180px;
      width: 120px;
    }

    button {
      display: inline-block;
      font-size: 20px;
      width: 26px;
      height: 26px;
      margin: 0 3px;
      line-height: 14px;
      text-align: center;
      cursor: pointer;
    }

    .ipt {
      display: inline-block;
      width: 40px;
      height: 26px;
      font-size: 18px;
      text-align: center;
    }

    .del {
      position: absolute;
      top: 10px;
      right: 10px;
      width: 40px;
      height: 40px;
      line-height: 35px;
      text-align: center;
      vertical-align: middle;
      font-size: 40px;
      color: red;
      cursor: pointer;
    }

    .del:hover {
      background-color: salmon;
    }
  }
}
</style>