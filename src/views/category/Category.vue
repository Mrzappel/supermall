<template>
  <div class="wrapper" ref="aaa">
    <scroll class="content">
      <ul>
        <li>商品数量1</li>
        <li>商品数量2</li>
        <li>商品数量3</li>
        <li>商品数量4</li>
        <li>商品数量5</li>
        <li>商品数量6</li>
        <li>商品数量7</li>
        <li>商品数量8</li>
        <li>商品数量9</li>
        <li>商品数量10</li>
        <li>商品数量11</li>
        <li>商品数量12</li>
        <li>商品数量13</li>
        <li>商品数量14</li>
        <li>商品数量15</li>
        <li>商品数量16</li>
        <li>商品数量17</li>
        <li>商品数量18</li>
        <li>商品数量19</li>
        <li>商品数量20</li>
        <li>商品数量21</li>
        <li>商品数量22</li>
        <li>商品数量23</li>
        <li>商品数量24</li>
        <li>商品数量25</li>
        <li>商品数量26</li>
        <li>商品数量27</li>
        <li>商品数量28</li>
        <li>商品数量29</li>
        <li>商品数量30</li>
        <li>商品数量31</li>
        <li>商品数量32</li>
        <li>商品数量33</li>
        <li>商品数量34</li>
        <li>商品数量35</li>
        <li>商品数量36</li>
        <li>商品数量37</li>
        <li>商品数量38</li>
        <li>商品数量39</li>
        <li>商品数量40</li>
        <li>商品数量41</li>
        <li>商品数量42</li>
        <li>商品数量43</li>
        <li>商品数量44</li>
        <li>商品数量45</li>
        <li>商品数量46</li>
        <li>商品数量47</li>
        <li>商品数量48</li>
        <li>商品数量49</li>
        <li>商品数量50</li>
        <li>商品数量51</li>
        <li>商品数量52</li>
        <li>商品数量53</li>
        <li>商品数量54</li>
        <li>商品数量55</li>
        <li>商品数量56</li>
        <li>商品数量57</li>
        <li>商品数量58</li>
        <li>商品数量59</li>
        <li>商品数量60</li>
        <li>商品数量61</li>
        <li>商品数量62</li>
        <li>商品数量63</li>
        <li>商品数量64</li>
        <li>商品数量65</li>
        <li>商品数量66</li>
        <li>商品数量67</li>
        <li>商品数量68</li>
        <li>商品数量69</li>
        <li>商品数量70</li>
        <li>商品数量71</li>
        <li>商品数量72</li>
        <li>商品数量73</li>
        <li>商品数量74</li>
        <li>商品数量75</li>
        <li>商品数量76</li>
        <li>商品数量77</li>
        <li>商品数量78</li>
        <li>商品数量79</li>
        <li>商品数量80</li>
        <li>商品数量81</li>
        <li>商品数量82</li>
        <li>商品数量83</li>
        <li>商品数量84</li>
        <li>商品数量85</li>
        <li>商品数量86</li>
        <li>商品数量87</li>
        <li>商品数量88</li>
        <li>商品数量89</li>
        <li>商品数量90</li>
        <li>商品数量91</li>
        <li>商品数量92</li>
        <li>商品数量93</li>
        <li>商品数量94</li>
        <li>商品数量95</li>
        <li>商品数量96</li>
        <li>商品数量97</li>
        <li>商品数量98</li>
        <li>商品数量99</li>
        <li>商品数量100</li>
      </ul>
    </scroll>
  </div>
</template>

<script>
// import BScroll from 'better-scroll'
import Scroll from "components/common/scroll/Scroll.vue";

export default {
  name: "Category",
  components: { Scroll }

  // data() {
  //   return {
  //     scroll: null
  //   }
  // },
  // mounted() {
  //   this.scroll = new BScroll(this.$refs.aaa,{
  //     probeType: 3,
  //     pullUpLoad: true
  //   })

  //   this.scroll.on('scroll', (position) => {
  //     console.log(position);
  //   })

  //   this.scroll.on('pullingUp', () => {
  //     console.log('上拉加载更多');
  //   })
  // }
};
</script>

<style scoped>
.content {
  height: 300px;
  background-color: red;
  color: white;
  overflow-y: scroll;
}
/* .content {
    height: 700px;
  } */
</style>
