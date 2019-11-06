<template>
    <div>
        <form @submit.prevent="onSubmit">
        <h1 id="aon">
            Create your profile
        </h1>
        <div class="mt-2">Name: {{ text1 }}</div>
        <b-form-input v-model="text1" size="sm" placeholder="Enter your name"></b-form-input>  
        <div class="mt-2">Email: {{ text2 }}</div>
        <b-form-input v-model="text2" size="sm" placeholder="Enter your email"></b-form-input>
        <div class="mt-2">Department: {{ selected1 }}</div>
        
        <b-form-select v-model="selected1" :options="options1" size="sm" class="mt-3"></b-form-select>
        
        <br>
        <br>
        <center>
        <b-button  size="sm" class="my-2 my-sm-0" type="submit">Add</b-button> 
        </center> 
        </form>
    </div>
</template>

<script>
    export default {
        props :['creaTe'],
        data(){
            return{
                text1:'',
                text2:'',
                selected1 : null,
                options1: [
                    {value:null,text:'Select'},
                    {text:'Chairman'},
                    {text:'Vice Chairman'},
                    {text:'President'},
                    {text:'Vice-President'},
                    {text:'Senior Advisor'},
                    {text:'General Manager'},
                ]
            }      
        },
        methods:{
            onSunmit(){
                   if(this.text1.trim()){
                       const addData ={
                           id: Date.now(),
                           text1:this.text1,
                           completed: false
                       }
                       this.$$emit('add-data',addData)
                       this.text1=''
                   } 
            }
        }     
    }
</script>

<style lang="scss" scoped>

</style>