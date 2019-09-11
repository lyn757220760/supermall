<template>
  <div>
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners='banners'></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar"
import {getHomeMultidata} from "network/home"

import HomeSwiper from "views/home/childComps/HomeSwiper"
import RecommendView from "views/home/childComps/RecommendView"

export default {
  name: "Home",
  components: {
    NavBar,
    HomeSwiper,
    RecommendView
  },
  data() {
    return {
      banners: [],
      recommends: []
    }
  },
  created() {
    getHomeMultidata().then(res => {
      console.log(res);
      this.banners = res.data.data.banner.list;
      this.recommends = res.data.data.recommend.list;
    })
  }
}
</script>

<style>
  .home-nav {
    background-color: #ff8198;
    color: #fff;
  }
</style>