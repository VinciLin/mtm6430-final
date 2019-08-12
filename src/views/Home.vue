<template>

    <div class=" card text-center bg-primary text-white rounded" style="max-width: 45rem; height: 25rem; margin: auto; margin-top: 3rem;">
      
      <h1>Welcome to My app</h1>
      
      <div class="card-body" style="">
        <p class="card-text">Please sign up if you are not a user. 
          <br/>If you already have an account, please sign in.</p>

        <!-- Sign in and Sign up button -->
        <button type="button" class="btn btn-light">
          <router-link v-if="!auth" :to="{ name: 'signup' }">Sign Up</router-link>
        </button>
        <button type="button" class="btn btn-light">
          <router-link v-if="!auth" :to="{ name: 'signin' }">Sign In</router-link>
        </button>  

      </div>
  </div>
</template>

<script>
import { mapState, mapActions, mapGetters} from "vuex";

export default {
  computed: {
    ...mapGetters({
      auth: "isauthenticated"
    })
  },
}
</script>


<style scoped>

.card {
  box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
}

h1 {
  padding-top: 2.5rem;
}

.card-body {
  padding-top: 4rem;
}

.btn-light {
  margin:2rem;
}

</style>
