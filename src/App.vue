<template>
<div>
  <b-navbar-brand href="#">Emoloyee</b-navbar-brand>
    <createUser @add-data="addData"/>
    <br>
    <listUser @add-data="addData" />
</div>  
</template>

<script>
import createUser from './components/createUser'
import listUser from './components/listUser'
export default {
  name: 'app',

  components: {
    createUser,listUser
  },
  methods:{
    addData(data){
      this.addData.push(data)
    } 
  }


}
</script>

<style>

</style>
