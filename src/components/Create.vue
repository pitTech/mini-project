<template>
    <div>
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
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>

</style>