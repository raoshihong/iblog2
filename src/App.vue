<template>
  <div id="app">
    <!-- 在vue模型中使用组件 -->
    <mytablelist></mytablelist>
  </div>
</template>

<script>

//引入单文件组件
import MyTableList from './components/MyTableList'

export default {
  components:{//注册组件
    'mytablelist':MyTableList
  }
}

</script>

<style>

</style>
