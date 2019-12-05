<template>
  <div id="home">
    <div class="wrapper">
      <div class="content">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
        <div class="item">4</div>
        <div class="item">5</div>
        <div class="item">6</div>
        <div class="item">7</div>
        <div class="item">8</div>
        <div class="item">9</div>
        <div class="item">10</div>
        <div class="item">11</div>
        <div class="item">12</div>
        <div class="item">13</div>
        <div class="item">14</div>
        <div class="item">15</div>
        <div class="item">16</div>
        <div class="item">17</div>
        <div class="item">18</div>
        <div class="item">19</div>
        <div class="item">20</div>
      </div>
    </div>
    <div class="backTop" @click="topClick" v-show="showTop">backTop</div>
  </div>
</template>

<script>
import BScroll from "better-scroll";

export default {
  name: "Home",
  components: {},
  data() {
    return {
      scroll: null,
      showTop: false,
    }
  },
  methods: {
    topClick() {
      this.scroll.scrollTo(0, 0, 500)
    },
  },
  mounted() {
    // 1. 创建BScroll对象
    this.scroll = new BScroll('.wrapper', {
      // click: true,
      probeType: 3, // 监听类型
      pullUpLoad: {threshold: -1}
    });
    // 2. 监听滚动位置
    this.scroll.on("scroll", position => {
      this.showTop = position.y < -100
    });
    // 3. 监听上拉加载
    this.scroll.on("pullingUp", () => {
      console.log('pull up load')
      setTimeout(() => {
        // alert('pulled up')  // 用于手机端测试
        this.scroll.finishPullUp()
      }, 2000)
    });
  },
};
</script>

<style>
#home {
  background-color: #ccc;
}
.wrapper {
  overflow: hidden;
  height: 500px;
}
.item {
  height: 50px;
  line-height: 50px;
  text-align: center;
  margin: 10px 0;
  background-color:#ddd;
}
.backTop {
  position: fixed;
  height: 50px;
  top: 100px;
  left: 100px;
  background-color: #fff;
}
</style>