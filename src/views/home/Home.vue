<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"/>
    <feature-view/>
    <tab-control class="tab-control" :titles="['流行','新款','精选']" @tabClick="itemClick"/>
    <good-list :goodList="this.goods[type].list"/>
    <ul>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
      <li>笨蛋</li>
    </ul>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import TabControl from "components/content/tabcontrol/TabControl"
import GoodList from "components/content/goods/GoodList";

import HomeSwiper from './homeChildren/HomeSwiper'
import RecommendView from './homeChildren/RecommendView'
import FeatureView from './homeChildren/FeatureView'

import {getMultiData,getHomeGoods} from "network/home/home";


export default {
  name: "Home",
  components: {
    NavBar,
    TabControl,
    GoodList,
    HomeSwiper,
    RecommendView,
    FeatureView
  },
  data(){
    return{
      banners: null,
      recommends: null,
      features: null,
      type: 'pop',
      goods: {
        pop: {page: 0,list: []},
        new: {page: 0,list: []},
        sell: {page: 0,list: []}
      }
    }
  },
  created() {
    this.getMultiData(),
    this.getHomeGoods('pop',0)
    this.getHomeGoods('new',0)
    this.getHomeGoods('sell',0)


  },
  methods: {
    itemClick(index){
      console.log('=================='+index+'=================')
      switch (index){
        case 0: {
          this.type = 'pop';
          break
        };
        case 1: {
          this.type = 'new';
          break
        }
        case 2: {
          this.type = 'sell';
          break
        }
      }
    },
    getMultiData(){
      getMultiData().then(res => {
        this.banners = res.data.banner.list
        this.recommends = res.data.recommend.list
        this.features = res
      })
    },
    getHomeGoods(type,page){
      getHomeGoods(type,page+1).then(res => {
        console.log(res)
        this.goods[type].list = res.data.list
      })
    }
  }
}
</script>

<style>
  #home{
    padding-top: 44px;

  }
  .home-nav{
    background-color: var(--color-tint);
    color: white;
    left: 0;
    right: 0;
    top: 0;
    position: fixed;
    z-index: 9;
  }
  .tab-control{
    position: sticky;
    top: 44px;
    z-index: 9;
  }
</style>
