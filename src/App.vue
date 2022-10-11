<template>
  <div id="app" class="fondo">
    <b-navbar toggleable="md" type="dark" variant="success">
      <b-container>
        
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        
        <b-navbar-brand href="#"> 
          <img src="./assets/logo_gs.png" class="img-navbar rounded-circle">
        </b-navbar-brand>

        <b-collapse  id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item :to="{name: 'home'}" exact>Home</b-nav-item>
            <b-nav-item :to="{name: 'login'}">Login</b-nav-item>
            
          </b-navbar-nav>

        </b-collapse>

      </b-container>
    
    </b-navbar>
    
    <router-view/>
      

  </div>
</template>



<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
.fondo{
  background-image: url(./assets/logoBG2.svg);
  background-repeat: no-repeat;
  background-attachment: scroll;
  background-position: center;
  background-size: cover;
}
.img-navbar{
  height: 50px;
  
}


</style>
