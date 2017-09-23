<template>
  <div class="pos">
    <div>
      <el-row id="this_box">
        <!--订单栏-->
        <el-col :span='7' class="left_box">
          <el-tabs value="first" @tab-click="leftTabClick">
            <el-tab-pane label="点餐" name="first">
              <!--表格1-->
              <el-table :data="tableData0" border style="width: 100%">
                <el-table-column prop="goodsName" label="商品"></el-table-column>
                <el-table-column prop="count" label="量" width="50"></el-table-column>
                <el-table-column prop="price" label="金额" width="70"></el-table-column>
                <el-table-column label="操作" width="100" fixed="right">
                  <template scope="scope">
                    <el-button type="text" size="small" @click="delSingleGoods(scope.row)">删除</el-button>
                    <el-button type="text" size="small" @click="addOrderList(scope.row)">增加</el-button>
                  </template>
                </el-table-column>
              </el-table>
            </el-tab-pane>
            <el-tab-pane label="挂单" name="second">
              <!--表格2-->
              <el-table :data="tableData1" border style="width: 100%">
                <el-table-column prop="goodsName" label="商品"></el-table-column>
                <el-table-column prop="count" label="量" width="50"></el-table-column>
                <el-table-column prop="price" label="金额" width="70"></el-table-column>
                <el-table-column label="操作" width="100" fixed="right">
                  <template scope="scope">
                    <el-button type="text" size="small" @click="delSingleGoods(scope.row)">删除</el-button>
                    <el-button type="text" size="small" @click="addOrderList(scope.row)">增加</el-button>
                  </template>
                </el-table-column>
              </el-table>
            </el-tab-pane>
            <el-tab-pane label="外卖" name="third">
              <!--表格3-->
              <el-table :data="tableData2" border style="width: 100%">
                <el-table-column prop="goodsName" label="商品"></el-table-column>
                <el-table-column prop="count" label="量" width="50"></el-table-column>
                <el-table-column prop="price" label="金额" width="70"></el-table-column>
                <el-table-column label="操作" width="100" fixed="right">
                  <template scope="scope">
                    <el-button type="text" size="small" @click="delSingleGoods(scope.row)">删除</el-button>
                    <el-button type="text" size="small" @click="addOrderList(scope.row)">增加</el-button>
                  </template>
                </el-table-column>
              </el-table>
            </el-tab-pane>
          </el-tabs>
          <div class="this_total">
            <span>数量：{{ totalCount }}</span>
            <span>金额：{{ totalMoney }}元</span>
          </div>
          <!--按钮-->
          <div class="this_btn">
            <el-button type="warning">挂单</el-button>
            <el-button type="danger" @click="delAllGoods()">删除</el-button>
            <el-button type="success" @click="checkOut()">结账</el-button>
          </div>
        </el-col>
        <!--商品展示-->
        <el-col :span="17" class="right_box">
          <div class="common_goods">
            <div class="common_title">常用商品</div>
            <div class="common_goods_list">
              <ul>
                <li v-for="(goods,index) in oftenGoods" @click="addOrderList(goods)">
                  <span :goodsid="goods.goodsId">{{goods.goodsName}}</span>
                  <span class="common_price">￥{{goods.price}}元</span>
                </li>
              </ul>
            </div>
          </div>
          <div class="goods_type">
            <el-tabs value="first" @tab-click="rightTabClick">
              <el-tab-pane label="汉堡" name="first">
                <!--表格1-->
                <ul class='cookList'>
                  <li v-for="(goods, index) in type0Goods" @click="addOrderList(goods)">
                    <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                    <span class="foodName" :goodsid="goods.goodsId">{{ goods.goodsName }}</span>
                    <span class="foodPrice">￥{{ goods.price }}元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="小食" name="second">
                <!--表格2-->
                <ul class='cookList'>
                  <li v-for="(goods, index) in type1Goods" @click="addOrderList(goods)">
                    <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                    <span class="foodName" :goodsid="goods.goodsId">{{ goods.goodsName }}</span>
                    <span class="foodPrice">￥{{ goods.price }}元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="饮料" name="third">
                <!--表格3-->
                <ul class='cookList'>
                  <li v-for="(goods, index) in type2Goods" @click="addOrderList(goods)">
                    <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                    <span class="foodName" :goodsid="goods.goodsId">{{ goods.goodsName }}</span>
                    <span class="foodPrice">￥{{ goods.price }}元</span>
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="套餐" name="four">
                <!--表格4-->
                <ul class='cookList'>
                  <li v-for="(goods, index) in type3Goods" @click="addOrderList (goods)">
                    <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                    <span class="foodName" :goodsid="goods.goodsId">{{ goods.goodsName }}</span>
                    <span class="foodPrice">￥{{ goods.price }}元</span>
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
        // 表格数据
        tableData0: [],
        tableData1: [],
        tableData2: [],
        // 常用商品
        oftenGoods: [],
        // 分类商品
        type0Goods: [],
        type1Goods: [],
        type2Goods: [],
        type3Goods: [],
        // 总个数和总价
        totalCount: 0,
        totalMoney: 0
      }
    },
    created: function () {
      // 常用商品数据
      this.$http.get('http://jspang.com/DemoApi/oftenGoods.php').then(res => {
        let data = JSON.parse(res.data)
        this.oftenGoods = data
      }, error => {
        console.log(error)
        console.log('网络错误，不能访问')
      })
      // 分类商品数据
      this.$http.get('http://jspang.com/DemoApi/typeGoods.php').then(res => {
        let data = res.data
        this.type0Goods = data[0]
        this.type1Goods = data[1]
        this.type2Goods = data[2]
        this.type3Goods = data[3]
      }, error => {
        console.log(error)
        console.log('网络错误，不能访问')
      })
    },
    mounted: function () {
      // 修改css样式
      var orderHeight = document.body.clientHeight
      document.getElementById('this_box').style.height = orderHeight + 'px'
      document.getElementsByClassName('left_box')[0].style.height = orderHeight + 'px'
      document.getElementsByClassName('right_box')[0].style.height = orderHeight + 'px'
    },
    methods: {
      // 加入购物车
      addOrderList (goods) {
        // 判断该商品是否已存在
        let isHave = false
        for (let i = 0; i < this.tableData0.length; i++) {
          if (this.tableData0[i].goodsId === goods.goodsId) {
            isHave = true
          }
        }
        // 如果商品存在数量加1，反之添加到商品列表
        if (isHave === true) {
          let arr = this.tableData0.filter(o => o.goodsId === goods.goodsId)
          arr[0].count++
        } else {
          var newGoods = {goodsId: goods.goodsId, goodsName: goods.goodsName, price: goods.price, count: 1}
          this.tableData0.push(newGoods)
        }
        // 重置总个数和总价
        this.getAllMoney()
      },
      // 删除单个商品
      delSingleGoods (goods) {
        this.tableData0 = this.tableData0.filter(o => o.goodsId !== goods.goodsId)
        // 重置总个数和总价
        this.getAllMoney()
      },
      // 删除全部商品
      delAllGoods () {
        this.tableData0 = []
        this.totalCount = 0
        this.totalMoney = 0
      },
      // 汇总数量和金额
      getAllMoney () {
        // 总数量和总价清零
        this.totalCount = 0
        this.totalMoney = 0
        // 计算总数量和总价
        this.tableData0.forEach(element => {
          this.totalCount += element.count
          this.totalMoney += this.totalMoney + (element.price * element.count)
        })
      },
      // 结账
      checkOut () {
        if (this.totalCount !== 0) {
          this.delAllGoods()
          this.$message({
            type: 'success',
            message: '结账成功，感谢你又为店里出了一份力!'
          })
        } else {
          this.$message.error('不能空结。老板了解你急切的心情！')
        }
      },
      leftTabClick (tab, event) {
        console.log(tab.label)
      },
      rightTabClick (tab, event) {
        console.log(tab.label)
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
  .this_total{
    padding: 10px 0;
    text-align: center;
    border-bottom: 1px solid #D3DCE6; 
  }
  .this_total span{
    padding: 0 10px;
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