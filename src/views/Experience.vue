<template>
  <v-row no-gutters>
    <v-col cols="12" id="Experience">
      <v-card tile outlined>
        <v-sheet class="text-md-h1 text-h3 font-weight-medium text-center py-8">Experience</v-sheet>
        <v-card tile flat class="px-2 px-md-7 pb-7">
          <v-row no-gutters>
            <v-col cols="12" md="9" class="mx-auto">
              <v-card shaped outlined class="elevation-5 mx-5 mb-5 mt-md-5">
                <v-card-title class="text-h5 font-weight-bold">Co-op</v-card-title>
                <v-divider />
                <v-card-text
                  :style="$vuetify.breakpoint.lgAndUp?'overflow-y:scroll;height:40vh':''"
                  class="pl-0"
                >
                  <v-timeline dense align-top>
                    <v-timeline-item>
                      <template v-slot:icon>
                        <v-avatar>
                          <v-img :src="require(`../assets/FyeLabs.jpg`)" />
                        </v-avatar>
                      </template>
                      <v-card elevation="10" color="#2050af">
                        <v-card-title class="white--text">
                          <span style="letter-spacing: 5px">
                            <span>FYE</span>
                            <span style="color:#fdbf57">LABS</span>
                          </span>
                          <span class="ml-auto">Summer 2020</span>
                        </v-card-title>
                        <v-card-text class="white pt-3 text-justify">
                          <ul>
                            <li>Gained experience in using Vue.JS, HTML, CSS and Bootstrap and Vuetify Material UI frameworks to build frontends.</li>
                            <li>Responsible for coding over 90% of the pages for a mock dashboard.</li>
                            <li>Built several frontends over the course of 12 weeks</li>
                            <li>Built various interactive elements such as a scheduler (Check Projects underneath) and a team planner.</li>
                            <li>Gained familiarity with Golang (coded a few files for dashboard backend), Docker and GitHub.</li>
                          </ul>
                        </v-card-text>
                      </v-card>
                    </v-timeline-item>
                  </v-timeline>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12" md="6" v-for="item in experience" :key="item.title">
              <v-card shaped outlined class="elevation-5 ma-5">
                <v-card-title class="text-h5 font-weight-medium">{{item.title}}</v-card-title>
                <v-divider />
                <v-card-text style="max-height:50vh;overflow-y:scroll" class="pl-0 pl-lg-5">
                  <v-timeline :dense="$vuetify.breakpoint.mdAndDown">
                    <v-timeline-item
                      v-for="event in item.events"
                      :key="event.title"
                      :color="colors[Math.floor(Math.random() * 8)]"
                    >
                      <span slot="opposite">{{event.date}}</span>
                      <v-card elevation="10">
                        <v-card-title
                          class
                          style="word-break:normal;line-height: 1.3;"
                        >{{event.name}}</v-card-title>
                        <v-card-subtitle class="hidden-lg-and-up">{{event.date}}</v-card-subtitle>
                        <v-divider />
                        <v-card-text class="pt-3 text-justify">{{event.brief}}</v-card-text>
                      </v-card>
                    </v-timeline-item>
                  </v-timeline>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-card>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      experience: [
        {
          title: "Events",
          events: [
            {
              name: "STREAMHacks Hackathon",
              date: "August 2020",
              brief:
                "Placed 1st with an innovative and creative idea. Designed an app to promote sustainable means of product purchase and disposing, along with a rewards system as an incentive.",
            },
            {
              name: "Technical Lead, Sumobot",
              date: "May 2020 to Present",
              brief:
                "Worked on redesigning the club website from ground-up, responsible for maintaining the website and keeping it updated.",
            },
            {
              name: "Volunteer, DeltaHacks VI",
              date: "January 2020",
              brief:
                "Coordinated with executive members to ensure the event operated smoothly. Undertook various jobs such as restocking and food distribution. Worked with Algorand to record videos of presentations.",
            },
            {
              name: "McMaster CAD Designathon, Hackathon",
              date: "January 2020",
              brief:
                "Designed and modelled a unique mine shaft and carriage with several safety features and quality of life improvements over existing mineshaft. Received a lot of positive feedback.",
            },
          ],
        },
        {
          title: "Important Courses",
          events: [
            {
              name: "Programming - 2MP3",
              date: "Fall 2020",
              brief:
                "Learnt to program in C, with recursions, pointers, file I/O, structs and more. Learnt basics on ARM Assembly.",
            },
            {
              name: "Engineering Design and Graphics - 1C03",
              date: "Fall 2020",
              brief:
                "Independently designed and modelled a very unique and complicated gear train for a prosthetic hand. Was praised for being able to build and demonstrate the gear train successfully without failure.",
            },
            {
              name: "Engineeering Profession and Practice - 1P03",
              date: "Fall 2019",
              brief:
                "Collaborated on building a writing tool to assist our client affected by generalised dystonia. Device consisted of a large flat surface with roller balls underneath, along with a spring hinged pen attachment to allow easy writing.",
            },
            {
              name: "Engineering Computation - 1D04",
              date: "Fall 2019",
              brief: "Learnt to program in Python.",
            },
          ],
        },
      ],
      colors: [
        "indigo",
        "red darken-2",
        "green darken-1",
        "purple",
        "yellow darken-3",
        "pink darken-1",
        "cyan",
        "brown",
      ],
    };
  },
};
</script>
