<template>
  <v-app>
    <v-content>
      <Navbar/>
      <router-view></router-view>
      <Footer/>
    </v-content>
  </v-app>
    
</template>

<script>

import Navbar from './components/Navbar.vue';
import Footer from './components/Footer.vue';


export default {
  name: 'App',
    components: { Navbar, Footer},
    data: () => ({
    //
  })
};
</script>


<style >
 * {
  font-family:Arial, Helvetica, sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  text-align: center; 
   
 
}
 .main-container{
  margin: 50px;
  min-height: 250px;
   
}
</style>