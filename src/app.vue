<template>
  <div class="app_zong">
    <!--顶部-->
    
    <mt-header fixed title="固定在顶部">
      <span slot="left" @click="goback" v-show="flag">
        <mt-button icon="back">返回</mt-button>
      </span>
    </mt-header>
    <!--中部-->
    <div class="view">
      <!--页面切换动画name控制从左到右-->
      <transition>
        <router-view></router-view>
      </transition>
    </div>
    <!--底部-->
    <nav class="mui-bar mui-bar-tab">
      <router-link class="mui-tab-item1" to="/home">
        <span class="mui-icon mui-icon-home"></span>
        <span class="mui-tab-label">首页</span>
      </router-link>
      <router-link class="mui-tab-item1" to="/member">
        <span class="mui-icon mui-icon-contact"></span>
        <span class="mui-tab-label">会员</span>
      </router-link>
      <router-link class="mui-tab-item1" to="/shopping">
        <span class="mui-icon mui-icon-extra mui-icon-extra-cart"><span class="mui-badge" id="badgeid">{{$store.getters.option}}</span></span>
        <span class="mui-tab-label">购物车</span>
      </router-link>
      <router-link class="mui-tab-item1" to="/search">
        <span class="mui-icon mui-icon-search"></span>
        <span class="mui-tab-label">搜索</span>
      </router-link>
    </nav>
  </div>
</template>
<script>
export default {
  data () {
    return {
      flag: false
    }
  },
  methods: {
    goback () {
      this.$router.go(-1)
    }
  },
  watch: {
    '$route.path': function (newVal) {
      if (newVal === '/home') {
        this.flag = false
      } else {
        this.flag = true
      }
    }
  },
  created () {
    this.flag = this.$route.path === '/home' ? false: true
    // if ($router.path === '/home') {
    //   this.flag = false
    // } else {
    //   this.flag = true
    // }
  }
}
</script>
<style lang="less" scoped>
.mui-bar-tab .mui-tab-item1.mui-active {
    color: #007aff;
}
.mui-bar-tab .mui-tab-item1 .mui-icon {
    top: 3px;
    width: 24px;
    height: 24px;
    padding-top: 0;
    padding-bottom: 0;
}
.mui-icon-home:before {
    content: '\E500';
}
.mui-bar-tab .mui-tab-item1 {
    display: table-cell;
    overflow: hidden;
    width: 1%;
    height: 55px;
    text-align: center;
    vertical-align: middle;
    white-space: nowrap;
    text-overflow: ellipsis;
    color: #929292;
}
.mui-bar-tab .mui-tab-item1 .mui-icon~.mui-tab-label {
    font-size: 11px;
    display: block;
    overflow: hidden;
    text-overflow: ellipsis;
}
.mui-bar-tab .mui-tab-item1.mui-active {
    color: #007aff;
}

</style>
