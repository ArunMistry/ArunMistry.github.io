<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :permanent="$vuetify.breakpoint.mdAndUp"
      bottom
      app
      mini-variant-width="90"
      :mini-variant.sync="hidesidemenu"
      @mouseover.native="scrlpoint ? (hidesidemenu = false) : ''"
      @mouseleave.native="scrlpoint ? (hidesidemenu = true) : ''"
      style="background:linear-gradient(#fff calc(0% + 475px), #1565C0 calc(100% - 165px));"
    >
      <v-card flat v-if="$vuetify.breakpoint.mdAndUp">
        <v-card-text v-if="!hidesidemenu" class="text-h4 text-no-wrap black--text">Arun Mistry</v-card-text>
        <v-card-text v-if="hidesidemenu" class="text-h4 black--text">AM</v-card-text>
      </v-card>
      <v-divider/>
      <v-list nav v-for="item in menu" :key="item.icon">
        <v-list-item link @click.stop="$vuetify.goTo('#'+item.id)">
          <v-list-item-icon>
            <v-icon :class="hidesidemenu?'':'ml-3'">mdi-{{item.icon}}</v-icon>
          </v-list-item-icon>
          <v-list-item-title>{{item.name}}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-btn
      v-if="$vuetify.breakpoint.smAndDown"
      dark
      color="red darken-3"
      fab
      fixed
      bottom
      right
      @click="drawer=!drawer"
    >
      <v-icon>mdi-menu</v-icon>
    </v-btn>
    <v-main>
      <Home />
    </v-main>
  </v-app>
</template>

<script>
import Home from "./views/Home"
export default {
  name: "App",

  components: {Home},

  data() {
    return {
      drawer: false,
      scrlpoint: false,
      hidesidemenu: false,
      menu: [
        { icon: "star", name: "Highlights", id:"Highlights" },
        { icon: "account", name: "About Me", id:"About" },
        { icon: "school", name: "Experience", id:"Experience" },
        { icon: "briefcase", name: "Projects", id:"Projects" },
        { icon: "phone", name: "Contact Me", id:"Contact" },
      ],
    };
  },
  methods: {
    // updateScroll checks how far page is scrolled, and changes scrlpoint value accordingly
    updateScroll() {
      window.scrollY >= 50
        ? ((this.scrlpoint = true), (this.hidesidemenu = true))
        : ((this.scrlpoint = false), (this.hidesidemenu = false));
    },
  },
  watch: {
    $route: {
      immediate: true,
      handler(to) {
        document.title = to.meta.title || "Arun Mistry";
      },
    },
  },
  mounted() {
    // Starts updateScroll method
    window.addEventListener("scroll", this.updateScroll);
  },
};
</script>

<style>
theme--light.v-navigation-drawer:not(.v-navigation-drawer--floating)
  .v-navigation-drawer__border {
  background-color: rgba(0, 0, 0, 0) !important;
}
.theme--light.v-navigation-drawer:not(.v-navigation-drawer--floating)
  .v-navigation-drawer__border {
  background-color: rgba(0, 0, 0, 0) !important;
}
</style>