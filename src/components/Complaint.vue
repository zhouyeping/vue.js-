<template>
  <div>
    <div class="header">
      <div class="header__title"><span>投诉内容</span></div>
      <div class="header__container">
        <div class="container__pic">
          <img src="../assets/logo.png" alt="">
        </div>

        <div class="header__store">
          <p>奈雪的茶</p>
          <p>支付结果页（不包括广告）</p>
        </div>
      </div>
    </div>
    <div class="content">
      <div class="content__title"><span>请选择投诉原因</span></div>
      <div class="content__div">
        <ul class="content_ul">
          <li class="content__list-item"><div>欺诈</div></li>
          <li class="content__list-item"><div>色情</div></li>
          <li class="content__list-item"><div>诱导分享、关注</div></li>
          <li class="content__list-item"><div>不实信息</div></li>
          <li class="content__list-item"><div>暴力恐怖</div></li>
          <li class="content__list-item"><div>政治敏感</div></li>
          <li class="content__list-item"><div>收集个人隐私信息</div></li>
          <li class="content__list-item"><div>骚扰</div></li>
        </ul>
      </div>
    </div>



  </div>
</template>

<script>
    export default {
        name: "Complaint"
    }
</script>

<style scoped>
  .header, .content{
    background-color: lightgray;
  }
  .header__container{
    background-color: white;
    border: 1px solid white;
  }
  .header__title, .content__title{
    margin: 0;
    height: 50px;
    line-height: 50px;
    vertical-align: middle;
  }
  .container__pic{
    float: left;
    margin: 10px;
  }
  .container__pic img{
    height: 50px;
    width: 50px;
  }
  .content__div{
    background-color: white;
  }
  .content_ul{
    list-style-type: none;
    padding: 0;
    margin-top: 0;
  }
  .content__list-item{
    margin-top: 0;
    height: 40px;
    border-bottom:1px solid #ccc;
    padding-left: 10px;
    padding-top: 10px;
  }
  .header__store p{
    margin: 10px 10px;
  }

</style>
