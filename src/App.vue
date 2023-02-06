<template>
  <div>
    <!-- <h1 v-upper.erha="msg"></h1> -->
    <Header></Header>
    <!-- 路由组件出口的地方 -->
    <router-view></router-view>
    <!-- 在Home、Search显示，在登录、注册隐藏 -->
    <Footer v-show="$route.meta.show"></Footer>
  </div>
</template>

<script>
import Header from "./components/Header/index";
import Footer from "./components/Footer/index";
export default {
  name: "app",
  data() {
    return {
      msg: 'abc'
    }
  },
  components: { Header, Footer },
  mounted(){
    //派发一个action||获取商品分类的三级列表的数据
    //通知vuex发请求，获取数据，存储于仓库当中
    this.$store.dispatch("categoryList"); 
  }
};
</script>

<style></style>
