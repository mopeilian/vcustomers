<template>
    <div class="details contanier">
        <router-link to="/" class="btn btn-default">返回</router-link>
        <h1 class="page-header">
            {{customer.name}}
            <span class="pull-right">
                <router-link class="btn btn-primary" v-bind:to="'/edit/'+customer.id">编辑</router-link>
                <button class="btn btn-danger" v-on:click="deleteCustomer(customer.id)">删除</button>
            </span>
        </h1>
        <ul class="list-group">
            <li class="list-group-item"><span class="glyphicon glyphicon-phone-altk">{{customer.phone}}</span></li>
            <li class="list-group-item"><span class="glyphicon glyphicon-envelope">{{customer.email}}</span></li>
        </ul>
        <ul class="list-group">
            <li class="list-group-item"><span class="glyphicon glyphicon-flag">{{customer.education}}</span></li>
            <li class="list-group-item"><span class="glyphicon glyphicon-lock">{{customer.gradutionschool}}</span></li>
        </ul>
        <ul class="list-group">
            <li class="list-group-item"><span class="glyphicon glyphicon-book">{{customer.profession}}</span></li>
            <li class="list-group-item"><span class="glyphicon glyphicon-tasks">{{customer.profile}}</span></li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'customerdetails',
        data () {
            return {
                customer:''
            }
        },
        methods:{
            fetchCustomers(id){
                this.$http.get("http://localhost:3000/users/"+id)
                    .then((response)=>{
//                    .then(function(response){
                        console.log(response)
                        this.customer=response.data;
//                        this.customer=response.body;
                    })
            },
            deleteCustomer(id){
//                console.log(id);
                this.$http.delete("http://localhost:3000/users/"+id)
                    .then((responce)=>{
//                    .then(function(responce){
                        this.$router.push({path:"/",query:{alert:"删除用户成功"}})
                })
            }
        },
        created(){
            this.fetchCustomers(this.$route.params.id);
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
