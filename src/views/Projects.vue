<template>
  <v-container fluid pa-0>
    <v-row no-gutters id="Projects" v-for="group in projects" :key="group.title">
      <v-col cols="12" md="6">
        <v-card
          tile
          outlined
          height="100%"
          class="pa-5 px-md-10 d-flex align-center text-truncate"
          :class="group.title === 'Work'?'justify-md-end text-md-right':''"
        >
          <span class="text-h3 text-md-h1 font-weight-medium mx-lg-5">
            {{group.title}}
            <br v-if="$vuetify.breakpoint.mdAndUp" />Projects
          </span>
        </v-card>
      </v-col>
      <v-col cols="12" md="6" :order-md="group.title === 'Personal'?'last':'first'">
        <v-card tile outlined>
          <v-carousel vertical :show-arrows-on-hover="$vuetify.breakpoint.mdAndUp">
            <v-carousel-item
              v-for="project in group.items"
              :key="project.name"
              :src="'https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg'"
            >
              <v-card
                height="100%"
                color="rgba(0,0,0,.3)"
                class="d-flex flex-column align-center justify-center"
              >
                <span class="text-h2 font-weight-medium text-center px-10">{{project.name}}</span>
                <span class="text-subtitle-1 text-center px-10 mt-2 mb-5">{{project.desc}}</span>
                <v-btn color="blue" @click="opendialog(project)">Read More</v-btn>
              </v-card>
            </v-carousel-item>
          </v-carousel>
        </v-card>
      </v-col>
    </v-row>
    <v-dialog v-model="dialog" scrollable max-width="900px">
      <v-card>
        <v-card-title class="text-h3">
          {{dialoginfo.name}}
          <v-btn icon class="ml-auto" @click="dialog=false">
            <v-icon large>mdi-close</v-icon>
          </v-btn>
        </v-card-title>
        <v-divider />
        <v-card-text class="pa-5">{{dialoginfo.desc}}</v-card-text>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      dialoginfo: {
        name: "",
        desc: "",
      },
      projects: [
        {
          title: "Work",
          items: [
            {
              name: "Gear Train",
              desc: "Complex system for prosthetic joints",
            },
            { name: "Scheduler", desc: "Feature-rich email scheduler" },
            {
              name: "Carbocycle",
              desc: "Sustainability Hackathon, placed 1st",
            },
            {
              name: "Mine Shaft",
              desc: "Innovative mineshaft design, Hackathon",
            },
            { name: "Speaker", desc: "Lab project, unique speaker design" },
          ],
        },
        {
          title: "Personal",
          items: [
            { name: "My Website !!!", desc: "You're looking at it" },
            { name: "OTF Blade", desc: "Inspired by AC, my take" },
            { name: "Model Dinosaur", desc: "A showcase piece" },
            { name: "Ornithopter", desc: "Flew with semi-success" },
            { name: "Model Gun", desc: "Inspired by AC4" },
          ],
        },
      ],
    };
  },
  methods: {
    opendialog(project) {
      this.dialoginfo = project;
      this.dialog = true;
    },
  },
};
</script>

<style>
</style>