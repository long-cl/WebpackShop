<template>
  <div>
    <!-- 轮播图 -->
    <mt-swipe>
      <mt-swipe-item v-for="item in lunbotuList" :key="item.id">
        <img :src="item.img" alt="">
      </mt-swipe-item>
    </mt-swipe>

    <!-- 九宫格  -->
    <div class="mui-content">
      <ul class="mui-table-view mui-grid-view mui-grid-9">
          <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
            <router-link to="/home/newslist">
              <img src="../../images/menu1.png" alt="">
              <div class="mui-media-body">新闻资讯</div>
            </router-link>  
          </li>
          <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
            <router-link to="home/photolist">
              <img src="../../images/menu2.png" alt="">
              <div class="mui-media-body">图片分享</div>
            </router-link>
          </li>
          <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
            <router-link to="">
              <img src="../../images/menu3.png" alt="">
              <div class="mui-media-body">商品购买</div>
            </router-link>
          </li>
          <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
            <router-link to="">
              <img src="../../images/menu4.png" alt="">
              <div class="mui-media-body">留言反馈</div>
            </router-link>
          </li>
          <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
            <router-link to="">
              <img src="../../images/menu5.png" alt="">
              <div class="mui-media-body">视频专区</div>
            </router-link>
          </li>
          <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
            <router-link to="">
              <img src="../../images/menu6.png" alt="">
              <div class="mui-media-body">联系我们</div>
            </router-link>
          </li>
      </ul> 
    </div>

    <router-view></router-view>
    <h3>Home</h3>
  </div>
</template>

<script>
import { Toast } from 'mint-ui'

export default {
  data(){
    return{
      lunbotuList: []
    }
  },
  created(){
    this.getLunbo()
  },
  methods: {
    getLunbo(){
      this.$http.get("api/getlunbo").then(result => {
        if(result.body.status === 0){
          this.lunbotuList = result.body.message;
        }else{
          Toast('加载轮播图失败！')
        }
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.mint-swipe{
  height: 200px;

  .mint-swipe-item{
    &:nth-child(1){
      background-color: red;
    }
    &:nth-child(2){
      background-color: blue;
    }
    &:nth-child(3){
      background-color: skyblue;
    }
  }
  img{
    width: 100%;
    height: 100%;
  }
  .mui-media-body{
    font-size: 13px;
  }
}

.mui-grid-view.mui-grid-9{
  background-color: #fff;
  border: none;

  img{
    width: 60px;
    height: 60px;
  }
}
.mui-grid-view.mui-grid-9 .mui-table-view-cell{
  border: none;
}

</style>