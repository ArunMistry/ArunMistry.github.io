<template>
  <v-app>
    <v-navigation-drawer
      app
      :mini-variant="hidesidemenu"
      mini-variant-width="90"
      @mouseover.native="scrlpoint ? (hidesidemenu = false) : ''"
      @mouseleave.native="scrlpoint ? (hidesidemenu = true) : ''"
    >
      <v-list>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title v-if="!hidesidemenu" class="text-h4">Arun Mistry</v-list-item-title>
            <v-list-item-title v-if="hidesidemenu" class="text-h4">AM</v-list-item-title>
            <v-list-item-subtitle></v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-divider></v-divider>

      <v-list nav v-for="item in menu" :key="item.icon">
        <v-list-item link>
          <v-list-item-icon>
            <v-icon>mdi-{{item.icon}}</v-icon>
          </v-list-item-icon>
          <v-list-item-title>{{item.name}}</v-list-item-title>
        </v-list-item>

      </v-list>
    </v-navigation-drawer>
    <v-main>
      <router-view />
    </v-main>
    <v-footer
      app
      absolute
    >Thank you for checking out my website. Feel free to contact me through any of the following mediums!</v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data() {
    return {
      scrlpoint: false,
      hidesidemenu: false,
      menu: [
        { icon: "star", name: "Highlights" },
        { icon: "account", name: "About Me" },
        { icon: "school", name: "Experience" },
        { icon: "briefcase", name: "Projects" },
        { icon: "phone", name: "Contact Me" }
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
