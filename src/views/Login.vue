<template>
  <div>
    <section class="col-md-4 offset-md-4">
      <div v-if="error" class="error">
        {{ error.message }}
      </div>
      <div class="card">
        <h5 class="card-header text-white text-center py-4 bg-primary">
          <strong>Login</strong>
        </h5>

        <!--Card content-->
        <div class="card-body px-lg-5 pt-0">
          <!-- Form -->
          <form @submit.prevent="login" class="text-left">
            <!-- E-mail -->
            <div class="md-form mt-5">
              <label for="Email" class="active">E-mail</label>
              <input type="email" v-model="email" class="form-control" />
            </div>

            <!-- Password -->
            <div class="md-form mt-3">
              <label for="Password" class="active">Password</label>
              <input type="password" v-model="password" class="form-control" />
            </div>

            <!-- Sign up button -->
            <button
              class="btn btn-outline-primary btn-rounded btn-block my-4 waves-effect z-depth-0"
              type="submit"
            >
              Sign in
            </button>
          </form>
          <span>
            Need an account click here to
            <router-link to="/register">Sign Up</router-link>
          </span>
          <!-- Form -->
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import firebase from "firebase/app";
import "firebase/auth";
export default {
  name: "Login",
  data() {
    return {
      email: "",
      password: "",
      error: "",
    };
  },

  methods: {
    async login() {
      try {
        const login = await firebase
          .auth()
          .signInWithEmailAndPassword(this.email, this.password);
        console.log(login);
        this.$router.replace({ name: "secret" });
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
