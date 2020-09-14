<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <div class="box">混入</div>
    <div class="floor">继承</div>
    <div class="floor">继承</div>
    <div class="fuhao">符号<p class="fuhao-over">&</p></div>
    <a href="#">hover</a>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>

<style lang="scss" scoped>
// 1.引入
@import './reset.scss';
// 2.变量
$themeColor:red;
//3.混入
@mixin commonStyle($radius){
  border-radius:$radius ;
  background: gold;
  font-size: 16px;
  height: 40px;
  width: 40px;
  line-height: 40px;
  text-align: center;
}
//4.继承
%commonCell{
  width: 50%;
  height: 100px;
  margin: 0 auto;
  background-color: green;
  margin-bottom: 10px;
}
.home{
  color:$themeColor;
  .box{
    @include commonStyle(8px)
  }
  .floor{
    @extend %commonCell;
    border: 10px solid #000;
  }
}
//5.符号
.fuhao{
  width: 50%;
  height: (400-200+200)*2px/8;
  background-color: hotpink;
  margin: 0 auto;
  &-over{
    color: #ccc;
  }
}
a:hover{
  color: aqua;
  border-bottom: 1px solid #000;
}
</style>
