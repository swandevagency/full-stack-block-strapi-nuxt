<template>
  <div class="app-wrapper">
    <div class="login-dialogue-wrapper">
      <div class="login-title-wrapper">
        <h3>Login</h3>
      </div>
      <div class="login-content-wrapper">
        <input
          type="text"
          class="normal-input user-name-input"
          placeholder="Username"
          v-model="username"
        />
        <div class="login-user-information-wrapper">
          <input
            type="password"
            class="normal-input user-name-input"
            placeholder="Password"
            v-model="password"
          />
        </div>
      </div>
      <div class="login-controls-wrapper">
        <Button
          class="login-control-button"
          buttonText="Skip"
          buttonStyle="normal"
          @click.native="goToHomePage"
        />
        <Button
          class="login-control-button"
          buttonText="Login"
          buttonStyle="important"
          @click.native="login"
        />
      </div>
    </div>
  </div>
</template>

<script>
import button from "../components/button.vue";
import Button from "../components/button.vue";
export default {
  data() {
    return {
      username: "",
      password: ""
    };
  },
  components: { button },
  methods: {
    goToHomePage() {
      location.href = "homepage";
    },
    async login() {
      const response = await this.$axios
        .post("http://localhost:1337/auth/local", {
          identifier: this.username,
          password: this.password
        })
        .then(res => res)
        .catch(error => {
          alert("Access denied!");
        });
      if (response.status == "200") {
        window.localStorage.setItem("token", response.data.jwt);
        this.goToHomePage();
      } else return;
    }
  }
};
</script>
<style>
.app-wrapper {
  display: grid;
  height: 100vh;
  align-content: center;
}
.login-dialogue-wrapper {
  box-sizing: border-box;
  padding: 2% 2%;
  width: 30vw;
  margin: auto;
  background-color: #ffffff;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, 0.16);
}
.login-title-wrapper > h3 {
  color: #3d2c8d;
  font-size: 2em;
  font-weight: 300;
  margin: 0 auto 0.5em;
  padding: 0 0 0.8em;
  border-bottom: 1px solid rgba(0, 0, 0, 0.16);
  text-align: center;
}
.login-content-wrapper {
  margin: 2em 0;
  padding: 0 10%;
}
.login-controls-wrapper {
  display: flex;
  justify-content: center;
}
.login-control-button {
  margin: 0 0.5em;
}
.normal-input {
  outline: none;
  border: none;
  border-bottom: 1px solid rgba(0, 0, 0, 0.16);
  box-sizing: border-box;
  color: #111;
  width: 100%;
  margin-bottom: 1em;
  padding: 1em;
  font-size: 1em;
}
.normal-input::placeholder {
  opacity: 0.5;
}
</style>
