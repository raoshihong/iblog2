<!-- 定义模版 -->
<template>
    <div>
        <input v-model="num1">
        <select v-model="opt">
            <option>+</option>
            <option>-</option>
        </select>
        <input v-model="num2">
        <button @click="caculate">=</button>
        <input v-model="sum">
    </div>
</template>
<!-- 自定义组件相关内容 -->
<script>
export default {
    data(){
        return {
            num1:0,
            opt:'+',
            num2:0,
            sum:0
        }
    },methods:{
        caculate:function(){
            //调用js的eval进行js解析
            this.sum = eval(this.num1 + this.opt + this.num2);
        }
    }
}
</script>
<style>

</style>