<template>
  <div id="app">
    <Vheader></Vheader>
    <div class="tab">
      <a href="" class="tab-item">商品</a>
      <a href="" class="tab-item">评论</a>
      <a href="" class="tab-item">商家</a>
    </div>
    <div class="content">i am content</div>
  </div>
</template>

<script type="text/ecmascript-6">
  import header from 'components/header/header';
  export default {
    components: {
      Vheader: header
    }
  };
</script>

<style lang="scss">
  @import "./common/scss/base.scss";

  .tab {
    display: flex;
    width: 100%;
    height: 4rem;
    line-height: 4rem;
    a {
      flex: 1;
      text-align: center;
      font-size: 1.4rem;
      color: rgb(7,17,27);
    }
  }
</style>
