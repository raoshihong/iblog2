<!-- 定义模版 -->
<template>
    <!-- 必须要有一个root根节点-->
    <div>
        <label>name:<input type="text" v-model="name"></label>
        <input type="button" value="添加" @click="add">
        <input type="button" value="批量删除" @click="batchDelete" >
        <label>根据关键字查询<input type="text" v-model="keyword"></label>

        <table>
            <thead>
                <td>选择</td>
                <td>id</td>
                <td>name</td>
                <td>操作</td>
            </thead>
            <!-- 在这里直接通过search()方法返回数据 -->
            <tr v-for="p in search()" :key="p.id">
               <td><input type="checkbox" v-model="selectedNums" :value="p.id"></td>
               <td>{{p.id}}</td>
               <td>{{p.name}}</td>
               <!-- a标签点击会触发默认事件,通过prevent修饰符阻止默认事件 -->
               <td><a href="" v-on:click.prevent="del(p.id)">删除</a></td>
            </tr>
        </table>
    </div>
</template>
<!-- 自定义组件相关内容 -->
<script>
export default {
    data(){//定义组件数据属性
        return {
            name:null,
            selectedNums:[],
            keyword:'',
            persons:[
                {
                    id:1,
                    name:'zhangsan'
                },
                {
                    id:2,
                    name:'lisi'
                },
                {
                    id:3,
                    name:'wangwu'
                },
            ]
        }
    },
    methods:{
        add(){

            // this.persons.unshift({id:this.persons.length+1,name:this.name});
            if(this.name == null) return;
            //向数组中添加元素
            this.persons.push({id:this.persons.length+1,name:this.name});
            this.name = null;
        },
        del(id){
            //从数组中删除元素有很多中方式
            //第一种 先获取对应元素索引,再通过splice删除
            // const index = this.persons.findIndex(p=>p.id == id);
            // //操作persons数据属性,当data当数据属性变动时,vue会自动渲染视图
            // this.persons.splice(index,1);

            //第二种方式,使用some函数
            // this.persons.some((p,index)=>{
            //     if(p.id == id){
            //         this.persons.splice(index,1);
            //         return true;
            //     }
            // })

            //第三种 直接使用数组的filter函数
            var ps = this.persons.filter(p=>{
                if(p.id != id) return true;
            });
            this.persons = ps;
        },
        batchDelete(){
            console.log(this.selectedNum);
            this.persons = this.persons.filter(p=>{
                return !this.selectedNums.includes(p.id);
            })
            this.selectedNums = [];
        },
        search(){
            //修改data数据属性中的keyword,会重新渲染视图,所以search()方法会被再次调用
            //对persons元素进行关键字过滤
            return this.persons.filter(p=>{
                return p.name.includes(this.keyword);
            });
        }
    }
}
</script>
<style>

</style>