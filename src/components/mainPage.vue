<template>
  <div class="paper" align="center">
    <!--<div v-if="numberPage===null">-->
      <!--<div>-->
        <!--<button @click="vhod">Вход</button>-->
      <!--</div>-->
      <!--<div>-->
        <!--<button class="reg">Регистрация</button>-->
      <!--</div>-->
    <!--</div>-->
    <div v-if="numberPage===null" class="container">
      <div class="row" style="height: 100vh">
        <div class="col-sm" style="margin-top: 30vh">
          <div>
            <div class="row justify-content-center">
                <div class="col-md-1">
                  <b-button size='lg' variant='primary' class="mb-3 button-with" @click="changeForm(1)">
                    Вход
                  </b-button>
                  <b-button size='lg' variant='primary' class="button-with" @click="changeForm(2)">
                    Регистрация
                  </b-button>
                </div>
            </div>
          </div>
        </div>
        <div class="col-sm">
          <!--One of two columns-->
        </div>
        <div class="col-sm">
          <!--One of three columns-->
        </div>
      </div>
    </div>
    <div v-if="numberPage===1" class="container">
    <div class="row">
      <div class="col-sm" style="margin-top: 30vh">
        <form @submit.prevent="enterLk">
          <div class="form-group">
            <label for="exampleInputLogin">LOGIN</label>
            <input v-model="enterLogin" type="login" class="form-control" id="exampleInputLogin" aria-describedby="emailHelp" placeholder="Enter login">
            <!--<small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>-->
          </div>
          <div class="form-group">
            <label for="exampleInputPassword1">Password</label>
            <input v-model="enterPassword" type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
          </div>
          <div class="form-group form-check">
            <input type="checkbox" class="form-check-input" id="exampleCheck1">
            <label class="form-check-label" for="exampleCheck1">Check me out</label>
          </div>
          <button type="submit" class="mb-3 btn btn-primary">Submit</button>
          <div>
            <b-button size='lg' variant='primary' class="mb-3 button-with" @click="changeForm(null)">
            Назад
          </b-button>
          </div>
        </form>
        <!--One of three columns-->
      </div>
      <div class="col-sm">

      </div>
      <div class="col-sm">
        <!--One of three columns-->
      </div>
    </div>
    </div>
    <div v-if="numberPage===2" class="container">
        <div class="row">
          <div>
            <b-form @submit="onSubmit" @reset="onReset" v-if="show">
              <b-form-group id="exampleInputGroup1"
                            label="Email address:"
                            label-for="exampleInput1"
                            description="We'll never share your email with anyone else.">
                <b-form-input id="exampleInput1"
                              type="email"
                              v-model="form.email"
                              required
                              placeholder="Enter email">
                </b-form-input>
              </b-form-group>
              <b-form-group id="exampleInputGroup2"
                            label="Your Name:"
                            label-for="exampleInput2">
                <b-form-input id="exampleInput2"
                              type="text"
                              v-model="form.name"
                              required
                              placeholder="Enter name">
                </b-form-input>
              </b-form-group>
              <b-form-group id="exampleInputGroup3"
                            label="Food:"
                            label-for="exampleInput3">
                <b-form-select id="exampleInput3"
                               :options="foods"
                               required
                               v-model="form.food">
                </b-form-select>
              </b-form-group>
              <b-form-group id="exampleGroup4">
                <b-form-checkbox-group v-model="form.checked" id="exampleChecks">
                  <b-form-checkbox value="me">Check me out</b-form-checkbox>
                  <b-form-checkbox value="that">Check that out</b-form-checkbox>
                </b-form-checkbox-group>
              </b-form-group>
              <b-button class="mb-3" type="submit" variant="primary">Submit</b-button>
              <b-button class="mb-3" type="reset" variant="danger">Reset</b-button>
            </b-form>
            <b-button size='lg' variant='primary' class="mb-3 button-with" @click="changeForm(null)">
              Назад
            </b-button>
          </div>
        </div>
        <div class="col-sm">
          <!--<b-button size='lg' variant='primary' class="mb-3 button-with" @click="changeForm(null)">-->
            <!--Назад-->
          <!--</b-button>-->
          <!--One of two columns-->
        </div>
        <div class="col-sm">
        <!--One of three columns-->
        </div>
    </div>
        <!--<div class="row">-->
          <!--<div class="col-sm" style="margin-top: 30vh">-->
            <!--<form @submit.prevent="enterLk">-->
              <!--<div class="form-group">-->
                <!--<label for="exampleInputEmail12">Email address</label>-->
                <!--<input type="email" class="form-control" id="exampleInputEmail12" aria-describedby="emailHelp" placeholder="Enter email">-->
                <!--<small id="emailHelp2" class="form-text text-muted">We'll never share your email with anyone else.</small>-->
              <!--</div>-->
              <!--<div class="form-group">-->
                <!--<label for="exampleInputPassword12">Password</label>-->
                <!--<input type="password" class="form-control" id="exampleInputPassword12" placeholder="Password">-->
              <!--</div>-->
              <!--<div class="form-group form-check">-->
                <!--<input type="checkbox" class="form-check-input" id="exampleCheck12">-->
                <!--<label class="form-check-label" for="exampleCheck12">Check me out</label>-->
              <!--</div>-->
              <!--<button type="submit" class="btn btn-primary">Submit</button>-->
            <!--</form>-->
            <!--&lt;!&ndash;One of three columns&ndash;&gt;-->
          <!--</div>-->
          <!--<div class="col-sm">-->

          <!--</div>-->
          <!--<div class="col-sm">-->
            <!--&lt;!&ndash;One of three columns&ndash;&gt;-->
          <!--</div>-->
        <!--</div>-->
  </div>
</template>

<script>
export default {
  name: 'mainPage',
  data: function () {
    return {
      msg: 'Welcome to Your Vue.js App',
      numberPage: null,
      form: {
        email: '',
        name: '',
        food: null,
        checked: []
      },
      foods: [
        { text: 'Select One', value: null },
        'Carrots', 'Beans', 'Tomatoes', 'Corn'
      ],
      show: true,
      enterLogin: '',
      enterPassword: ''
    }
  },

  methods: {
    enterLk () {
      // this.$router.push({name: 'lk'})
      // console.log(this.enterLogin)
      this.$http.post('http://localhost:3100/users', {
        login: this.enterLogin,
        password: this.enterPassword
      })
        .then(response => {
          if (response.status === 200) {
            this.numberPage = 3
            this.$router.push({name: 'lk'})
          }
        })
        .catch(error => {
          console.log(error)
        })
    },
    changeForm (formNumber) {
      // this.$router.push({name: 'mainPage'})
      this.numberPage = formNumber
    },
    onSubmit (evt) {
      evt.preventDefault()
      alert(JSON.stringify(this.form))
    },
    onReset (evt) {
      evt.preventDefault()
      /* Reset our form values */
      this.form.email = ''
      this.form.name = ''
      this.form.food = null
      this.form.checked = []
      /* Trick to reset/clear native browser form validation state */
      this.show = false
      this.$nextTick(() => { this.show = true })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
  /*#42b983;*/
  /*background-image: image();*/
}
.paper {
  background-image: url("../assets/skorohod_main.jpg"); height: 100vh; background-size: cover;
  /*image('../assets/skorohod_main.jpg')*/
}
.button-with {
  width: 150px;
}
/*{ image src (./); }*/
  /*}*/
</style>
