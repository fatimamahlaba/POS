<template>
  <form @submit.prevent="login" class="form border">
    <h2 class="form-heading">Login</h2>
    <input
      class="form-input border-input"
      type="email"
      v-model="email"
      placeholder="Email"
    />
    <input
      class="form-input border-input"
      type="password"
      v-model="password"
      placeholder="Password"
    />
    <button type="submit" class="form-btn border">Login</button>
    <div class="form-social-login">
      <button class="form-btn border form-social-btn">
        <i class="fab fa-google"></i>
      </button>
      <button class="form-btn border form-social-btn">
        <i class="fab fa-facebook"></i>
      </button>
    </div>
  </form>
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      isLoggedIn: true
    };
  },
  methods: {
  login(){
    fetch('http://localhost:2000/users', {
     method: 'PATCH',
     body: JSON.stringify({
      email: this.email,
      password: this.password,
  }),
  headers: {
    'Content-type': 'application/json; charset=UTF-8',
  },
})
  .then((response) => response.json())
  .then((json) => {
   localStorage.setItem("jwt", json.jwt);
   alert("User logged in");
   this.$router.push({ name: "Products"});
  })
  .catch((err) => {
    alert(err);
  });
  },
 },
};
</script>
<style>
.border {
border: none !important;
}


.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 40px;
  gap: 20px;
  width: 100%;
  margin-inline: auto;
  max-width: 600px;
  margin-top: 150px;
  z-index: 1;
}

.form-heading {
  text-align: center;
  text-transform: uppercase;
}

.form-input,
.form-btn {
  border: none;
  outline: none;
  padding: 20px;
  z-index: 1;
}

.form-btn {
  cursor: pointer;
  transition: all 0.1s linear;
}

.form-btn:hover {
  transform: scale(1.05);
}

.form-social-login {
  display: flex;
  justify-content: space-between;
}

.form-social-btn {
  width: 45%;
  color: #333;
}
</style>
