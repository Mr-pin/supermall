<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive"><slot name="img-icon"></slot></div>
    <div v-else><slot name="img-icon-active"></slot></div>
    <!--<div :style="{color:isActive?fontColor:''}"><slot name="text-icon"></slot></div>-->
    <div :style=fontStyle ><slot name="text-icon"></slot></div>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props: {
    path: '',
    fontColor: {
      type: String,
      default: 'blue'
    }
  },
  data() {
    return {
    }
  },
  computed: {
    isActive(){
      return this.$route.path.indexOf(this.path)!=-1
    },
    fontStyle(){
      return this.isActive?{color:this.fontColor}:{}
    }
  },
  methods: {
    itemClick() {
      this.$router.replace(this.path)
    }
  }
}
</script>
<style scoped>
.active{
  color: deeppink;
}
.tab-bar-item img {
  width: 24px;
  height: 24px;
  margin-top: 3px;
  margin-bottom: 2px;
}
.tab-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;
}
</style>
