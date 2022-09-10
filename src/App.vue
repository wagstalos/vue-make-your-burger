<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <router-view />
  <Footer />
</template>

<script>
import Navbar from './components/Navbar.vue';
import Footer from './components/Footer.vue';

export default {
  components: {
    Navbar,
    Footer
  },
  data() {
    return {
      logo_src: "/img/logo.png",
      app_name: "Make yout burguer"
    }
  }
}
</script>

<style>
* {
  font-family: Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;

  font-family: 'Lato', sans-serif;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}

h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  font-family: 'Anton', sans-serif;
}

h2 {
  text-align: center;
}

.underline {
  content: '';
  width: 80px;
  height: 2px;
  background-color: #FCBA03;
  margin: 20px auto;

}
</style>
