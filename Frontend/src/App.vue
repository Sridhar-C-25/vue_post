<template>

  <div id="nav">
    <nav class="navbar navbar-expand-lg navbar-light bg-dark">
  <div class="container">
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
       
        <li class="nav-item">
    <router-link to="/" class="nav-link">Home</router-link> 

        
        </li>
        <li class="nav-item">
    <router-link to="/about" class="nav-link">About</router-link>

        </li>
      </ul>
    </div>
  </div>
</nav>
  </div>
  <router-view/>
</template>

<style>
*{
  margin:0;
  padding:0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #fff;
  background: #000;
  min-height: 100vh;
  padding-bottom: 5%;
}



#nav a {
  font-weight: bold;
  color: aliceblue;
}


#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
