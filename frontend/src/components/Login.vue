<template>
  <div class="container">
    <form>
      <div class="header">
        <h1>Mina sidor</h1>
        <img src="@/assets/icons/close.svg" class="close" @click="closeLogin" />
      </div>
      <input type="email" placeholder="Email" required v-model="email" />
      <input
        type="password"
        placeholder="Lösenord"
        required
        v-model="password"
      />
      <button @click="login">Logga In</button>
      <button class="register" @click="register">Registrera</button>
      <p>Glömt Lösenordet?</p>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    closeLogin() {
      this.$store.dispatch("closeLogin");
    },
    register(e) {
      e.preventDefault();
      this.$router.push({ name: "Register" });
      this.$store.dispatch("closeLogin");
    },
    async login(e) {
      e.preventDefault();
      const loginInfo = {
        email: this.email,
        password: this.password,
      };
      await this.$store.dispatch("login", loginInfo);
      this.$store.dispatch("closeLogin");
      this.$router.push("/account");
    },
  },
};
</script>

<style scoped>
.container {
  background: rgba(0, 0, 0, 0.6);
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  height: 130%;
  width: 100%;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
  position: fixed;
}
form {
  width: 320px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 25px;
  background: #f6f6f6;
}
.header {
  display: flex;
  margin-bottom: 30px;
  width: 100%;
  justify-content: space-between;
}
h1 {
  font-size: 26px;
  color: black;
  width: 100%;
}
.close {
  width: 30px;
  margin-top: -30px;
  margin-right: -15px;
}
img:hover {
  cursor: pointer;
}
input {
  width: 80%;
  margin-bottom: 20px;
  padding: 15px;
  border: 2px solid #c0c0c0;
  outline-color: #e84b38;
  border-radius: 3px;
}
button {
  width: 90%;
  padding: 18px;
  margin-bottom: 20px;
  font-size: 16px;
  font-weight: bold;
  color: white;
  background: #e84b38;
  border: none;
  outline: none;
  border-radius: 3px;
  text-transform: uppercase;
}
button:hover {
  cursor: pointer;
}
.register {
  background: white;
  border: 2px solid #e84b38;
  color: #e84b38;
}
p {
  font-size: 13px;
  font-weight: bold;
  color: black;
}
p:hover {
  cursor: pointer;
}
</style>
