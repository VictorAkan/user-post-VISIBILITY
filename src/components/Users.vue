<template>
  <div class="container py-5">
    <div class="row mx-0 px-0">
      <div v-for="(user) in users" :key="user" class="col col-md-4">
        <User :user="user" @userDetail="show"/>
        <!-- <User :user="modal" /> -->
      </div>
    </div>
  </div>

  <Modal :user="user"/>

  <div class="loading" v-if="isFetching">
    <h5>Loading Users.....</h5>
    <h5 v-if="isError">Error Fetching Users....</h5>
  </div>
</template>

<script>
import axios from "axios";
import User from "./User.vue";
import Modal from "./userModal.vue"
export default {
   data() {
       return {
           users: "",
           user: {},
           isFetching: true,
           isError: false,
       };
   },
   components: {
       User,
       Modal
   },
   methods: {
       async getUsers() {
         this.isFetching = true;
           try {
              let response = await axios.get("https://randomuser.me/api/?results=10");
              this.users = response.data.results;

              console.log(this.users);
              this.isFetching = false;
           } catch(error) {
              this.isError = true;
              console.log(error);
           }
       },
       show(user){
          this.user = user
       }
   },
   mounted() {
       this.getUsers();
   }
}
</script>

<style>

</style>