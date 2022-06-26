<template>
  <div>
    <MyHeader title="购物车案例" />
    <MyGoods v-for="item in goodsList" :key="item.goods_id" :goods="item"/>
    <MyFooter :list="goodsList"/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyGoods from './components/MyGoods.vue'
import MyFooter from './components/MyFooter.vue'
import axios from 'axios'
export default {
  data () {
    return {
      goodsList: []
    }
  },
  components: {
    MyHeader,
    MyGoods,
    MyFooter
  },
  created () {
    this.getArr()
  },
  methods: {
    async getArr () {
      const res = await axios({ url: '/api/cart' })
      this.goodsList = res.data.list
    }
  }
}
</script>

<style scoped></style>
