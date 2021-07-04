<template>
  <v-app>
    <v-app-bar app color="primary" dark>     
       <h2>E-commerce Portal</h2>
      <v-spacer></v-spacer> 
      <v-btn text href="#home">Home</v-btn>
      <v-btn text href="#login">Login</v-btn>    
    </v-app-bar>

    <v-main>
      <template>
        <HomeCom/>
      </template>
      
    </v-main>
  </v-app>
  
</template>

<script>
// import Login from "./components/Login";
import HomeCom from "./views/Home.vue";

export default {
  name: "App",

  components: {
    HomeCom
  }
};
</script>
