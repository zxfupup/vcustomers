<template>
  <div class="customers container">
    <alert v-if="alert" v-bind:message="alert"></alert>
    <h1 class="page-header">customers</h1>
    <table class="table table-striped table-bordered">
       <thead>
        <tr>
          <th>姓名</th>
          <th>电话</th>
          <th>邮箱</th>
          <th></th>
        </tr>

       </thead>
      <tbody>
        <tr v-for="customer in customers">
          <td>{{customer.name}}</td>
          <td>{{customer.phone}}</td>
          <td>{{customer.email}}</td>
          <td><router-link v-bind:to="'/customer/'+customer.id" class="btn btn-default">详情</router-link></td>
        </tr>
      </tbody>
    </table>


  </div>
</template>

<script>
  import Alert from "./Alert"
export default {
  components: {Alert},
  name: 'customers',
  data () {
    return {
      customers:[],
      alert:""
    }
  },
  methods:{
    fetchCustomers(){
      this.$http.get("http://localhost:3000/users").then(function (response) {
        this.customers=response.body;
      })
    }
  },
  created(){
    if(this.$route.query.alert){
      this.alert=this.$route.query.alert;
    }
   this.fetchCustomers();
  },
  updated(){
    this.fetchCustomers();
  },
  comments:{
    Alert
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
