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
      // 上拉加载的设置
      infiniteLoadData: {
        initialShowNum: 10, // 初始显示多少条
        everyLoadingNum: 10, // 每次加载的个数
        pullUpState: 1, // 子组件的pullUpState状态
        pullUpList: [], // 上拉加载更多数据的数组
        showPullUpListLength: this.initialShowNum // 上拉加载后所展示的个数
      },
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
      if (this.infiniteLoadData.pullUpState === 1) {
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


