<template>
  <v-app class="grey lighten-4">
    <Navbar />

    <v-content class="mx-4 mb-4">
      <v-avatar color="indigo">
      <v-icon dark>mdi-account-circle</v-icon>
    </v-avatar>
      <router-view></router-view>
    </v-content>
    <Footer />
  </v-app>
</template>

<script>
import Navbar from "./components/Navbar";
import Footer from "./components/Footer";

export default {
  components: { Navbar, Footer },
  name: "App",
  data() {
    return {};
  }
};
</script>