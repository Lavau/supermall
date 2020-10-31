<template>
    <div class="tab-bar-item" @click="itemClick">
      <div v-if="!isActive"><slot name="item-icon"></slot></div>
      <div v-else><slot name="item-icon-active"></slot></div>
      <div :style="activeStyle"><slot name="item-text"></slot></div>
    </div>
</template>

<script>
  export default {
    name: "TabBarItem",
    props: {
      path: String,
      activeColor: {
        type: String,
        default: "red"
      }
    },
    computed: {
      isActive() {
        return this.$route.path.indexOf(this.path) !== -1;
      },
      activeStyle() {
        return this.isActive ? {color: this.activeColor} : {};
      }
    },
    methods: {
      itemClick() {
        // this.isActive = !this.isActive;
        this.$router.replace(this.path);
      }
    }
  }
</script>

<style scoped>
  .tab-bar-item {
    /*与父元素 css 的 display:flex 结合使用*/
    /*使每个 tab-bar-item 平分空间*/
    flex: 1;

    text-align: center;  /*让每个 tab-bar-item 中的文字居中*/
    height: 49px;  /*设置每个 tab-bar-item 的高度为 49px*/

    font-size: 14px;
  }

  .tab-bar-item img {
    height: 24px;
    width: 24px;
    margin-top: 3px;
    margin-bottom: 2px;
    vertical-align: middle;  /*去除图片最下面多的 3 px （默认的）*/
  }

  .active {
    color: red;
  }
</style>
