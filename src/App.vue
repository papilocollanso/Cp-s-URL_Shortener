<template>
  <div  id="app">
    <div id="nav">
    <div class="pix">
      
          <h1>   <span id="down"><img src="../src/Images/url1.png" width="60px" height="70px" alt=""/></span>&nbsp;Cp's</h1>
      <h2  id="link"><router-link  to="/">URL Shortener</router-link></h2>
    </div>

     
      
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">


#link{

  text-align: center;
}
h1{
  text-align: center;
}
.pix{
  text-align: start;
  margin-left: 10px;
  margin-top: 10px;

}
#app {
  
  font-family: Georgia, 'Times New Roman', Times, serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

}


#nav {

  text-align: center;
  font-size: 30px;

  a {
    font-weight: bold;
    color: #000;

  
  }
}
</style>
