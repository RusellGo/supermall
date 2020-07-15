<template>
  <div id="home">
    <nav-bar class="home-nav">
      <template v-slot:center>购物街</template>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feature-view></feature-view>
    <tab-control :titles="['流行', '新款', '精选']" class="tab-control"></tab-control>

    <ul>
      <li>占位1</li>
      <li>占位2</li>
      <li>占位3</li>
      <li>占位4</li>
      <li>占位5</li>
      <li>占位6</li>
      <li>占位7</li>
      <li>占位8</li>
      <li>占位9</li>
      <li>占位10</li>
      <li>占位11</li>
      <li>占位12</li>
      <li>占位13</li>
      <li>占位14</li>
      <li>占位15</li>
      <li>占位16</li>
      <li>占位17</li>
      <li>占位18</li>
      <li>占位19</li>
      <li>占位20</li>
      <li>占位21</li>
      <li>占位22</li>
      <li>占位23</li>
      <li>占位24</li>
      <li>占位25</li>
      <li>占位26</li>
      <li>占位27</li>
      <li>占位28</li>
      <li>占位29</li>
      <li>占位30</li>
      <li>占位31</li>
      <li>占位32</li>
      <li>占位33</li>
      <li>占位34</li>
      <li>占位35</li>
      <li>占位36</li>
      <li>占位37</li>
      <li>占位38</li>
      <li>占位39</li>
      <li>占位40</li>
      <li>占位41</li>
      <li>占位42</li>
      <li>占位43</li>
      <li>占位44</li>
      <li>占位45</li>
      <li>占位46</li>
      <li>占位47</li>
      <li>占位48</li>
      <li>占位49</li>
      <li>占位50</li>
    </ul>
  </div>
</template>

<script>
// Home页面的子组件
import HomeSwiper from "./childComps/HomeSwiper.vue";
import RecommendView from "./childComps/RecommendView.vue";
import FeatureView from "./childComps/FeatureView.vue";

// 公共组件
import NavBar from "components/common/navbar/NavBar.vue";
import TabControl from "components/content/tabControl/TabControl.vue";

import { getHomeMultidata } from "network/home.js";

export default {
  name: "Home",
  components: {
    "home-swiper": HomeSwiper,
    "recommend-view": RecommendView,
    "feature-view": FeatureView,
    "nav-bar": NavBar,
    "tab-control": TabControl
  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods: {
        pops: { page: 0, list: [] },
        news: { page: 0, list: [] },
        sells: { page: 0, list: [] }
      }
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
.tab-control {
  position: sticky;
  top: 44px;
}
</style>