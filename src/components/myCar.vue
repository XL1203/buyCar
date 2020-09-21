<template>
  <div class="container">
    <car-tittle :uname="uname"></car-tittle>
    <car-content :list="list" @car-del="delItem" @change-num="changeItemNum"></car-content>
    <car-footer :list="list"></car-footer>
  </div>
</template>


<script>
import carTittle from "./carTittle";
import carContent from "./carContent";
import carFooter from "./carFooter";

export default {
  data() {
    return {
      uname: "张三",
      list: [
        {
          id: 1,
          name: "TCL彩电",
          price: 1000,
          num: 1,
          pic: "../assets/images/a.jpg",
        },
        {
          id: 2,
          name: "机顶盒",
          price: 1000,
          num: 1,
          img: "../assets/images/b.jpg",
        },
        {
          id: 3,
          name: "海尔冰箱",
          price: 1000,
          num: 1,
          img: "../assets/images/c.jpg",
        },
        {
          id: 4,
          name: "小米手机",
          price: 1000,
          num: 1,
          img: "../assets/images/d.jpg",
        },
        {
          id: 5,
          name: "PPTV电视",
          price: 1000,
          num: 1,
          img: "../assets/images/e.jpg",
        },
      ],
    };
  },
  methods: {
    changeItemNum(param) {
      if (param.type === "sub") {
        this.list.some((item) => {
          if (item.id === param.id && item.num > 0) {
            item.num -= 1;
            return true;
          }
        });
      } else if (param.type === "add") {
        this.list.some((item) => {
          if (item.id === param.id) {
            item.num += 1;
            return true;
          }
        });
      } else {
        this.list.some((item) => {
          if (item.id === param.id) {
            item.num = param.num;
            return true;
          }
        });
      }
    },
    delItem(id) {
      var index = this.list.findIndex((item) => {
        return item.id === id;
      });
      this.list.splice(index, 1);
    },
  },
  components: {
    "car-tittle": carTittle,
    "car-content": carContent,
    "car-footer": carFooter,
  },
};
</script>   

<style lang="less" scoped>
.container {
  width: 100%;
  height: 100%;
}
</style>
