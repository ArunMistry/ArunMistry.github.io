<template>
  <v-footer dark padless style="border-left: thin solid rgba(100,150,255,.85)" id="Contact">
    <v-card tile color="#1565C0" class="text-center" width="100%">
      <v-card-text>
        <v-btn
          v-for="item in footer"
          :key="item.icon"
          class="mx-3 mx-sm-5"
          icon
          :href="item.link"
          target="_blank"
        >
          <v-icon size="24px">mdi-{{ item.icon }}</v-icon>
        </v-btn>
      </v-card-text>
      <v-card-text
        class="white--text pt-0"
      >Thank you for checking out my website. Feel free to contact me or connect with me through any of the following mediums!</v-card-text>
      <v-divider />
      <v-card-text class="white--text">
        <v-icon class="mr-2">mdi-copyright</v-icon>
        {{ new Date().getFullYear() }} — Arun Mistry
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
export default {
  data() {
    return {      footer: [
        { icon: "linkedin", link: "https://www.linkedin.com/in/arun-mistry/" },
        { icon: "instagram", link: "https://www.instagram.com/arunmistry79/" },
        { icon: "gmail", link: "mailto:mistra11@mcmaster.ca" },
        { icon: "facebook", link: "https://www.fb.me/arunmistry92" },
        { icon: "github", link: "https://github.com/ArunMistry" },
      ],};
  },
};
</script>
