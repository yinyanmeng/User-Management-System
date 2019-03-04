<template>
  <div class="details container">
    <div class="fanhui">
      <router-link to="/" class="btn btn-default">返回</router-link>
    </div>    
    <h1 class="page-header">
      用户信息
      <span class="pull-right">
        <router-link class="btn btn-primary" v-bind:to="'/edit/'+customer.id">编辑</router-link>
        <button class="btn btn-danger" v-on:click="delectCustomer(customer.id)">删除</button>
      </span>
    </h1> 
    <ul class="list-group">
      <li class="list-group-item">
        <span class="glyphicon glyphicon-asterisk">{{customer.phone}}</span>
      </li>
      <li class="list-group-item">
        <span class="glyphicon glyphicon-asterisk">{{customer.email}}</span>
      </li>      
    </ul>  
    <ul class="list-group">
      <li class="list-group-item">
        <span class="glyphicon glyphicon-asterisk">{{customer.education}}</span>
      </li>
      <li class="list-group-item">
        <span class="glyphicon glyphicon-asterisk">{{customer.graduationschool}}</span>
      </li> 
      <li class="list-group-item">
        <span class="glyphicon glyphicon-asterisk">{{customer.profession}}</span>
      </li>  
      <li class="list-group-item">
        <span class="glyphicon glyphicon-asterisk">{{customer.profile}}</span>
      </li>  

    </ul>     
  </div>
  
</template>

<script>
export default {
  name: 'customerdetails',
  data () {
    return {
      customer:""
    }
  },
  methods:{
    fetchCustomers(id){      
      this.$http.get("http://localhost:3000/users/"+id).then(function(response){        
        //console.log(response);
        this.customer=response.body;
      })
    },
    delectCustomer(id){
      //console.log(id);
      this.$http.delete("http://localhost:3000/users/"+id).then(function(response){
        this.$router.push({path:'/',query:{alert:"删除成功"}})
      })
    }
  },
  
  created(){    
    this.fetchCustomers(this.$route.params.id);
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.fanhui{margin-top: 108px}
.page-header {
    padding-bottom: 9px;
    margin: 28px 0 20px;
    border-bottom: 1px solid #eee;
}
</style>
