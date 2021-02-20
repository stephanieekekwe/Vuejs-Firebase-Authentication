<template>
  <div>
    <section class="col-md-4 offset-md-4">
      <div v-if="error" class="error">
        {{ error.message }}
      </div>
      <div class="card">
        <h5 class="card-header text-white text-center py-4 bg-dark">
          <strong>Sign up</strong>
        </h5>

        <!--Card content-->
        <div class="card-body px-lg-5 pt-0">
          <!-- Form -->
          <form @submit.prevent="pressed" class="text-left">
            <!-- E-mail -->
            <div class="md-form mt-5">
              <label for="Email" class="active">E-mail</label>
              <input type="email" v-model="email" class="form-control" />
            </div>

            <!-- Password -->
            <div class="md-form mt-3">
              <label for="Password" class="active">Password</label>
              <input type="password" v-model="password" class="form-control" />
              <small class="form-text text-muted mb-4">
                At least 8 characters and 1 digit
              </small>
            </div>

            <!-- Sign up button -->
            <button
              class="btn btn-outline-primary btn-rounded btn-block my-4 waves-effect z-depth-0"
              type="submit"
            >
              Sign in
            </button>
          </form>
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
  name: "Register",
  data() {
    return {
      email: "",
      password: "",
      error: "",
    };
  },

  methods: {
    async pressed() {
      try {
        var user = firebase
          .auth()
          .createUserWithEmailAndPassword(this.email, this.password);
        console.log(user);
        this.$router.replace({ name: "secret" });
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
