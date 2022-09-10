<template>
  <div>
    <Banner />
    <div class="main-container">
      <h2>Monte o seu burger</h2>
      <div class="underline"></div>
      <BurguerForm />
    </div>
  </div>
</template>

<script>
import Banner from "../components/Banner.vue"
import BurguerForm from "../components/burguerForm.vue";

export default {
  name: "Home",
  components: {
    Banner,
    BurguerForm
  }
}

</script>
