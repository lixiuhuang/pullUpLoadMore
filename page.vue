<template>
  <div>
      <p>上拉加载更多数据，使用vue-infinite-scroll 也可实现同类效果</p>
     <pull-up-load-more :on-infinite-load="onInfiniteLoad" :parent-pull-up-state="pullUpState">
       there are many data
     </pull-up-load-more>
  </div>
</template>
<script>
import pullUpLoadMore from './components'
export default {
  data () {
    return {
      dataList:[],
      pullUpState:1,
      dataList:[],
      page:1
    }
  },
  methods: {
    // 上拉一次加载更多的数据
    getPullUpMoreData () {
      this.page = this.page + 1
      this.getData()
    },
    onInfiniteLoad (done) {
      if (this.pullUpState === 1) {
        this.getPullUpMoreData()
      }
      done()
    },
    getData() {
      // 这里获取数据处理。初始化调用一次
    }
  },
  components:{
    pullUpLoadMore,
  },
  mounted () {
    this.getData()
  }
}
</script>
<style lang="scss" scoped>
.cont{
  padding:15px 20px;
  li{
    line-height: 30px;
    margin-bottom: 15px;
  }
}
</style>


