<template>
  <div class="bg-dark border border-success p-4 mb-4">
    <img :src="user.picture.large" alt="" class="rounded-circle user_img">
    <h6 class="my-3">{{user.name.first}} {{user.name.last}}</h6>
    <p class="text- small">
       {{user.email}}
    </p>
    <p class="text- small">
       {{user.location.state}}, {{user.location.country}}
    </p>
    <button
      class="btn btn-success"
      data-toggle="modal"
      data-target="#exampleModal"
      @click="showUser"
    >
      View
    </button>
    
  </div>
</template>

<script>
export default {
   props:["user"],
   data() {
       return {
           
       }
   },
   methods: {
       showUser: function(){
          this.$emit('userDetail', this.user);
      },
   }
}
</script>

<style>
  .small {
      font-size: smaller;
  }
  .mode {
      color: white !important;
  }
  .mode-content {
        background-color:#2c3e50 !important;
  }
  .modal-content {
  background-color: #2c3e50 !important;
  }
</style>