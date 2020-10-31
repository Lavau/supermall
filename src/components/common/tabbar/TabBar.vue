<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: "TabBar"
  }
</script>

<style scoped>
  #tab-bar {
    /*使tab-bar内的布局为 flex*/
    display: flex;

    background-color: #f6f6f6;  /*设置背景色*/

    /*使 tab-bar 位于最下方*/
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;

    box-shadow: 0px -3px 1px rgba(100, 100, 100, 0.1);  /*设置 tab-bar 上方的阴影*/
  }
</style>
