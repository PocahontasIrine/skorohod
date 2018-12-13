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
        <div class="col-sm" style="margin-top: 40vh">
          <div>
          <button @click="vhod">Вход</button>
          </div>
          <div><br></div>
          <div>
          <button class="reg">Регистрация</button>
          </div>
          <!--One of three columns-->
        </div>
        <div class="col-sm">
        </div>
        <div class="col-sm">
          <!--One of three columns-->
        </div>
      </div>
    </div>
    <div v-if="numberPage===1" class="container">
      <div class="row">
        <div class="col-sm">
          <form @submit.prevent="enterLk">
            <div class="form-group">
              <label for="exampleInputEmail1">Email address</label>
              <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
              <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
            </div>
            <div class="form-group">
              <label for="exampleInputPassword1">Password</label>
              <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
            </div>
            <div class="form-group form-check">
              <input type="checkbox" class="form-check-input" id="exampleCheck1">
              <label class="form-check-label" for="exampleCheck1">Check me out</label>
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
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
  </div>
</template>

<script>
export default {
  name: 'mainPage',
  data: function () {
    return {
      msg: 'Welcome to Your Vue.js App',
      numberPage: null
    }
  },

  methods: {
    enterLk () {
      this.$router.push({name: 'lk'})
    },
    vhod () {
      this.$router.push({name: 'mainPage'})
      this.numberPage = 1
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
/*{ image src (./); }*/
  /*}*/
</style>
