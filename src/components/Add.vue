<template>
  <div class="add container">
  <Alert v-if="alert" v-bind:message="alert"></Alert>
    <h1 class="page-header">添加用户</h1>
    <form v-on:submit="addCustomer">
      <div class="well">
        <h4>添加用户</h4>
        <div class="form-group">
          <label for="">姓名</label>
          <input type="text" class="form-control" placeholer="name" v-model="customer.name">
          <label for="">电话</label>
          <input type="text" class="form-control" placeholer="name" v-model="customer.phone">
          <label for="">邮箱</label>
          <input type="text" class="form-control" placeholer="name" v-model="customer.email">
          <label for="">学历</label>
          <input type="text" class="form-control" placeholer="name" v-model="customer.education">
          <label for="">毕业学校</label>
          <input type="text" class="form-control" placeholer="name" v-model="customer.graduationschool">
          <label for="">职业</label>
          <input type="text" class="form-control" placeholer="name" v-model="customer.profession">
          <label for="">个人简介</label>
          <textarea rows="10" class="form-control" v-model="customer.profile"></textarea>

        </div>
        <button type="submit" class="btn btn-primary">添加</button>
      </div>
    </form>
     
    </div>
  
</template>

<script>
import Alert from './Alert'
export default {
  name: 'add',
  data () {
    return {
      customer:{},
      alert:""
    }
  },
  methods:{
    addCustomer(e){
      //console.log('111');
      if(!this.customer.name || !this.customer.phone || !this.customer.email){
        //console.log('添加对应信息');
        this.alert="添加对应信息";
      }else{
        let newCustomer={
          name:this.customer.name,
          phone:this.customer.phone,
          email:this.customer.email,
          education:this.customer.education,
          graduationschool:this.customer.graduationschool,
          profession:this.customer.profession,
          profile:this.customer.profile
        }
        this.$http.post("http://localhost:3000/users",newCustomer).then(function(response){
          //console.log(response);
          this.$router.push({path:'/',query:{alert:"用户信息添加成功"}});

        })
      }
      e.preventDefault();
    }

  },
  components:{
    Alert
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.page-header {
    padding-bottom: 9px;
    margin: 108px 0 20px;
    border-bottom: 1px solid #eee;
}
</style>
