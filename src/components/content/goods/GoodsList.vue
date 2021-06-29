<template>
  <div class="goods">
    <goods-list-item v-for="(item,id) in goods" :key="id" :goods-item="item"></goods-list-item>
  </div>
</template>

<script>
import GoodsListItem from "components/content/goods/GoodsListItem"
export default {
  name:"GoodsList",
  components: {GoodsListItem},
  props: {
    type: Array,
    default() {
      return [] 
    }
  }
}
</script>

<style>

</style>
