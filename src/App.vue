<template>
  <div id="app">
    <transition :name="transitionName">
      <router-view style=" transition: all 0.4s ease;"></router-view>
    </transition>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        transitionName: 'slide-left'
      }
    },
    components: { //引入组件
    },
    methods: { //执行的方法函数

    },
    watch: {
      '$route'(to, from) {
        if (to.path == '/') {
          this.transitionName = 'slide-right';
        } else {
          this.transitionName = 'slide-left';
        }
      }
    },
    created() { //只执行一次

    }
  }
</script>
<style lang="less">
  @import './assets/less/style.less';

  h1, h2 {
    font-weight: normal;
  }

  * {
    margin: 0;
    padding: 0;
  }

  li {
    list-style: none;
  }

  a {
    text-decoration: none;
  }
  .slide-left-enter, .slide-right-leave-active {
    opacity: 0;
    left:0;
    /*-webkit-transform: translate(50px, 0);*/
    /*transform: translate(50px, 0);*/
    transform: translateX(-30%);
  }
  .slide-left-leave-active, .slide-right-enter {
    opacity: 0;
    -webkit-transform: translate(50px, 0);
    transform: translate(50px, 0);
  }
</style>
