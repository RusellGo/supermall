<template>
  <div id="home">
    <nav-bar class="home-nav">
      <template v-slot:center>购物街</template>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar.vue";
import HomeSwiper from "./childComps/HomeSwiper.vue";
import RecommendView from "./childComps/RecommendView.vue";
import { getHomeMultidata } from "network/home.js";

export default {
  name: "Home",
  components: {
    "nav-bar": NavBar,
    "home-swiper": HomeSwiper,
    "recommend-view": RecommendView
  },
  data() {
    return {
      banners: [],
      recommends: []
    };
  },
  created() {
    // 1.请求多个数据
    getHomeMultidata().then(result => {
      this.banners = result.data.banner.list;
      this.recommends = result.data.recommend.list;
    });
  }
};
</script>

<style>
.home-nav {
  background-color: var(--color-tint);
  color: #fff;
}
</style>