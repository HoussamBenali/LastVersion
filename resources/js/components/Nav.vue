<template>
<div class="header">
<nav class="navbar navbar-icon-top navbar-expand-lg navbar-dark bg-dark">
  <img class="hi" alt="Pokelogo" src="/images/pokelogo.png" width="60" height="60">
  <a class="navbar-brand" href="#"><b>PokeCards</b></a>

  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav ml-auto"  v-if="$store.state.auth">
      <li class="nav-item ">
          <router-link to="/home" active-class="active" class="nav-link">
            <i class="fa fa-home"></i>
              Home
            <span class="sr-only">(current)</span>
          </router-link>
      </li>
      <li class="nav-item">
          <router-link to="/adventure" active-class="active" class="nav-link">
            <i class="fa fa-dungeon"></i>
             Adventure
            <span class="sr-only">(current)</span>
          </router-link>
      </li>
      <li class="nav-item">
         
          <router-link to="/decks" active-class="active" class="nav-link">
          <i class="fa fa-book"></i>
              Decks
          </router-link>
      </li>

        <li class="nav-item">
        <router-link to="/shop" active-class="active" class="nav-link" >
           <i class="fa fa-shopping-cart fa-stack" :data-count="pokemons_cart" ></i>
              Shop   
        </router-link>
      </li>

      <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          <span class="span nav-link"> 
          <img :src="'/api/getAvatar'"  class="fa img">
          {{$store.state.user.nick}}
          </span>
        </a>
        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <router-link to="/changeAvatar" class="dropdown-item ">Change Avatar</router-link>
            <router-link class="dropdown-item " to="/changeProfile" >Change Profile</router-link>
            <router-link class="dropdown-item " to="/changePass" >Change Password</router-link>
            <router-link to="/myshops" active-class="active" class="dropdown-item ">Shopping Records</router-link>
            <router-link to="/myGamesOff" active-class="active" class="dropdown-item ">Adventure Records</router-link>
          <div class="dropdown-divider"></div>
           <a @click="Logout"  active-class="active" class="dropdown-item">Logout</a>
        </div>
      </li>

        <li class="nav-item">
        <router-link to="#" active-class="active" class="nav-link" >
           <i class="fa fa-ruble-sign"> </i>   
            {{this.$store.state.user.coins}}
        </router-link>
      </li>

    </ul>

    <ul class="navbar-nav ml-auto" v-else>
      <li class="nav-item">
        <router-link to="/login" active-class="active" class="nav-link ">
          Login
        </router-link>
      </li>
      <li class="nav-item">
        <router-link to="/register" active-class="active" class="nav-link ">
          Register
        </router-link>
      </li>
    </ul>
  </div>
</nav>

</div>
</template>

<script>
import cart from '../store/index'
// import user from '../store/store'
export default {
  
  name: 'navigator',
  methods:{
    async Logout(){
        localStorage.removeItem("who")
        await this.$store.dispatch("logout")
        return this.$router.push('login')
    }
    
  },
  computed:{
    pokemons_cart: function () {

        return cart.state.pokemons_cart.length
    },
  },
  mounted () {

    cart.dispatch('fetcCart')

    
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.dropdown-menu{
  margin:0;
  padding:4px;
  padding-left: 2px;
  padding-right: 2px;
  font-size: 0.8rem;
}

$shopping-cart-red: #ce4217;

.fa-stack[data-count]:after{
  position:absolute;
  right:0%;
  top:0%;
  content: attr(data-count);
  font-size:40%;
  padding:.6em;
  border-radius:999px;
  line-height:.4em;
  color: white;
  color:$shopping-cart-red;
  text-align:center;
  max-width:2em;
  background: white;
  border-style:solid;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}

.fa-stack{
 height: 27px!important;
 margin: 0 !important; padding:0!important
}


.img{
  max-width: 30px; max-height: 30px; min-width: 30px; min-height: 30px; border-radius: 50%;
  margin-right:6px;
}

.navbar-icon-top .navbar-nav .nav-link > .fa {
  position: relative;
  width: 36px;
  font-size: 24px;
}

.navbar-icon-top .navbar-nav .nav-link > .fa > .badge {
  font-size: 0.75rem;
  position: absolute;
  right: 0;
  font-family: sans-serif;
}

.navbar-icon-top .navbar-nav .nav-link > .fa {
  top: 3px;
  line-height: 12px;
}

.navbar-icon-top .navbar-nav .nav-link > .fa > .badge {
  top: -10px;
}

@media (min-width: 576px) {
  .navbar-icon-top.navbar-expand-sm .navbar-nav .nav-link {
    text-align: center;
    display: table-cell;
    height: 70px;
    vertical-align: middle;
    padding-top: 0;
    padding-bottom: 0;
  }

  .navbar-icon-top.navbar-expand-sm .navbar-nav .nav-link > .fa {
    display: block;
    width: 48px;
    margin: 2px auto 4px auto;
    top: 0;
    line-height: 24px;
  }

  .navbar-icon-top.navbar-expand-sm .navbar-nav .nav-link > .fa > .badge {
    top: -7px;
  }
}

@media (min-width: 768px) {
  .navbar-icon-top.navbar-expand-md .navbar-nav .nav-link {
    text-align: center;
    display: table-cell;
    height: 70px;
    vertical-align: middle;
    padding-top: 0;
    padding-bottom: 0;
  }

  .navbar-icon-top.navbar-expand-md .navbar-nav .nav-link > .fa {
    display: block;
    width: 48px;
    margin: 2px auto 4px auto;
    top: 0;
    line-height: 24px;
  }

  .navbar-icon-top.navbar-expand-md .navbar-nav .nav-link > .fa > .badge {
    top: -7px;
  }
}

@media (min-width: 992px) {
  .navbar-icon-top.navbar-expand-lg .navbar-nav .nav-link {
    text-align: center;
    display: table-cell;
    height: 70px;
    vertical-align: middle;
    padding-top: 0;
    padding-bottom: 0;
  }

  .navbar-icon-top.navbar-expand-lg .navbar-nav .nav-link > .fa {
    display: block;
    width: 48px;
    margin: 2px auto 4px auto;
    top: 0;
    line-height: 24px;
  }

  .navbar-icon-top.navbar-expand-lg .navbar-nav .nav-link > .fa > .badge {
    top: -7px;
  }
}

@media (min-width: 1200px) {
  .navbar-icon-top.navbar-expand-xl .navbar-nav .nav-link {
    text-align: center;
    display: table-cell;
    height: 70px;
    vertical-align: middle;
    padding-top: 0;
    padding-bottom: 0;
  }

  .navbar-icon-top.navbar-expand-xl .navbar-nav .nav-link > .fa {
    display: block;
    width: 48px;
    margin: 2px auto 4px auto;
    top: 0;
    line-height: 24px;
  }

  .navbar-icon-top.navbar-expand-xl .navbar-nav .nav-link > .fa > .badge {
    top: -7px;
  }
}

</style>