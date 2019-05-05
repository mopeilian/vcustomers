<template>
    <div class="add contanier">
        <h1 class="page-header">添加用户</h1>
        <form v-on:submit="addCustomer">
            <h4>用户信息</h4>
            <div class="form-group">
                <label>姓名</label>
                <input type="text" class="form-control" placeholder="name" v-model="customer.name"/>
            </div>
            <div class="form-group">
                <label>电话</label>
                <input type="text" class="form-control" placeholder="name" v-model="customer.phone"/>
            </div>
            <div class="form-group">
                <label>邮箱</label>
                <input type="text" class="form-control" placeholder="name" v-model="customer.email"/>
            </div>
            <div class="form-group">
                <label>学历</label>
                <input type="text" class="form-control" placeholder="name" v-model="customer.education"/>
            </div>
            <div class="form-group">
                <label>毕业学校</label>
                <input type="text" class="form-control" placeholder="name" v-model="customer.graduationschool"/>
            </div>
            <div class="form-group">
                <label>职业</label>
                <input type="text" class="form-control" placeholder="name" v-model="customer.profession"/>
            </div>
            <div class="form-group">
                <label>个人简介</label>
                <!--<input type="text" class="form-control" placeholder="name" v-model="customer.profile"/>-->
                <textares class="form-control" row=""10 v-model="customer.profile"></textares>
            </div>
            <button type="submit" class="btn primary">添加</button>
        </form>
    </div>
</template>

<script>
    export default {
        name: 'add',
        data () {
            return {
                customers:[]
            }
        },
        method:{
            addCustomer(e){
                console.log(123);
               /* if(!this.customer.name || !this.customer.phone || !this.customer.email){
                    console.log("请添加用户信息")
                }else{
                    let newCustomer = {
                        name:this.customer.name,
                        phone:this.customer.phone,
                        email:this.customer.email,
                        education:this.customer.education,
                        gradutionschool:this.customer.gradutionschool,
                        profession:this.customer.profession,
                        profile:this.customer.profile
                    }
                    this.$http.post("http://localhost:3000/users",newCustomer)
                        .then(function(response){
                            console.log(response)
                        })
                }*/
                e.preventDefault();//阻止默认事件
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
