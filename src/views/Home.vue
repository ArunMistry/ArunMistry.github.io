<template>
  <v-container fluid pa-0>
    <Highlights/>
    <About />
    <Experience />
    <Projects />
    <Footer />
  </v-container>
</template>

<script>
import Projects from "./Projects";
import Experience from "./Experience";
import Footer from "./Footer";
import About from "./About.vue";
import Highlights from './Highlights.vue';
export default {
  components: { Projects, Experience, About, Footer, Highlights },
};
</script>