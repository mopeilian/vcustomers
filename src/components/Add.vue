<template>
    <div class="add contanier">
        <h1 class="page-header">添加用户</h1>
        <Alert v-if="alert" v-bind:message="alert"></Alert>
        <form v-on:submit.prevent="addCustomer">
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
                <button type="submit" class="btn btn-primary">添加</button>
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
            addCustomer(e){
                if(!this.customer.name || !this.customer.phone || !this.customer.email){
//                    console.log("请添加用户信息")
                    this.alert="请添加用户信息";
                }else{
                    var newCustomer = {
                        name:this.customer.name,
                        phone:this.customer.phone,
                        email:this.customer.email,
                        education:this.customer.education,
                        gradutionschool:this.customer.gradutionschool,
                        profession:this.customer.profession,
                        profile:this.customer.profile
                    }
                    this.$http.post("http://localhost:3000/users",newCustomer)
                        .then((response)=>{
//                            console.log(response)
                            this.$router.push({path:'/',query:{alert:"用户信息添加成功！"}})
                        })
//                    e.preventDefault();
                }
//                e.preventDefault();//阻止默认事件
            }
        },
        components:{
            Alert
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
