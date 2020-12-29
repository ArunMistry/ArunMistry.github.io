/* eslint-disable */
<template>
  <v-container fluid pa-0>
    <v-row no-gutters id="Highlights">
      <v-col cols="12" md="7" lg="8" xl="9">
        <v-card
          tile
          outlined
          height="100%"
          min-height="90vh"
          class="text-center d-flex flex-column"
        >
          <v-sheet class="text-h2 font-weight-bold pt-10 pb-3">Arun Mistry</v-sheet>
          <v-sheet class="text-h6 font-weight-medium mb-5">Welcome to my website</v-sheet>
          <v-sheet width="100%" class="d-flex flex-grow-1 align-end justify-center">
            <v-img :src="require(`../assets/TotallyMe.jpg`)" max-height="70vh" contain />
          </v-sheet>
        </v-card>
      </v-col>
      <v-col cols="12" md="5" lg="4" xl="3">
        <v-card tile outlined height="100%" class="d-flex flex-column">
          <v-card flat class="pa-5 pa-md-8 text-h3 font-weight-medium">Highlights</v-card>
          <v-divider />
          <!-- Change to rows and columns for sm -->
          <v-card flat class="pa-5 pa-md-8 flex-grow-1 text-no-wrap">
            <h2>Education</h2>
            <ul>
              <li>
                McMaster Univeristy
                <ul>
                  <li>Expected Graduation: 2023</li>
                  <li>Mechatronics Engineering II</li>
                </ul>
              </li>
              <li>GPA 11.8/12</li>
            </ul>
            <br />
            <h2>Skillset</h2>
            <ul>
              <li>Front-End Developer</li>
              <li>Fluent in Vue.JS, HTML, CSS and C</li>
              <li>Experienced with Vuetify Framework</li>
              <li>Familiar with Python, JavaScript</li>
            </ul>
            <br />
            <h2>Experience</h2>
            <ul>
              <li>
                Summer 2020 Coop, FyeLabs
                <ul>
                  <li>FrontEnd Development</li>
                </ul>
              </li>
              <li>Coded 2020-21 sumobot.ca</li>
            </ul>
            <v-btn x-large dark class="red darken-4 my-5 mx-2">Resume</v-btn>
          </v-card>
        </v-card>
      </v-col>
      <v-card tile outlined width="100%">
        <v-sheet class="arrows" />
      </v-card>
      <v-col cols="12" md="5" id="About">
        <v-card tile outlined height="100%" class="pa-5 px-md-10 d-flex align-center">
          <span class="text-md-h1 text-h3 font-weight-medium">
            About
            <br v-if="$vuetify.breakpoint.mdAndUp" />Me
          </span>
        </v-card>
      </v-col>
      <v-col cols="12" md="7">
        <v-card
          :min-height="$vuetify.breakpoint.mdAndUp ?'65vh':''"
          tile
          outlined
          class="pa-7 pa-md-10 text-justify d-flex align-center text-body-1 font-weight-regular"
        >
          <span>
            <p>Hi, my name is Arun Mistry, and I am a Mechatronics Engineering II Student in McMaster Univeristy. I am in my second year, and plan on graduating in 2023-24. My ambition is to work in the field of robotics. Robotics involves building, coding, debugging, problem solving, and a lot more, all of which I find very interesting.</p>
            <p>Some of my hobbies include cooking, coding, going for long walks, playing games on my PC and tinkering around with my phone's software (Pocophone F1). Some of my favourite memories during university were during various events. Meeting new people, learning new things and being in different scenarios in different environments was always interesting.</p>
            <p
              class="ma-0"
            >I thank you for taking the time to check my website out. Please feel free to connect with me or contact me at any time. My contact details are at the bottom of the website.</p>
          </span>
        </v-card>
      </v-col>
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
                          <v-card-text
                            class="white pt-3 text-justify"
                          >Proficient in using Vue.JS, HTML, CSS and Bootstrap and Vuetify Material UI frameworks to build frontends. Responsible for coding over 90% of the pages for a mock dashboard. Built various interactive elements such as an email scheduler (Check Projects underneath). Gained familiarity with Golang (coded a few files for dashboard backend), Docker and GitHub.</v-card-text>
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
                  <v-card-text style="max-height:50vh;overflow-y:scroll">
                    <v-timeline :dense="$vuetify.breakpoint.mdAndDown">
                      <v-timeline-item v-for="event in item.events" :key="event.title">
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
    <Projects />
    <v-card tile outlined width="100%">
      <v-sheet class="arrows" style="transform: rotate(180deg);" />
    </v-card>
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
  </v-container>
</template>

<script>
import Projects from "./Projects";
export default {
  components: { Projects },
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
              name: "Engineering Computation",
              date: "Fall 2019",
              brief: "Learnt to program in Python.",
            },
          ],
        },
      ],
      footer: [
        { icon: "linkedin", link: "https://www.linkedin.com/in/arun-mistry/" },
        { icon: "instagram", link: "https://www.instagram.com/arunmistry79/" },
        { icon: "gmail", link: "mailto:mistra11@mcmaster.ca" },
        { icon: "facebook", link: "https://www.fb.me/arunmistry92" },
        { icon: "github", link: "https://github.com/ArunMistry" },
      ],
    };
  },
};
</script>

<style scoped>
.arrows {
  position: relative;
  margin: 0 20px;
  height: 10vh;
  background-image: url("../assets/arrowgroup.png");
  background-size: contain;
  background-repeat: repeat-x;
}
</style>