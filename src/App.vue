<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :permanent="$vuetify.breakpoint.mdAndUp"
      bottom
      app
      mini-variant-width="90"
      :mini-variant.sync="hidemenu"
      @mousemove.native="hidemenu = false"
      @mouseleave.native=" hidemenu = (scrlpoint && $vuetify.breakpoint.mdAndUp)"
      style="background:linear-gradient(#fff calc(0% + 400px), #1565C0 calc(100% - 165px));"
    >
      <v-card flat v-if="$vuetify.breakpoint.mdAndUp">
        <v-card-text v-if="!hidemenu" class="text-h4 text-no-wrap black--text">Arun Mistry</v-card-text>
        <v-card-text v-if="hidemenu" class="text-h4 black--text">AM</v-card-text>
      </v-card>
      <v-divider />
      <v-list nav id="menu">
        <v-list-item
          v-for="item in menu"
          :key="item.icon"
          @click.stop="$vuetify.goTo('#'+item.id), drawer=false"
        >
          <v-list-item-icon>
            <v-icon :class="hidemenu?'':'ml-3'">mdi-{{item.icon}}</v-icon>
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
      @click.stop="drawer=true, hidemenu=false"
    >
      <v-icon>mdi-menu</v-icon>
    </v-btn>
    <v-main>
      <Home />
    </v-main>
  </v-app>
</template>

<script>
import Home from "./views/Home";
export default {
  name: "App",
  components: { Home },
  data() {
    return {
      drawer: false,
      scrlpoint: 0,
      x: 0,
      hidemenu: false,
      menu: [
        { icon: "star", name: "Highlights", id: "Highlights" },
        { icon: "account", name: "About Me", id: "About" },
        { icon: "school", name: "Experience", id: "Experience" },
        { icon: "briefcase", name: "Projects", id: "Projects" },
        { icon: "phone", name: "Contact Me", id: "Contact" },
      ],
    };
  },
  methods: {
    updateScroll() {
      this.scrlpoint = window.scrollY > 75;
      this.hidemenu = window.scrollY > 75 && this.x > 90 && this.$vuetify.breakpoint.mdAndUp;
    },
    updateX(e) {
      this.x = e.clientX;
    },
  },
  mounted() {
    // Starts updateScroll method
    window.addEventListener("scroll", this.updateScroll);
    // Get X-coordinate when in menu
    document.getElementById("menu").addEventListener("mousemove", this.updateX);
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

