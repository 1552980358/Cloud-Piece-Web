<template>
  <div id="div-initial-root">
    <div id="div-input-box">
      <input ref="input-url" id="input-url" v-model="inputURL" v-bind:placeholder="$t('auth.url')">
      <input ref="input-username" id="input-username" v-model="inputUsername" v-bind:placeholder="$t('auth.username')">
      <input ref="input-password" id="input-password" type="password" v-model="inputPassword" v-bind:placeholder="$t('auth.password')">
      <br>
      <div ref="div-input-button" id="div-input-button" @click="inputButtonClick">{{ $t('auth.connect') }}</div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Initial",
  data() {
    return {
      inputURL: '',
      inputUsername: '',
      inputPassword: '',
      divInputButton: ''
    }
  },
  methods: {
    inputButtonClick() {
      console.log('Input URL: ' + this.inputURL);
      console.log('Input Username: ' + this.inputUsername);
      console.log('Input Password: ' + this.inputPassword);

      if (this.inputURL.includes(' ') || this.inputUsername.includes(' ') || this.inputPassword.includes(' ')) {
        return;
      }

      let url = 'init?method=initial&url=' + this.inputURL + '&username=' + this.inputUsername + '&password=' + this.inputPassword;
      console.log('Initial with uri: ' + url);
      axios({
        url: url,
        method: 'GET',
        headers: {
          'Content-Type': 'multipart/form-data',
          'Access-Control-Allow-Origin': window.location.origin,
          'Access-Control-Allow-Methods': 'POST,GET,OPTIONS',
          'Access-Control-Allow-Headers': '*',
          'Access-Control-Max-Age': '0'
        },
      }).then(resp => {
        console.log(resp);
      });
    },
  },
  mounted() {
  },
}
</script>

<style scoped>

#div-initial-root {
  background-color: #32C8E6;
  width: 100vw;
  height: 100vh;
  display: table-cell;
  vertical-align: middle;
}

/** Input Option **/

#div-input-box {
  width: 17vw;
  margin: 0 auto;
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 10px;
  padding: 1vw;
}

input {
  width: 15vw;
  margin-left: 0.5vw;
  outline-style: none ;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 5px 5px 5px 5px;
  font-size: 18px;
  margin-bottom: 10px;
}

input:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075),0 0 8px rgba(102,175,233,.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075),0 0 8px rgba(102,175,233,.6)
}

#div-input-button {
  width: 15vw;
  margin-left: 0.5vw;
  border: 2px solid #32C8E6;
  padding: 5px;
  color: #32C8E6;
  cursor: pointer;
  font-size: 25px;
  text-align: center;
  border-radius: 5px;
  -moz-user-select: none;
  -khtml-user-select: none;
  user-select: none;
}

#div-input-button:hover {
  background-color: #32C8E6;
  color: white;
}

#div-input-button:active {
  color: #5E6AC4;
  background-color: white;
}

</style>