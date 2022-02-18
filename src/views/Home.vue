<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1>HOMEW</h1>
    <pre v-if="arrayPassword.length>0">{{arrayPassword[0]}}</pre>
    <pre v-else>cargando...</pre>
    <button @click="getPassword">password</button>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
import {reactive} from 'vue';
export default {
  name: 'Home',
  setup() {
    let arrayPassword=reactive([]);
    const getPassword = () => {
      axios(`https://backend-passwords.herokuapp.com/password/6/False/True/True`)
          .then(response => {
            arrayPassword[0]=reactive(response.data);
            console.log(arrayPassword);
          })
          .catch(error => {
            console.error(error);
          })
    }
    return {
      getPassword,
      arrayPassword,
    }
  }
}
</script>
