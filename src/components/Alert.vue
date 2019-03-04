<template>
  <div class="alert alert-warning alert-dismissible" role="alert">
  <button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
  {{message}}
  
</div>
  
</template>

<script>
export default {
  name: 'alert',
  props:["message"],
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.alert {
    padding: 15px;
    margin-bottom: 0px;
    border: 1px solid transparent;
    border-radius: 4px;
    margin-top:80px;
}
</style>
