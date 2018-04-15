<template>
  <div class="edit container">
    <h1 class="page-header">添加用户</h1>
    <form v-on:submit="addCustomer">
      <div class="well">
        <h4>用户信息</h4>
        <div class="form-group">
          <label>姓名</label>
          <input type="text" class="form-control" placeholder="name"v-model="customer.name"/>
        </div>
        <div class="form-group">
          <label>电话</label>
          <input type="text" class="form-control" placeholder="phone"v-model="customer.phone"/>
        </div>
        <div class="form-group">
          <label>邮箱</label>
          <input type="text" class="form-control" placeholder="email"v-model="customer.email"/>
        </div>
        <div class="form-group">
          <label>学历</label>
          <input type="text" class="form-control" placeholder="education"v-model="customer.education"/>
        </div>
        <div class="form-group">
          <label>毕业学校</label>
          <input type="text" class="form-control" placeholder="graduationschool"v-model="customer.graduationschool"/>
        </div>
        <div class="form-group">
          <label>职业</label>
          <input type="text" class="form-control" placeholder="profession"v-model="customer.profession"/>
        </div>
        <div class="form-group">
          <label>简介</label>
          <!--<input type="text" class="form-control" placeholder="profile"v-model="customer.profile"/>-->
          <textarea class="form-control" rows="10" v-model="customer.pofile"></textarea>
        </div>
        <button class="btn btn-primary">提交</button>
      </div>
    </form>
  </div>
</template>

<script>
  export default {
    name: "edit",
    data(){
      return{
        customer:[]
      }
    },
    methods:{
      addCustomer(e){
        if(!this.customer.name||!this.customer.phone||!this.customer.email){
          console.log("请添加对应的信息")
        }else{
          var updateCustomer={
            name:this.customer.name,
            phone:this.customer.phone,
            email:this.customer.email,
            education:this.customer.education,
            graduationschool:this.customer.graduationschool,
            profession:this.customer.profession,
            profile:this.customer.profile
          }
          this.$http.post("http://localhost:3000/users",updateCustome).then(function (response) {
            this.$router.push({"path":"/",query:{alert:"用户信息添加成功！"}})
          })
        }
        e.preventDefault();
      }
    }
  }
</script>

<style scoped>

</style>
