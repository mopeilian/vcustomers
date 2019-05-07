<template>
    <div class="add contanier">
        <h1 class="page-header">修改用户</h1>
        <Alert v-if="alert" v-bind:message="alert"></Alert>
        <form v-on:submit.prevent="updateCustomer">
            <div class="well">
                <h4>用户信息</h4>
                <div class="form-group">
                    <label>姓名</label>
                    <input type="text" class="form-control" placeholder="name" v-model="customer.name"/>
                </div>
                <div class="form-group">
                    <label>电话</label>
                    <input type="text" class="form-control" placeholder="phone" v-model="customer.phone"/>
                </div>
                <div class="form-group">
                    <label>邮箱</label>
                    <input type="text" class="form-control" placeholder="email" v-model="customer.email"/>
                </div>
                <div class="form-group">
                    <label>学历</label>
                    <input type="text" class="form-control" placeholder="education" v-model="customer.education"/>
                </div>
                <div class="form-group">
                    <label>毕业学校</label>
                    <input type="text" class="form-control" placeholder="graduationschool" v-model="customer.gradutionschool"/>
                </div>
                <div class="form-group">
                    <label>职业</label>
                    <input type="text" class="form-control" placeholder="profession" v-model="customer.profession"/>
                </div>
                <div class="form-group">
                    <label>个人简介</label>
                    <!--<input type="text" class="form-control" placeholder="name" v-model="customer.profile"/>-->
                    <textarea class="form-control" row="10" v-model="customer.profile">profile</textarea>
                </div>
                <button type="submit" class="btn btn-primary">确认</button>
            </div>
        </form>
    </div>
</template>

<script>
    import Alert from "./Alert"
    export default {
        name: 'add',
        data () {
            return {
                customer:[],
                alert:""
            }
        },
        methods:{
            fetchCustomer(id){
                this.$http.get("http://localhost:3000/users/"+id)
                    .then((response)=>{
//                        console.log(response.body);
                        this.customer=response.data;
                    })
            },
            updateCustomer(e){
                if(!this.customer.name || !this.customer.phone || !this.customer.email){
//                    console.log("请添加用户信息")
                    this.alert="请添加用户信息";
                }else{
                    var updateCustomer = {
                        name:this.customer.name,
                        phone:this.customer.phone,
                        email:this.customer.email,
                        education:this.customer.education,
                        gradutionschool:this.customer.gradutionschool,
                        profession:this.customer.profession,
                        profile:this.customer.profile
                    }
                    this.$http.put("http://localhost:3000/users/"+this.$route.params.id,updateCustomer)
                        .then((response)=>{
//                            console.log(response)
                            this.$router.push({path:'/',query:{alert:"用户信息修改成功！"}})
                        })
//                    e.preventDefault();
                }
//                e.preventDefault();//阻止默认事件
            }
        },
        created(){
            this.fetchCustomer(this.$route.params.id);
        },
        components:{
            Alert
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
