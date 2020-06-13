<style >
  body{
    min-height: 100vh;
    min-width: 100vw;
    background: #018eaf;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  display: flex;
  justify-content: center;

}
.form-group{
  margin: 0;
  padding: 30px;
  width: 100%;
  display: flex;
  background: #018eaf;
  justify-content: center;
}
form label {
  position: relative;
  display: block;

}
    input {
      font: 18px Helvetica, Arial, sans-serif;
      box-sizing: border-box;
      display: block;
      border: none;
      padding: 20px;
      width: 300px;
      margin-bottom: 20px;
      font-size: 18px;
      outline: none;
      transition: all 0.2s ease-in-out;
    }

      input placeholder {
        color: #999;
        font: 18px Helvetica, Arial, sans-serif;
      }


    span {
      color: #35dc9b;
      font: 13px Helvetica, Arial, sans-serif;
      position: absolute;
      top: 0px;
      left: 20px;
      opacity: 0;
      transition: all 0.2s ease-in-out;
    }


  input[type="submit"] {
    transition: all 0.2s ease-in-out;
    font: 18px Helvetica, Arial, sans-serif;
    border: none;
    background: #01c2f1;
    color: #fff;
    padding: 16px 40px;
  }
  .messg{
    color: #8ee100;
  }
  .error{
    color: red;
  }




</style>

<template>
  <div id="app">

    <div class="form-group">
    <form @submit.prevent="login">
      <div >
        <p class="error" v-if="$v.email.$dirty && !$v.email.required">Pole jest wymagane.</p>
        <p class="error"
        v-if="$v.email.$dirty && !$v.email.email">Adres email jest niepoprawny.</p>
      <label>
        <input type="email" placeholder="Email" v-model.lazy="email" @input="$v.email.$touch()">
        <span>Email</span>
      </label>
      </div>
      <label>
        <input id="passworld" type="password" v-model="password" placeholder="password">
        <span>Password</span>
      </label>
      <input type="submit" value="Send">

      <div class="error" v-if="error && !messg">
        <p class="form-input-hint float-right">Podałeś niepoprawne dane.</p>
      </div>
      <div class="messg" v-if="messg && !error">
        <p class="form-input-hint float-right">Zalogowałeś się</p>
      </div>
    </form>
    </div>

    </div>
</template>
<script>
  import axios from 'axios';
  import { validationMixin } from 'vuelidate';
  import { required, email } from 'vuelidate/lib/validators';
  export default {
    mixins: [validationMixin],
    data() {
      return {
        email: '',
        password: '',
        error: false,
        messg: false
      }

    },
    methods: {
      login() {
        if (this.password === 'error') {
          return this.error = true;
        }else{
          axios.post("https://dogz.studio/api/login", {
            name: this.email,
            password: this.password
          }).then(({data}) => {
            if(data.message === 'Login success!') {
              let val = this.messg = true
              console.log(data);
              window.Storage(data.token);
              console.log(data.token);
              return val;
            }
          })
            .catch(function (error) {

            });
        }

      },
    },
    validations: {
      email: {
        required,
        email,
      },
    },
  }
</script>
