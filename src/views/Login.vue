<template>
  <div class="main-panel">
    <div class="content-wrapper d-flex align-items-center auth">
      <div class="row w-100">
        <div class="col-lg-4 mx-auto">
          <div class="auth-form-light text-left p-5">
            <div class="navbar-brand brand-logo">
              <img src="assets/img/logo.png" />
            </div>
            <h4>Selamat datang!</h4>
            <h6 class="font-weight-light">Login untuk mengakses aplikasi daily scrum.</h6>
            <form class="pt-3" method="post" action="#" v-on:submit.prevent="Login">
              <div class="form-group">
                <div class="input-group">
                  <div class="input-group-prepend bg-transparent">
                    <span class="input-group-text bg-transparent border-right-0">
                      <i class="mdi mdi-account-outline text-primary"></i>
                    </span>
                  </div>
                  <input
                    type="email"
                    class="form-control form-control-lg border-left-0"
                    id="email"
                    name="email"
                    v-model="email"
                    placeholder="E-Mail"
                    required
                  />
                </div>
              </div>
              <div class="form-group">
                <div class="input-group">
                  <div class="input-group-prepend bg-transparent">
                    <span class="input-group-text bg-transparent border-right-0">
                      <i class="mdi mdi-lock-outline text-primary"></i>
                    </span>
                  </div>
                  <input
                    type="password"
                    class="form-control form-control-lg border-left-0"
                    name="password"
                    id="password"
                    v-model="password"
                    placeholder="Kata Sandi"
                    required
                  />
                </div>
              </div>
              <div class="my-3">
                <input
                  type="submit"
                  name="submit"
                  class="btn btn-block btn-primary btn-lg font-weight-medium auth-form-btn"
                  value="MASUK"
                />
              </div>
            </form>
            <label>Belum terdaftar? <br/> <a href="/register"> Register </a></label>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        email: "",
        password: ""
      };
    },
    methods: {
      Login: function() {
        let email = this.email;
        let password = this.password;
        this.$store
          .dispatch("login", { email, password })
          .then(response => {
            console.log("berhasil");
            this.$router.push({ path: "/" });
          })
          .catch(err => console.log(err));
      },
      mounted() {
        if (!localStorage.getItem("Authorization") == null) {
          this.$router.push({ path: "/" });
        }
      }
    }
  };
</script>