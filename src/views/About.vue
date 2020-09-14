<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div class="floor">混入不带参</div>
    <div class="about-box">混入带参</div>
    <div class="item">匹配</div>
    <div class="key">继承</div>
  </div>
</template>
<style lang="less" scoped>
//1.引入
@import './reset.less';
//2.变量
@themeColor: yellow;
//3.混入
.center() {
  text-align: center;
  line-height: 40px;
  height: 40px;
  width: 50%;
  background: aqua;
}
//4.混入（带参）
.transformz(@a:90deg,@b:120px) {
  transform: rotateZ(@a);
  height: @b;
  width: @b;
  background-color: pink;
}
//5.匹配模式
.marginz(left,@m) {
  margin-left: @m;
}
//6.@arguments表示mixin的所有入参
.borderz(@a,@b,@c) {
  border: @arguments;
}
//7.继承
.extendz {
  color: #000;
  width: 40%;
  height: 200px;
  background-color: red;
}
.about {
  color: @themeColor;
  .floor {
    .center;
  }
  &-box {
    .transformz(@a:180deg,@b:200px);
  }
  .item {
    height: 40px;
    width: 50%;
    background-color: green;
    .marginz(left,100px);
    //写法一： .borderz(@a:5px+5,@b:solid,@c:#000)
    //写法二：
    .borderz(5px+5,solid,#000)//8.符号运算;
  }
  .key {
    &:extend(.extendz);
  }
}
</style>