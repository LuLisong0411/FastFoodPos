<template>
  <div class="pos"> 
    <el-row>
      <el-col :span='7' class="pos-order" id="order-list">
        <el-tabs>
          <el-tab-pane label="点餐">
            <el-table :data="tableData" border style="width:100%">
              <el-table-column prop="goodsName" label="商品名称"> </el-table-column>
              <el-table-column prop="count" label="数量"> </el-table-column>
              <el-table-column prop="price" label="单价"> </el-table-column>
              <el-table-column label="操作" fixed="right">
                <template scope="">
                  <el-button type="text" size="samll">删除</el-button>
                  <el-button type="text" size="samll">增加</el-button>
                </template>
              </el-table-column>
            </el-table>
          </el-tab-pane>
          <el-tab-pane label="外卖">

          </el-tab-pane>
          <el-tab-pane label="挂单">

          </el-tab-pane>
        </el-tabs>
        <div class="div-btn">
          <el-button type="warning">挂单</el-button>
          <el-button type="danger">删除</el-button>
          <el-button type="success">结账</el-button>
        </div>
        
      </el-col>
      <el-col :span='17'>
        <div often-goods>
          <div class="title">常用商品</div>
          <div class="often-goods-list"> 
            <ul>
              <li v-for="foods in oftenFoods">
                <span>{{foods.goodsName}}</span>
                <span class="o-price">￥{{foods.price}}</span>
              </li>
            </ul>
          </div>
        </div>
        <div class="goods-type">
          <el-tabs>
            <el-tab-pane label="汉堡">
              <div>
                <ul class='cookList'>
                  <li v-for="goods in type0Goods">
                    <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                    <span class="foodName">{{goods.goodsName}}</span>
                    <span class="foodPrice">￥{{goods.price}}元</span>
                  </li>
                </ul>
              </div>
            </el-tab-pane>
            <el-tab-pane label="小食">
              <div>
                <ul class='cookList'>
                  <li v-for="goods in type1Goods">
                    <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                    <span class="foodName">{{goods.goodsName}}</span>
                    <span class="foodPrice">￥{{goods.price}}元</span>
                  </li>
                </ul>
              </div>
            </el-tab-pane>
            <el-tab-pane label="饮料">
              <div>
                <ul class='cookList'>
                  <li v-for="goods in type2Goods">
                    <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                    <span class="foodName">{{goods.goodsName}}</span>
                    <span class="foodPrice">￥{{goods.price}}元</span>
                  </li>
                </ul>
              </div>
            </el-tab-pane>
            <el-tab-pane label="套餐">
              <div>
                <ul class='cookList'>
                  <li v-for="goods in type3Goods">
                    <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                    <span class="foodName">{{goods.goodsName}}</span>
                    <span class="foodPrice">￥{{goods.price}}元</span>
                  </li>
                </ul>
              </div>
            </el-tab-pane>
          </el-tabs>
        </div>
        
      </el-col>
    </el-row> 
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'pos', 
  data(){
    return {
      tableData:[{
          
          goodsName: '可口可乐',
          count:1,
          price: 8,
        }, {
          
          goodsName: '香辣鸡腿堡',
          count:1,
          price: 15,
        }, {
         
          goodsName: '爱心薯条',
          count:1,
          price: 8,
        }, {
         
          goodsName: '甜筒',
          count:1,
          price: 8,
        }],
        oftenFoods:[
          // {
          //     goodsId:1,
          //     goodsName:'香辣鸡腿堡',
          //     price:18
          // }, {
          //     goodsId:2,
          //     goodsName:'田园鸡腿堡',
          //     price:15
          // }, {
          //     goodsId:3,
          //     goodsName:'和风汉堡',
          //     price:15
          // }, {
          //     goodsId:4,
          //     goodsName:'快乐全家桶',
          //     price:80
          // }, {
          //     goodsId:5,
          //     goodsName:'脆皮炸鸡腿',
          //     price:10
          // }, {
          //     goodsId:6,
          //     goodsName:'魔法鸡块',
          //     price:20
          // }, {
          //     goodsId:7,
          //     goodsName:'可乐大杯',
          //     price:10
          // }, {
          //     goodsId:8,
          //     goodsName:'雪顶咖啡',
          //     price:18
          // }, {
          //     goodsId:9,
          //     goodsName:'大块鸡米花',
          //     price:15
          // }, {
          //     goodsId:20,
          //     goodsName:'香脆鸡柳',
          //     price:17
          // }
        ],
        type0Goods:[],
        type1Goods:[],
        type2Goods:[],
        type3Goods:[],
    }
  },
  created:function(){
    axios.get('https://www.easy-mock.com/mock/5b8b30dbf032f03c5e71de7f/kuaican/oftenGoods')
    .then(reponse=>{
      // console.log(reponse);
      this.oftenFoods = reponse.data;
    })
    .catch(error=>{
      // console.log(error);
      alert('error')
    })
    axios.get('https://www.easy-mock.com/mock/5b8b30dbf032f03c5e71de7f/kuaican/typeGoods')
    .then(reponse=>{
      // console.log(reponse);
      this.type0Goods = reponse.data[0];
      this.type1Goods = reponse.data[1];
      this.type2Goods = reponse.data[2];
      this.type3Goods = reponse.data[3];
    })
    .catch(error=>{
      // console.log(error);
      alert('error')
    })
  },
  mounted(){
    var orderHeight = document.body.clientHeight;
    // console.log(orderHeight);
    document.getElementById('order-list').style.height = orderHeight + 'px';
  }
};
</script>


<style scoped>
  .pos-order{
    background-color: #F9FAFC;
    border-right: 1px solid #C0CCDA;
  }
  .div-btn{
    margin-top:14px;
  }
  .title{
    height: 20px;
    background-color: #F9FAFC;
    border-bottom: 1px solid #f3dFe6;
    padding: 10px;
    text-align: left;
  }
  .often-goods-list ul li{
    list-style: none;
    float: left;
    border:1px solid #fe3dce;
    background-color: #fff;
    margin: 10px;
    padding: 10px;
    display: block;
  }
  .o-price{
    color:#58B7FF;
  }
  .goods-type{
    clear: both;
  }
  .cookList li{
       list-style: none;
       width:23%;
       border:1px solid #E5E9F2;
       height: auot;
       overflow: hidden;
       background-color:#fff;
       padding: 2px;
       float:left;
       margin: 2px;
 
   }
   .cookList li span{
       
        display: block;
        float:left;
   }
   .foodImg{
       width: 40%;
   }
   .foodName{
       font-size: 18px;
       padding-left: 10px;
       color:brown;
 
   }
   .foodPrice{
       font-size: 16px;
       padding-left: 10px;
       padding-top:10px;
   }
  
</style>
