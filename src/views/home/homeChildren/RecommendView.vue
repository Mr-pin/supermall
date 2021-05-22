<template>
  <div class="recommend">
    <div v-for="item in recommends" class="recommend-item">
      <a  :href="item.link">
        <img :src="item.image">
        <p>{{item.title}}</p>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "RecommendView",
  props: {
    recommends:{
      type: Array,
      default() {
        return [];
      }
    }
  }
}
</script>

<style scoped>
.recommend{
  width: 100%;
  display: flex;
  text-align: center;
  padding: 10px 0 15px;
  font-size: 13px;
  border-bottom: 10px solid #eee;

}
.recommend-item {
  flex: 1
}
.recommend-item img{
  width: 80px;
  height: 80px;
  margin-bottom: 10px;
}
</style>
