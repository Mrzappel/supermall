<template>
  <div id="home" class="warpper">
    
    <nav-bar class="home-navbar"><div slot="center">购物街</div></nav-bar>
    <tab-control  
                    @tabClick="tabClick"
                    :titles="['流行','新款','精选']"
                    v-show="isTabFixed"
                    ref="tabControl1"
                    class="tab-control"/>
    <scroll class="content" 
            ref="scroll" 
            :probe-type="3" 
            @scroll="contentScroll"
            :pull-up-load='true'
            @pullingUp = "loadMore">
      <home-swiper :banners="banners"
                    @swiperImageLoad="swiperImageLoad"/>
      <recommend-view :recommends="recommends"/>
      <tab-control  
                    @tabClick="tabClick"
                    :titles="['流行','新款','精选']"
                    ref="tabControl2"/>
      <feature-view/>
      <goods-list :goods="showGoods"/>
      <!-- 解决滚动问题的占位 -->
      <!-- <div class="have"></div> -->
    </scroll>
    <back-top @click.native="backClick" v-show="isShowBackTop"></back-top>
  </div>
</template>

<script>

  import HomeSwiper from "./childComps/HomeSwiper.vue"
  import RecommendView from "./childComps/RecommendView.vue"
  import FeatureView from "./childComps/FeatureView.vue"
  import TabControl from "components/content/tabControl/TabControl"
  import GoodsList from "components/content/goods/GoodsList"
  import Scroll from "components/common/scroll/Scroll.vue"
  import NavBar from "components/common/navbar/NavBar.vue"
  import BackTop from "components/common/backtop/BackTop.vue"

  import {getHomeMultidata, getHomeGoods} from "network/home"
  import {debounce} from "common/utils.js"
  
  export default {
    name:"Home",
    components:{
      HomeSwiper,
      FeatureView,
      NavBar,
      RecommendView,
      TabControl,
      GoodsList,
      Scroll,
      BackTop
    },
    data() {
      return {
        banners: [],
        recommends: [],
        goods: {
          'pop': {page: 0, list: []},
          'new': {page: 0 ,list: []},
          'sell': {page: 0 ,list: []}
        },
        currentType: 'pop',
        isShowBackTop: false,
        tabOffsetTop: 0,
        isTabFixed: false
        
      }
    },
    created() {
      this.getHomeMultidata()
      this.getHomeGoods('pop')
      this.getHomeGoods('new')
      this.getHomeGoods('sell')
    },
    mounted() {
      const refresh = debounce(this.$refs.scroll.refresh, 200)
      this.$bus.$on('itemImageLoad', () => {
        refresh()
      })
      
      
    },

    computed: {
      showGoods() {
        return this.goods[this.currentType].list
      }
    },
    methods: {
      
      // 事件监听相关的事件
      tabClick(index) {
        switch (index) {
          case 0:
            this.currentType = "pop"
            break
          case 1:
            this.currentType = "new"
            break
          case 2:
            this.currentType = "sell"
            break
        }
        this.$refs.tabControl1.currentIndex = index
        this.$refs.tabControl2.currentIndex = index
      },
      contentScroll(position) {
        this.isShowBackTop = (-position.y) > 100
        this.isTabFixed = (-position.y) > this.tabOffsetTop
      },
      backClick() {
        this.$refs.scroll.scrollTo(0,0,500)
      },
      loadMore() {
        this.getHomeGoods(this.currentType) 
      },
      swiperImageLoad() {
        // console.log(this.$refs.tabControl.$el.offsetTop)
        this.tabOffsetTop = this.$refs.tabControl2.$el.offsetTop
        
        
      },
      // 网络请求相关的事件
      getHomeMultidata() {
        getHomeMultidata().then(res => {
          // this.result = res;
          this.banners = res.data.banner.list;
          this.recommends = res.data.recommend.list;
        })
      },
      getHomeGoods(type) {
        const page = this.goods[type].page +1
        getHomeGoods(type, page).then(res => {
          this.goods[type].list.push(...res.data.list)
          this.goods[type].page += 1
          this.$refs.scroll.finishPullUp()
        })
      }

    }
  }
</script> 

<style scoped>
  /* 为了解决滚动问题的占位 */
  /* .have {
    height: 1000px
  } */
  #home {
    height: 100vh;
    position: relative;
    /* padding-top: 44px; */
  }
  .home-navbar {
    background-color: var(--color-tint);
    color: #ffffff;
    /* position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9 */
  }
  .tab-control {
    position: relative;
    z-index: 9;
  }
  .content {
    overflow: hidden;
    position: absolute;
    top: 44px;
    bottom: 49px;
    left: 0;
    right: 0;
  }
</style>
