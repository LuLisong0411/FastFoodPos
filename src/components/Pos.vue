<template>
  <div class="pos"> 
    <el-row>
      <el-col :span='7' class="pos-order" id="order-list">
        <el-tabs>
          <el-tab-pane label="点餐">
            <el-table v-bind:data="goodsData" border style="width:100%">
              <el-table-column prpo="goodsName" label="商品名称"> </el-table-column>
              <el-table-column prpo="count" label="数量"> </el-table-column>
              <el-table-column prpo="price" label="单价"> </el-table-column>
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
      <el-col>
        我是餐品栏
      </el-col>
    </el-row> 
  </div>
</template>

<script>
export default {
  name: 'pos',
  data(){
    return {
      goodsData: [{
          
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
        }]
    }
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
</style>
