<template>
    <div id="app">
  <h4 class="head">Application</h4>
  <div class="container">
    <table class="table-responsive bordered highlight centered hoverable z-depth-2" v-show="persons.length">
      <thead>
        <tr>
          <th v-bind:key="column" v-for="column in columns">
            {{column}}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-bind:key="index" v-for="(person,index) in persons">
          <td>{{index}}</td>
          <td>
            {{person.lname}}
          </td>
          <td>
            {{person.fname}}
          </td>
          <td>
            {{person.age}} 
          </td>
          <td>
            {{person.job}}
          </td>
          <td>
            {{person.gender}}
          </td>
          <td style="width: 18%;">
            <a href="#modal" @click="edit(index)" class="btn waves-effect waves-light yellow darken-2"><i class="material-icons">edit</i>
            </a>
            <a href="#!" class="btn waves-effect waves-light red darken-2" @click="archive(index)"><i class="material-icons">Close</i>
            </a>
          </td>
        </tr>
        <tr>
        </tr>
      </tbody>
    </table>

    <table class="table-responsive centered bordered striped highlight z-depth-1 hoverable" v-show="bin.length">
      <thead>
        <tr>
          <th v-bind:key="column" v-for="column in columns">
            {{column}}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr  v-bind:key="index" v-for="(person,index) in bin">
          <td>{{index}}</td>
          <td>
            {{person.lname}}
          </td>
          <td>
            {{person.fname}}
          </td>
          <td>
            {{person.age}} 
          </td>
          <td>
            {{person.job}}
          </td>
          <td>
            {{person.gender}}
          </td>
          <td>
            <a href="#!" @click="restore(index)" class="btn waves-effect waves-light blue darken-2"><i class="material-icons">Open</i>
            </a>
            <a href="#!" @click="deplete(index)" class="btn waves-effect waves-light red darken-2"><i class="material-icons">Delete</i>
            </a>
          </td>
        </tr>
      </tbody>
    </table>
  

  <div id="modal" class="modal modal-fixed-footer">
    <div class="modal-content">
      <h4 class="center-align">Edit</h4>
      <div class="row">
        <form class="col s12">
          <div class="row">
            <div class="input-field col s6">
              <input placeholder="Doe" id="first_name" type="text" v-model="editInput.fname">
              <label for="first_name">First Name</label>
            </div>
              <div class="input-field col s6">
              <input placeholder="John" id="last_name" type="text" v-model="editInput.lname">
              <label for="last_name">Last Name</label>
            </div>
          </div>
          <div class="row">
            <div class="input-field col s6">
              <input placeholder="26" id="edit_age" type="text" v-model="editInput.age">
              <label for="edit_age">Age</label>
            </div>
            <div class="input-field col s6">
              <input placeholder="Teacher" id="edit_job" type="text" v-model="editInput.job">
              <label for="edit_job">Job</label>
            </div>
          </div>
          <div class="row">
            <div class="input-field col s12">
              <select id="edit_gender" type="text"  v-model="editInput.gender">
                  <option selected disabled>Gender</option>
                  <option value="Male">Male</option>
                <option value="Female">Female</option>
              </select>
            </div>
          </div> 
        </form>
      </div>
    </div>
    <div class="modal-footer">
      <a href="#!" @click="update" class="btn waves-effect waves-light"><i class="material-icons">Add</i></a>
    </div>
  </div>
</div>
    </div>
</template>
<script>
    export default {
        name:'app',
        data(){
            return{
                columns: ['Index', 'Last Name', 'First Name', 'Age', 'Job', 'Gender', 'Actions '],
    persons: [{
    }],
    bin: [],
    input: {
    },
                 editInput: {
                        lname: "",
                        fname: "",
                        age: "",
                        job: "",
                        gender: ""
                        }
                 }
            
               },
               methods: {
    //function to add data to table
    add: function() {
      this.persons.push({
        lname: this.input.lname,
        fname: this.input.fname,
        age: this.input.age,
        job: this.input.job,
        gender: this.input.gender
      });

      for (var key in this.input) {
        this.input[key] = '';
      }
      this.persons.sort(ordonner);
      this.$refs.lname.focus();
    },
    //function to handle data edition
    edit: function(index) {
      this.editInput = this.persons[index];
      console.log(this.editInput);
      this.persons.splice(index, 1);
    },
    //function to send data to bin
    archive: function(index) {
      this.bin.push(this.persons[index]);
      this.persons.splice(index, 1);
      this.bin.sort(ordonner);
    },
    //function to restore data
    restore: function(index) {
      this.persons.push(this.bin[index]);
      this.bin.splice(index, 1);
      this.bin.sort(ordonner);
    },
    //function to update data
    update: function(){
      // this.persons.push(this.editInput);
       this.persons.push({
        lname: this.editInput.lname,
        fname: this.editInput.fname,
        age: this.editInput.age,
        job: this.editInput.job,
        gender: this.editInput.gender
      });
       for (var key in this.editInput) {
        this.editInput[key] = '';
      }
      this.persons.sort(ordonner);
    },
    //function to defintely delete data 
    deplete: function(index) {
      // console.log(this.bin[index]);
      this.bin.splice(index, 1);
    }
  }
             
    

}
var ordonner = function(a, b) {
  return (a.lname > b.lname);
};


</script>


<style>

div:first-child{
  margin: 20px 0; 
}


</style>
