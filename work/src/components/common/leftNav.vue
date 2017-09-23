<template>
  <div class="left-nav">
    <ul>
      <li>
        <i class="icon iconfont icon-trade"></i>
        <div>收银</div>
      </li>
      <li>
        <i class="icon iconfont icon-store"></i>
        <div>店铺</div>
      </li>
      <li>
        <i class="icon iconfont icon-bags"></i>
        <div>商品</div>
      </li>
      <li>
        <i class="icon iconfont icon-bussinesscard"></i>
        <div>会员</div>
      </li>
      <li>
        <i class="icon iconfont icon-Calculator"></i>
        <div>统计</div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'leftNav',
    data () {
      return {
      }
    }
  }
</script>

<style scoped>
  .left-nav{
    float: left;
    width: 5%;
    height: 100%;
    color: #fff;
    font-size: 10px;
    background-color: #1D8ce0;
  }
  .iconfont{
    font-size: 24px;
  }
  .left-nav ul{
    padding: 0px;
    margin: 0px;
  }
  .left-nav li{
    padding: 10px;
    list-style: none;
    text-align: center;
    border-bottom: 1px solid #20a0ff;
    cursor: pointer;
  }
</style>