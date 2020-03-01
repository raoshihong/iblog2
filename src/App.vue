<template>
  <div id="app">
    <!-- 使用自定义组件 -->
    <mytest></mytest>
  </div>
</template>

<script>
//引入自定义组件
import MyTest from './components/MyTest'

export default {
  components:{//局部注册自定义组件
    'mytest':MyTest
  }
}

</script>

<style>

</style>
