<template>
  <div class="card" >
    <b-card-header>Registration Form</b-card-header>
    <b-card-body>
      <b-form>
        <b-row>
          <b-col>
          <b-form-group id="nameGroup" label="FirstName" label-for="firstname">
            <b-form-input
               id="firstname"
               type="text"
               v-model="form.firstname"
               required
               placeholder="enter name"/>
          </b-form-group>
           <b-form-group id="nameGroup" label="Lastname" label-for="lastname">
            <b-form-input
               id="lastname"
               type="text"
               v-model="form.lastname"
               required
               placeholder="enter lastname"/>
          </b-form-group>
           <b-form-group id="nameGroup" label="Email" label-for="email">
            <b-form-input
               id="email"
               type="email"
               v-model="form.email"
               required
               placeholder="enter email"/>
          </b-form-group>
           <b-form-group id="nameGroup" label="Password" label-for="password">
            <b-form-input
               id="password"
               type="password"
               v-model="form.password"
               required
               placeholder="enter password"/>
          </b-form-group>
          <b-button @click="savemodal">submit</b-button>
        </b-col>
        </b-row>
      </b-form>
    </b-card-body>

  </div>
</template>
<script>
import axios from "axios"
  export default{
    data(){
      return{
        form:{
          firstname:'',
          lastname:'',
          email:'',
          password:''
        },
        userData:[]
      }
    },
    methods:{
      savemodal(){
        console.log(this.form)
        axios.post("http://localhost:8081/registration", this.form)
             .then(res => {
              this.userData = res.data.data
             }).catch(err => {
              console.log(err);
             })

      }
    }
  }
</script>
<style >

</style>
