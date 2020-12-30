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
          <v-carousel
            vertical
            :show-arrows-on-hover="$vuetify.breakpoint.mdAndUp"
            cycle
            interval="2500"
          >
            <v-carousel-item
              v-for="project in group.items"
              :key="project.name"
              :src="require('../assets/'+project.pic+'.jpg')"
            >
              <v-card
                height="100%"
                color="rgba(0,0,0,0.2)"
                class="d-flex flex-column align-center justify-center"
              >
                <span class="text-h2 font-weight-medium text-center px-10">{{project.name}}</span>
                <span class="text-subtitle-1 text-center px-10 mt-2">{{project.desc}}</span>
                <v-btn
                  v-if="project.name==='Scheduler'"
                  class="mt-3 blue darken-1"
                  @click="opendialog(project)"
                >Open Scheduler</v-btn>
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
              name: "Scheduler",
              desc: "Select ranges of dates and times",
              pic: "Scheduler",
            },
            {
              name: "Gear Train",
              desc: "Complex system of worm, axial and spur gears",
              pic: "GearTrain",
            },

            {
              name: "Carbocycle",
              desc: "Sustainability Hackathon, placed 1st",
              pic: "Carbocycle",
            },
            {
              name: "Mine Shaft",
              desc: "Innovative mineshaft cage design, Hackathon",
              pic: "MineShaft",
            },
            {
              name: "Super Desk",
              desc: "Concept for isolated studying in public spaces",
              pic: "SuperDesk",
            },
            {
              name: "Mini MacEng Comp",
              desc: "Vehicle to move without help, placed 1st",
              pic: "MacComp",
            },
            {
              name: "Writing tool",
              desc: "Designed for generalised dystonia",
              pic: "WritingTool",
            },
          ],
        },
        {
          title: "Personal",
          items: [
            {
              name: "My Website !!!",
              desc: "You're looking at it",
              pic: "Website",
            },
            {
              name: "OTF Blade",
              desc: "Inspired by AC, my take",
              pic: "Carbocycle",
            },
            {
              name: "Model Dinosaur",
              desc: "A showcase piece",
              pic: "Dino",
            },
            { name: "Model Gun", desc: "Inspired by AC4", pic: "Carbocycle" },
            {
              name: "Paper Crafts",
              desc: "From 'Canon Creative Park'",
              pic: "Carbocycle",
            },
            {
              name: "3D Printed Things",
              desc: "Learnt to use 3D printer efficiently, models found online",
              pic: "3Dmodels",
            },
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