<template>
  <div>
    <User />
  </div>
</template>

<script>
// @ is an alias to /src
import User from '@/components/Users.vue'

export default {
  name: 'HomeView',
  components: {
    User
  }
}
</script>
