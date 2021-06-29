<template>
  <div id="home" class="warpper">
    
    <nav-bar class="home-navbar"><div slot="center">购物街</div></nav-bar>
    <scroll class="content" ref="scroll">
      <home-swiper :banners="banners"></home-swiper>
      <recommend-view :recommends="recommends"></recommend-view>
      <tab-control  class="tab-control"
                    @tabClick="tabClick"
                    :titles="['流行','新款','精选']"></tab-control>
      <feature-view></feature-view>
      <goods-list :goods="showGoods"></goods-list>
      <!-- 解决滚动问题的占位 -->
      <!-- <div class="have"></div> -->
      <ul>
        <li>数个数1</li>
        <li>数个数2</li>
        <li>数个数3</li>
        <li>数个数4</li>
        <li>数个数5</li>
        <li>数个数6</li>
        <li>数个数7</li>
        <li>数个数8</li>
        <li>数个数9</li>
        <li>数个数10</li>
        <li>数个数11</li>
        <li>数个数12</li>
        <li>数个数13</li>
        <li>数个数14</li>
        <li>数个数15</li>
        <li>数个数16</li>
        <li>数个数17</li>
        <li>数个数18</li>
        <li>数个数19</li>
        <li>数个数20</li>
        <li>数个数21</li>
        <li>数个数22</li>
        <li>数个数23</li>
        <li>数个数24</li>
        <li>数个数25</li>
        <li>数个数26</li>
        <li>数个数27</li>
        <li>数个数28</li>
        <li>数个数29</li>
        <li>数个数30</li>
        <li>数个数31</li>
        <li>数个数32</li>
        <li>数个数33</li>
        <li>数个数34</li>
        <li>数个数35</li>
        <li>数个数36</li>
        <li>数个数37</li>
        <li>数个数38</li>
        <li>数个数39</li>
        <li>数个数40</li>
        <li>数个数41</li>
        <li>数个数42</li>
        <li>数个数43</li>
        <li>数个数44</li>
        <li>数个数45</li>
        <li>数个数46</li>
        <li>数个数47</li>
        <li>数个数48</li>
        <li>数个数49</li>
        <li>数个数50</li>
        <li>数个数51</li>
        <li>数个数52</li>
        <li>数个数53</li>
        <li>数个数54</li>
        <li>数个数55</li>
        <li>数个数56</li>
        <li>数个数57</li>
        <li>数个数58</li>
        <li>数个数59</li>
        <li>数个数60</li>
        <li>数个数61</li>
        <li>数个数62</li>
        <li>数个数63</li>
        <li>数个数64</li>
        <li>数个数65</li>
        <li>数个数66</li>
        <li>数个数67</li>
        <li>数个数68</li>
        <li>数个数69</li>
        <li>数个数70</li>
        <li>数个数71</li>
        <li>数个数72</li>
        <li>数个数73</li>
        <li>数个数74</li>
        <li>数个数75</li>
        <li>数个数76</li>
        <li>数个数77</li>
        <li>数个数78</li>
        <li>数个数79</li>
        <li>数个数80</li>
        <li>数个数81</li>
        <li>数个数82</li>
        <li>数个数83</li>
        <li>数个数84</li>
        <li>数个数85</li>
        <li>数个数86</li>
        <li>数个数87</li>
        <li>数个数88</li>
        <li>数个数89</li>
        <li>数个数90</li>
        <li>数个数91</li>
        <li>数个数92</li>
        <li>数个数93</li>
        <li>数个数94</li>
        <li>数个数95</li>
        <li>数个数96</li>
        <li>数个数97</li>
        <li>数个数98</li>
        <li>数个数99</li>
        <li>数个数100</li>
      </ul>
    </scroll>
    <back-top @click.native="backClick"></back-top>
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
        currentType: ['pop']
      }
    },
    created() {
      this.getHomeMultidata()
      this.getHomeGoods('pop')
      this.getHomeGoods('new')
      this.getHomeGoods('sell')
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
        
      },
      backClick() {
        this.$refs.scroll.scrollTo(0,0,500)
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
    /* height: 100vh; */
    /* position: relative; */
    padding-top: 44px;
  }
  .home-navbar {
    background-color: var(--color-tint);
    color: #ffffff;
    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9
  }
  .tab-control {
    position: sticky;
    top: 44px;
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
