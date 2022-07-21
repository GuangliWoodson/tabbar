<template>
  <div id="app">
    <MyHeader title="My Tab"></MyHeader>
    <div class="a">
      <component :is="comName"></component>
    </div>
    <MyTabBar :list="tabList"></MyTabBar>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader'
import MyTabBar from './components/MyTabBar'
import MyGoodsList from './views/MyGoodsList'
import MyGoodsSearch from './views/MyGoodsSearch'
import MyUserInfo from './views/MyUserInfo'

export default {
  name: 'App',
  data() {
    return {
      comName: 'MyGoodsList',
      tabList: [
        {
          iconText: "icon-shangpinliebiao",
          text: "商品列表",
          componentName: "MyGoodsList"
        },
        {
          iconText: "icon-sousuo",
          text: "商品搜索",
          componentName: "MyGoodsSearch"
        },
        {
          iconText: "icon-user",
          text: "我的信息",
          componentName: "MyUserInfo"
        }
      ]
    }
  },
  components: {
    MyHeader,
    MyTabBar,
    MyGoodsList,
    MyGoodsSearch,
    MyUserInfo
  }
}
</script>

<style>
  .a: {
    padding-top: 45px;
    padding-bottom: 51px
  }
</style>