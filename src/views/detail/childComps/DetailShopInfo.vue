<template>
  <div class="shop-info">
    <div class="shop-top">
      <img :src="shop.logo">
      <span class="title">{{shop.name}}</span>
    </div>
    <div class="shop-middle">
      <div class="shop-middle-item shop-middle-left">
        <div class="info-sells">
          <div class="sells-count">
            {{shop.sells| sellCountFilter}}
          </div>
          <div class="sells-text">总销量</div>
        </div>
        <div class="info-goods">
          <div class="goods-count"> 
            {{shop.goodsCount}}
          </div>
          <div class="goods-text">全部宝贝</div>
        </div>
      </div>
      <div class="shop-middle-item shop-middle-right">
        <table>
          <tr v-for="(item,index) in shop.score" :key="index">
            <td>{{item.name}}</td>
            <td class="score" :class="{'score-better':item.isBetter}">{{item.score}}</td>
            <td class="better" :class="{'better-more':item.isBetter}"><span>{{item.isBetter ? '高':'低'}}</span></td>
          </tr>
        </table>
      </div>
    </div>
    <div class="shop-bottom">
      <div class="enter-shop">进店逛逛</div>
    </div>


    
  </div>
</template>

<script>
export default {
  props:{
    shop:{
      type: Object,
      default(){
        return {}
      }
    }
  },
  filters: {
    sellCountFilter: function(value){
      if(value < 10000 ) return value;
      return (value/10000).toFixed(1) + '万'
    }
  }

}
</script>

<style scoped>
.shop-info{
  
  background-color: #fff;
}
.shop-top{
  height: 100px;
  line-height: 100px;
  background-color: #ffffff;
}
.shop-top img{
  height: 50px;
  width: 50px;
  border-radius: 50%;
  border: 1px solid rgba(100, 100, 100, 0.2);
  position: relative;
  left: 10px;
  top: 24px;
  
}
.shop-top span{
  font-size: 16px;
  color: #A4A1A4;
  position: relative;
  left: 20px;
  top: 6px;
}

.shop-middle{
  margin-top:15px;
  display: flex;
  align-content: center;
}
.shop-middle-item{
  flex: 1;
  text-align: center;
}
.shop-middle-left{
  display: flex;
  justify-content: space-evenly;
  color: #333;
  text-align: center;
  border-right: 1px solid rgba(0, 0, 0, 0.1);
}
.sells-count, .goods-count{
  font-size: 18px;
  margin-top: 15px ;
  
}
.goods-text,.sells-text{
  margin-top: 10px;
  font-size: 12px;
}
.shop-middle-right {
  font-size: 13px;
  color: #333;
}
.shop-middle-right table {
  width: 120px;
  margin-left: 30px;
}
.shop-middle-right table td {
  padding: 5px 0;
}
.shop-middle-right .score {
    color: #5ea732;
}
.shop-middle-right .score-better {
  color: #f13e3a;
}
  .shop-middle-right .better span {
    background-color: #5ea732;
    color: #fff;
    text-align: center;
    padding: 2px;
    border-radius: 4px;
    font-size: 12px;
  }
  .shop-middle-right .better-more span {
    background-color: #f13e3a;
  }
  .shop-bottom {
    text-align: center;
    margin-top: 10px;
  }
.enter-shop {
    display: inline-block;
    font-size: 14px;
    background-color: #f2f5f8;
    width: 150px;
    height: 30px;
    text-align: center;
    line-height: 30px;
    border-radius: 10px;
  }
</style>