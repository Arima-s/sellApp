<template>
  <div id="app">
    <Vheader :seller="seller"></Vheader>
    <div class="tab">
      <a v-link="{ path:'/goods' }" class="tab-item">商品</a>
      <a v-link="{ path:'/ratings' }" class="tab-item">评论</a>
      <a v-link="{ path:'/seller' }" class="tab-item">商家</a>
    </div>
    <router-view></router-view>
  </div>
</template>

<script type="text/ecmascript-6">
  import header from 'components/header/header';

  export default {
    data() {
      return {
        seller: {}
      };
    },
    created() {
      this.$http.get('/api/seller').then((response) => {
        response = response.body;
        if (response.errno === 0) {
          this.seller = response.data;
          console.log(this.seller);
        }
      });
    },
    components: {
      Vheader: header
    }
  };
</script>

<style lang="scss">

  @import "./common/scss/base.scss";
  @import "./common/scss/mixin.scss";

  .tab {
    display: flex;
    width: 100%;
    height: 4rem;
    line-height: 4rem;
    @include border-1px(rgba(7, 17, 27, 0.1));
    a {
      flex: 1;
      text-align: center;
      font-size: 1.4rem;
      color: rgb(7,17,27);
      &.active {
        color: rgb(240, 20, 20);
      }
    }
  }
</style>
