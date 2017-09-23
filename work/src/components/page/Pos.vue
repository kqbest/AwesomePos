<template>
  <div class="pos">
    <div>
      <el-row id="this_box">
        <!--订单栏-->
        <el-col :span='7' class="left_box">
          <el-tabs v-model="activeName" @tab-click="leftTabClick">
            <el-tab-pane label="点餐" name="first">
              <!--表格1-->
              <el-table :data="tableData" border show-summary style="width: 100%">
                <el-table-column prop="goodsName" label="商品"></el-table-column>
                <el-table-column prop="count" label="量" width="50"></el-table-column>
                <el-table-column prop="price" label="金额" width="70"></el-table-column>
                <el-table-column label="操作" width="100" fixed="right">
                  <template scope="scope">
                    <el-button type="text" size="small">删除</el-button>
                    <el-button type="text" size="small">增加</el-button>
                  </template>
                </el-table-column>
              </el-table>
            </el-tab-pane>
            <el-tab-pane label="挂单" name="second">
              <!--表格2-->
              <el-table :data="tableData" border show-summary style="width: 100%">
                <el-table-column prop="goodsName" label="商品"></el-table-column>
                <el-table-column prop="count" label="量" width="50"></el-table-column>
                <el-table-column prop="price" label="金额" width="70"></el-table-column>
                <el-table-column label="操作" width="100" fixed="right">
                  <template scope="scope">
                    <el-button type="text" size="small">删除</el-button>
                    <el-button type="text" size="small">增加</el-button>
                  </template>
                </el-table-column>
              </el-table>
            </el-tab-pane>
            <el-tab-pane label="外卖" name="third">
              <!--表格3-->
              <el-table :data="tableData" border show-summary style="width: 100%">
                <el-table-column prop="goodsName" label="商品"></el-table-column>
                <el-table-column prop="count" label="量" width="50"></el-table-column>
                <el-table-column prop="price" label="金额" width="70"></el-table-column>
                <el-table-column label="操作" width="100" fixed="right">
                  <template scope="scope">
                    <el-button type="text" size="small">删除</el-button>
                    <el-button type="text" size="small">增加</el-button>
                  </template>
                </el-table-column>
              </el-table>
            </el-tab-pane>
          </el-tabs>
          <!--按钮-->
          <div class="this_btn">
            <el-button type="warning">挂单</el-button>
            <el-button type="danger">删除</el-button>
            <el-button type="success">结账</el-button>
          </div>
        </el-col>
        <!--商品展示-->
        <el-col :span="17" class="right_box">
          <div class="common_goods">
            <div class="common_title">常用商品</div>
            <div class="common_goods_list">
              <ul>
                <li v-for="(item,index) in oftenGoods">
                  <span :goodsid="item.goodsId">{{item.goodsName}}</span>
                  <span class="common_price">￥{{item.price}}元</span>
                </li>
              </ul>
            </div>
          </div>
          <div class="goods_type">
            <el-tabs v-model="activeName1" @tab-click="rightTabClick">
              <el-tab-pane label="汉堡" name="first">
                <!--表格1-->
                <ul class='cookList'>
                  <li v-for="(item, index) in typeGoods">
                    <span class="foodImg"><img :src="item.goodsImg" width="100%"></span>
                    <span class="foodName" :goodsid="item.goodsId">{{ item.goodsName }}</span>
                    <span class="foodPrice">￥{{ item.price }}元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="小食" name="second">
                <!--表格2-->
                <ul class='cookList'>
                  <li v-for="(item, index) in typeGoods">
                    <span class="foodImg"><img :src="item.goodsImg" width="100%"></span>
                    <span class="foodName" :goodsid="item.goodsId">{{ item.goodsName }}</span>
                    <span class="foodPrice">￥{{ item.price }}元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="饮料" name="third">
                <!--表格3-->
                <ul class='cookList'>
                  <li v-for="(item, index) in typeGoods">
                    <span class="foodImg"><img :src="item.goodsImg" width="100%"></span>
                    <span class="foodName" :goodsid="item.goodsId">{{ item.goodsName }}</span>
                    <span class="foodPrice">￥{{ item.price }}元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="套餐" name="four">
                <!--表格3-->
                <ul class='cookList'>
                  <li v-for="(item, index) in typeGoods">
                    <span class="foodImg"><img :src="item.goodsImg" width="100%"></span>
                    <span class="foodName" :goodsid="item.goodsId">{{ item.goodsName }}</span>
                    <span class="foodPrice">￥{{ item.price }}元</span>
                  </li>
                </ul>
              </el-tab-pane>
            </el-tabs>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'pos',
    data () {
      return {
        activeName: 'first',
        activeName1: 'first',
        // 表格数据
        tableData: [{
          goodsName: '可口可乐',
          price: 8,
          count: 1
        }, {
          goodsName: '香辣鸡腿堡',
          price: 15,
          count: 1
        }, {
          goodsName: '爱心薯条',
          price: 8,
          count: 1
        }, {
          goodsName: '甜筒',
          price: 8,
          count: 1
        }],
        // goodsList
        oftenGoods: [{
          goodsId: 1,
          goodsName: '香辣鸡腿堡',
          price: 18
        }, {
          goodsId: 2,
          goodsName: '田园鸡腿堡',
          price: 15
        }, {
          goodsId: 3,
          goodsName: '和风汉堡',
          price: 15
        }, {
          goodsId: 4,
          goodsName: '快乐全家桶',
          price: 80
        }, {
          goodsId: 5,
          goodsName: '脆皮炸鸡腿',
          price: 10
        }, {
          goodsId: 6,
          goodsName: '魔法鸡块',
          price: 20
        }, {
          goodsId: 7,
          goodsName: '可乐大杯',
          price: 10
        }, {
          goodsId: 8,
          goodsName: '雪顶咖啡',
          price: 18
        }, {
          goodsId: 9,
          goodsName: '大块鸡米花',
          price: 15
        }, {
          goodsId: 20,
          goodsName: '香脆鸡柳',
          price: 17
        }],
        // typeGoodsList
        typeGoods: [{
          goodsId: 1,
          goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg',
          goodsName: '香辣鸡腿堡',
          price: 18
        }, {
          goodsId: 2,
          goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg',
          goodsName: '田园鸡腿堡',
          price: 15
        }, {
          goodsId: 3,
          goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg',
          goodsName: '和风汉堡',
          price: 15
        }, {
          goodsId: 4,
          goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg',
          goodsName: '快乐全家桶',
          price: 80
        }, {
          goodsId: 5,
          goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg',
          goodsName: '脆皮炸鸡腿',
          price: 10
        }, {
          goodsId: 6,
          goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg',
          goodsName: '魔法鸡块',
          price: 20
        }, {
          goodsId: 7,
          goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg',
          goodsName: '可乐大杯',
          price: 10
        }, {
          goodsId: 8,
          goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg',
          goodsName: '雪顶咖啡',
          price: 18
        }, {
          goodsId: 9,
          goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg',
          goodsName: '大块鸡米花',
          price: 15
        }, {
          goodsId: 20,
          goodsImg: 'http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg',
          goodsName: '香脆鸡柳',
          price: 17
        }]
      }
    },
    mounted: function () {
      var orderHeight = document.body.clientHeight
      document.getElementById('this_box').style.height = orderHeight + 'px'
      document.getElementsByClassName('left_box')[0].style.height = orderHeight + 'px'
      document.getElementsByClassName('right_box')[0].style.height = orderHeight + 'px'
      this.$http.get('http://jspang.com/DemoApi/typeGoods.php').then(data => {
        console.log(data)
      }, () => {
        console.log('错误信息')
      })
    },
    methods: {
      leftTabClick (tab, event) {
        console.log(tab.label)
      },
      rightTabClick (tab, event) {
        console.log(tab.label)
      },

      datas () {
        this.$http.get('http://jspang.com/DemoApi/typeGoods.php').then(data => {
          console.log(data)
        }, () => {
          console.log('错误信息')
        })
      }
    }
  }
</script>

<style scoped>
  .left_box{
    background-color: #fff;
  }
  .this_btn{
    padding: 10px 0;
    text-align: center;
  }

  .common_goods{
    width: 100%;
  }
  .common_title{
    height: 20px;
    padding: 10px;
    border-bottom: 1px solid #D3DCE6;
    background-color: #F9FAFC;
  }
  .common_goods_list ul{
    overflow: hidden;
  }
  .common_goods_list ul li{
    float: left;
    padding: 10px;
    margin: 5px;
    list-style: none;
    border: 1px solid #E5E9F2;
    background-color: #fff;
    cursor: pointer;
  }
  .common_price{
    color: #58B7FF; 
  }

  .cookList li{
    float: left;
    width: 23%;
    height: auto;
    padding: 2px;
    margin: 2px;
    list-style: none;
    border: 1px solid #E5E9F2;
    background-color: #fff;
    overflow: hidden;
    cursor: pointer;
  }
  .cookList li span{
    float: left;
    display: block;
  }
  .foodImg{
    width: 40%;
  }
  .foodName{
    width: 50%;
    font-size: 18px;
    padding-left: 10px;
    color: brown;
  }
  .foodPrice{
    width: 50%;
    padding-left: 10px;
    padding-top: 10px;
    font-size: 16px;
  }
</style>