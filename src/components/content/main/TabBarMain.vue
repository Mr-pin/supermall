<template>
  <tab-bar>
    <tab-bar-item  path="/home" fontColor="deeppink">
      <img slot="img-icon" src="~assets/img/tabbar/home.svg">
      <img slot="img-icon-active" src="~assets/img/tabbar/home_active.svg">
      <div slot="text-icon">
        首页
      </div>
    </tab-bar-item>
    <tab-bar-item  path="/category" fontColor="deeppink">
      <img slot="img-icon" src="~assets/img/tabbar/category.svg">
      <img slot="img-icon-active" src="~assets/img/tabbar/category_active.svg">
      <div slot="text-icon">
        分类
      </div>
    </tab-bar-item>
    <tab-bar-item  path="/cart" fontColor="deeppink">
      <img slot="img-icon" src="~assets/img/tabbar/shopcart.svg">
      <img slot="img-icon-active" src="~assets/img/tabbar/shopcart_active.svg">
      <div slot="text-icon">
        购物车
      </div>
    </tab-bar-item>
    <tab-bar-item path="/profile" fontColor="deeppink">
      <img slot="img-icon" src="~assets/img/tabbar/profile.svg">
      <img slot="img-icon-active" src="~assets/img/tabbar/profile_active.svg">
      <div slot="text-icon">
        我的
      </div>
    </tab-bar-item>
  </tab-bar>
</template>

<script>
import TabBar from "components/common/tabbar/TabBar";
import TabBarItem from "components/common/tabbar/TabBarItem";
export default {
  name: "TabBarMain",
  components: {
    TabBar,
    TabBarItem
  }
}
</script>

<style scoped>

</style>
