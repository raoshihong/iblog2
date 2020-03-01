<!-- 定义模版 -->
<template>
    <!-- 必须要有一个root根节点-->
    <div>
        <label>用户名:<input type="text" v-model="loginDto.username"></label>
        <label>密码:<input type="password" v-model="loginDto.password"></label>
        <input type="button" @click="login" value="登录">
    </div>
</template>
<!-- 自定义组件相关内容 -->
<script>
//引入axios
import axios from 'axios'

export default {
    data(){
        return {
            loginDto:{
                username:null,
                password:null
            }
        }
    },
    methods:{
        login(){
            //在这里进行ajax请求
            var config = {//定义配置
            }
            //使用post请求
            axios.post("http://localhost:8081/react/api/login",this.loginDto,config)
                .then(function(res){
                    //获取响应数据
                    console.log(res);
                })
        }                       
    }
}
</script>
<style>

</style>