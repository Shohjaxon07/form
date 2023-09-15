<script setup>
import { ref } from "vue";
import axios from "axios";
let name = ref("");
let email = ref("");
let password = ref("");
let message = ref("");


const addRegister = async () => {
  

  if (name.value !== password.value) {
    message.value = 'passwords don\'t match'
  }
  else{
    await axios.post('https://test-auth-render.onrender.com/users/register',{
    name:name.value,
    email:email.value,
    password:password.value
  })
    message.value = 'succesfull'
  }
 
}
</script>

<template>
  <div class="container">
    <div class="form-box">
      <div class="form-value">
        <form class="mt-5" @submit.prevent="addRegister">
          <h2>Sign in</h2>
          <h3 class="h3">{{ message }}</h3>
          
         
          <div class="inputbox">
            <ion-icon name="person-circle-outline"></ion-icon>
            <input type="email" required id="email" v-model="email" />
            <label for="">Email</label>
          </div>
          <div class="inputbox">
            <ion-icon name="lock-closed-outline"></ion-icon>
            <input type="text" id="name" required v-model="name" />
            <label for="">Password</label>
          </div>
          <div class="inputbox">
            <ion-icon name="lock-closed-outline"></ion-icon>
            <input type="text" id="password" v-model="password" required />
            <label for="">Confirm password</label>
          </div>
          <button type="submit">Sign in</button>
          <div class="bottom"></div>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
.h3{
  color: rgb(213, 213, 213);
  text-align: center;
  margin-top: 10px;
}

* {
  margin: 0;
  padding: 0;
  font-family: "poppins", sans-serif;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  width: 100%;

  background: url("https://source.unsplash.com/cPccYbPrF-A");
  background-position: center;
  background-size: cover;
}
.form-box {
  position: relative;
  width: 400px;
  height: 450px;
  background: transparent;
  border: 2px solid rgba(255, 255, 255, 0.5);
  border-radius: 20px;
  backdrop-filter: blur(15px);
  display: flex;
  justify-content: center;
  align-items: center;
}
h2 {
  font-size: 2em;
  color: #fff;
  text-align: center;
}
.inputbox {
  position: relative;
  margin: 30px 0;
  width: 310px;
  border-bottom: 2px solid #fff;
}
.inputbox label {
  position: absolute;
  top: 50%;
  left: 5px;
  transform: translateY(-50%);
  color: #fff;
  font-size: 1em;
  pointer-events: none;
  transition: 0.5s;
}
input:focus ~ label,
input:valid ~ label {
  top: -5px;
}
.inputbox input {
  width: 100%;
  height: 50px;
  background: transparent;
  border: none;
  outline: none;
  font-size: 1em;
  padding: 0 35px 0 5px;
  color: #fff;
}
.inputbox ion-icon {
  position: absolute;
  right: 8px;
  color: #fff;
  font-size: 1.2em;
  top: 20px;
}
button {
  width: 100%;
  height: 40px;
  border-radius: 40px;
  background: #fff;
  border: none;
  outline: none;
  cursor: pointer;
  font-size: 1em;
  font-weight: 600;
}
.bottom {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  color: #fff;
  margin-top: 20px;
}
label a {
  text-decoration: none;
  color: #fff;
}
</style>
