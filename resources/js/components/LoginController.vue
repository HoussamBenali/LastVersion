<template>
<body>
<div id="LoginForm">
    <div class="container0">
<<<<<<< HEAD
      <form class="form" @submit.prevent="login">
=======
      <form @submit.prevent="login" class="form">
>>>>>>> 889a5aeb852ccad9a961e7a68021eb3e9da9135a
          <div v-if="credentials.length > 0" class="alert alert-warning" role="alert">
              {{credentials}}
          </div>
          <h2><b>Login</b></h2>
          <hr>

          <div class="form-group">
              <label for="email"><b>Email:</b></label>
              <input type="text" class="form-control" v-model="form.email" placeholder="Enter Email" name="email" id="email" required>
          </div>

          <div class="form-group">
              <label for="password"><b>Password:</b></label>
              <input type="password" class="form-control" v-model="form.password" placeholder="Enter Password" name="password" id="password" required>
          </div>

          <button class="mybtn" type="submit">Login</button>
      
          <div class="container">
              <label class="psw">
                  <span> Forgot your pasword?<router-link to="forgot"> Click here</router-link></span>
              </label>
          </div>
      </form>
    </div>
    <div class="newUser">
          <p>New here? Register for free now!</p>
          <router-link to="register" class="goRegister">Create an account</router-link>
        </div>
    </div>
</body>
</template>

<script>
import axios from 'axios'
axios.defaults.withCredentials = true
export default {

    data: () => ({
        form: {
            email:"",
            password:"",
        },
        credentials: ""
    }),
    computed:{
        user_pokes: function () {
            console.log(decksStore.state.pokes,"USERS POKES")
            return decksStore.state.pokes
        },
    },
    methods: {
        async login () {
            try{
              console.log(this.form.email)
              await this.$store.dispatch('login',this.form)
              const res = await axios.post('login',{
                email: this.email,
                password: this.password,
            })
              this.$awn.success("Bienvenido")
              console.log(res.data.pokemons)
              if (res.data.pokemons == null){
                return this.$router.push('starting');
              } else{
                 this.$store.dispatch('getDecks')
                  return this.$router.go('home');
              }

            }catch{
                this.$awn.warning("Credenciales invalidas")
                this.credentials="Credenciales invalidas"
            }
        }
    },
    mounted(){
      this.$store.dispatch('showDeck')
      this.$store.dispatch('showPokes')
    }
}
</script>
<style lang="scss">
    @import '~vue-awesome-notifications/dist/styles/style.scss';

</style>
<style scoped>

    /* // @import "../../css/styles.css"; */


    #LoginForm{
    background-color: #f6f7c7;
    background-image: url(https://assets.pokemon.com/assets/cms2/img/pokedex/full/150.png),url(https://assets.pokemon.com/assets/cms2/img/pokedex/full/151.png);
    background-repeat: no-repeat;
    background-position-x: left ,  right;
    display: block;
    width: 100%;
    overflow: auto;
    height:fit-content;
    text-align: center;
    
    
  }

  .alert{
    margin-top:2vh;
  }
  
  .newUser{
    border:solid 3px black;
    border-radius: 1vh;
    min-width: 300px;
    padding: 2vh;
    margin-top: 1vh;
    width: 37%;
    background-color: white;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 2vh;
  }
  
  .goRegister{
    border-radius: 1vh;
    background-color: #4CAF50;
    padding: 1.5vh;
    color: white;
    display: block;
    margin-top: 2vh;
    margin-left: auto;
    margin-right: auto;
  }
  
  .goRegister:hover{
    text-decoration: none;
    opacity: 0.8;
    color: white;
  }
  
  .check{
    display: block;
    margin-top: 2vh;
    margin-bottom: 2vh;
  }
  
  h2{
    margin-top:2vh;
  }
  
  .psw{
    padding: 12.5px;
    padding-bottom: 5px;
  }
  
  .container0{
    margin-top: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
  }
  
  .container{
    min-width: 250px;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color:#f1f1f1;
    position: relative;
    top:5px;
   
  }
  
  button {
    background-color: #4CAF50;
    border-radius: 1vh;
    color: white;
    padding: 1.5vh;
    margin: 8px 0;
    border: none;
    cursor: pointer;
    width: 100%;
  }
  
  button:hover {
    opacity: 0.8;
  }
  
  .mybtn{
    margin-bottom: 0;
  }
  
</style>