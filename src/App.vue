<template>
  <div id="app">
    <keep-alive exclude="Detail">
      <router-view/>        <!--显示当前路由地址所对应的内容-->
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style></style>
