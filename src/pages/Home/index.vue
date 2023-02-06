<template>
  <div>
    <!-- 三级联动全局组件:三级联动已经注册为全局组件,因此不需要再引入 -->
    <TypeNav></TypeNav>
    <ListContainer></ListContainer>
    <TodayRecommend></TodayRecommend>
    <RankShow></RankShow>
    <LikeShow></LikeShow>
    <!-- Floor这个组件：自己在组件内部是没有发请求的，数据是父组件给的 -->
    <FloorShow
      v-for="floor in floorList"
      :key="floor.id"
      :list="floor"
    ></FloorShow>
    <BrandShow></BrandShow>
  </div>
</template>

<script>
//引入其余的组件
import ListContainer from "@/pages/Home/ListContainer";
import TodayRecommend from "@/pages/Home/Recommend";
import RankShow from "@/pages/Home/Rank";
import LikeShow from "@/pages/Home/Like";
import FloorShow from "@/pages/Home/Floor";
import BrandShow from "@/pages/Home/Brand";
import { mapState } from "vuex";
export default {
  name: "indexShow",
  components: {
    ListContainer,
    TodayRecommend,
    RankShow,
    LikeShow,
    FloorShow,
    BrandShow,
  },
  mounted() {
    //派发action，获取floor组件的数据
    this.$store.dispatch("getFloorList");
    this.$store.dispatch("getUserInfo");
  },
  computed: {
    ...mapState({
      floorList: (state) => state.home.floorList,
    }),
  },
};
</script>

<style></style>
