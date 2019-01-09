<template>
  <div id="app">
    <!-- <div class="nav">
      <router-link to="/">spacer</router-link>
      <router-link to="/about">spacer</router-link>
      <router-link to="/search">Search</router-link>
    </div> -->
    <router-view />
  </div> 
  
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Montserrat:400,600,800');
  *{
    box-sizing: border-box;
  }

  body{
    font-family: 'Montserrat', sans-serif;
    margin: 0;
    padding: 0;
  }
</style>
