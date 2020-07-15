<template>
  <div id="home">
    <nav-bar class="home-nav">
      <template v-slot:center>购物街</template>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feature-view></feature-view>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar.vue";
import HomeSwiper from "./childComps/HomeSwiper.vue";
import RecommendView from "./childComps/RecommendView.vue";
import FeatureView from "./childComps/FeatureView.vue";

import { getHomeMultidata } from "network/home.js";

export default {
  name: "Home",
  components: {
    "nav-bar": NavBar,
    "home-swiper": HomeSwiper,
    "recommend-view": RecommendView,
    "feature-view": FeatureView
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
#home {
  padding: 44px 0 54px;
}
.home-nav {
  position: fixed;
  left: 0;
  top: 0;
  right: 0;
  background-color: var(--color-tint);
  color: #fff;
  z-index: 999;
}
</style>