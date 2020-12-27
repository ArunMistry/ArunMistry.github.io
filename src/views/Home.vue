/* eslint-disable */
<template>
  <v-container fluid pa-0>
    <v-row no-gutters>
      <v-col cols="12" md="7" xl="8">
        <v-card tile outlined style="min-height:90vh;height:100%" class="text-center pt-10">
          <span class="text-h2 font-weight-bold">Arun Mistry</span>
          <h2>- Mechatronics Eng Student</h2>
          <h2>- Front End Developer</h2>
          <h4 class="font-weight-medium">Welcome to my website</h4>
          <v-img :src="require(`../assets/TotallyMe.jpg`)" max-height="60vh" width="100%" contain/>
        </v-card>
      </v-col>
      <v-col cols="12" md="5" xl="4">
        <v-card tile outlined height="100%">
          <v-card flat class="pa-5 pa-md-8 text-h3 font-weight-medium">Highlights</v-card>
          <v-divider />
          <v-card flat class="pa-5">
            <h2>Education</h2>
            <ul>
              <li>McMaster Univeristy, Expected Graduation: 2023</li>
              <li>Mechatronics Engineering II, Second Year Student</li>
              <li>GPA 11.8/12</li>
            </ul>
            <br />
            <h2>Skillset</h2>
            <ul>
              <li>Front-End Developer</li>
              <li>Fluent in Vue.JS, JavaScript, HTML, CSS</li>
              <li>Experienced with using Vuetify Framework</li>
              <li>Proficient in C</li>
              <li>Prior experience with Python</li>
            </ul>
            <br />
            <h2>Experience</h2>
            <ul>
              <li>Summer 2020 Coop, FyeLabs (FrontEnd Dev)</li>
              <li>Coded and built 2020-2021 sumobot.ca website</li>
            </ul>
            <v-btn x-large dark class="red darken-4 my-5 mx-2">Resume</v-btn>
          </v-card>
        </v-card>
      </v-col>
      <v-card tile outlined width="100%">
        <v-sheet
          height="100%"
          width="20"
          style="position:absolute;right:0px;z-index:1"
          color="white"
        />
        <v-sheet class="arrows" />
      </v-card>
      <v-col cols="12" md="5">
        <v-card tile outlined height="100%" class="pa-5 px-md-10 d-flex align-center">
          <span class="text-md-h1 text-h3 font-weight-medium">
            About
            <br v-if="$vuetify.breakpoint.mdAndUp" />Me
          </span>
        </v-card>
      </v-col>
      <v-col cols="12" md="7">
        <v-card tile outlined class="pa-7 pa-md-10 text-justify text-body-1 font-weight-regular">
          <p>Hi, my name is Arun Mistry, and I am a Mechatronics Engineering II Student in McMaster Univeristy. I am in my second year, and plan on graduating in 2023-24. My ambition is to work in the field of robotics. Robotics involves building, coding, debugging, problem solving, and a lot more, all of which I find very interesting.</p>
          <p>Some of my hobbies include cooking, coding, going for long walks, playing games on my PC and tinkering around with my phone's software (Pocophone F1). Some of my favourite memories during university were during various events. Meeting new people, learning new things and being in different scenarios in different environments was always interesting.</p>
          <p
            class="ma-0"
          >I thank you for taking the time to check my website out. Please feel free to connect with me or contact me at any time. My contact details are at the bottom of the website.</p>
        </v-card>
      </v-col>
      <v-col cols="12">
        <v-card tile outlined>
          <v-sheet class="text-md-h1 text-h3 font-weight-medium text-center py-8">Experience</v-sheet>
          <v-card tile flat class="px-7 pb-7">
            <v-row no-gutters>
              <v-col cols="12" md="9" class="mx-auto">
                <v-card shaped outlined class="elevation-5 ma-5">
                  <v-card-title class="text-h5 font-weight-bold">Co-op</v-card-title>
                  <v-divider />
                  <v-card-text>
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
                              FYE
                              <span style="color:#fdbf57">LABS</span>
                            </span>
                            <v-spacer />Summer 2020
                          </v-card-title>
                          <v-card-text class="white pt-3">blablabla</v-card-text>
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
                    <v-timeline :dense="$vuetify.breakpoint.smAndDown" align-top>
                      <v-timeline-item
                        v-for="event in events"
                        :key="event.title"
                        :icon="(event.rawDate < new Date()) ? 'mdi-check' : ''"
                        :color="(event.rawDate < new Date()) ? 'red darken-4' : 'blue'"
                      >
                        <span slot="opposite">{{event.date}}</span>
                        <v-card
                          elevation="10"
                          :color="(event.rawDate < new Date()) ? 'red darken-4' : 'blue'"
                        >
                          <v-card-title
                            class="headline white--text"
                            style="word-break:normal"
                          >{{event.title}}</v-card-title>
                          <v-card-subtitle class="hidden-md-and-up white--text">{{event.date}}</v-card-subtitle>
                          <v-card-text class="white pt-3">{{event.text}}</v-card-text>
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
      <v-col cols="12" md="5" order-md="1">
        <v-card tile outlined height="100%" class="pa-5 px-md-10 d-flex align-center justify-end">
          <span class="text-h3 text-md-h1 font-weight-medium mx-lg-5">Projects</span>
        </v-card>
      </v-col>
      <v-col cols="12" md="7">
        <v-card tile outlined height="100%">
          <v-tabs grow :height="$vuetify.breakpoint.mdAndUp?'60':''">
            <v-tab>Professional</v-tab>
            <v-tab>Personal</v-tab>
            <!-- Use v-window or v-carousel -->
            <v-tab-item v-for="i in projects" :key="i.ii">
              <v-carousel>
                <v-carousel-item v-for="(color, i) in colors" :key="color">
                  <v-sheet :color="color" height="100%" tile>
                    <v-row class="fill-height" align="center" justify="center">
                      <div class="display-3">Slide {{ i + 1 }}</div>
                    </v-row>
                  </v-sheet>
                </v-carousel-item>
              </v-carousel>
            </v-tab-item>
          </v-tabs>
        </v-card>
      </v-col>
    </v-row>
    <v-footer dark color="#9a2a29" class="py-0">
      Thank you for checking out my website. Feel free to contact me through any of the following mediums!
      <v-row justify="center" class="text-center py-2 py-sm-6">
        <!-- Location Column -->
        <v-col cols="12" sm="4" lg="2">
          <span class="d-flex align-center justify-center text-h5 font-weight-medium mb-3">
            <v-icon size="28" class="pr-2">mdi-map-marker</v-icon>LOCATION
          </span>
          <span>
            McMaster University
            <br />1280 Main Street West
            <br />Hamilton, Ontario
            <br />L8S 4L8
          </span>
        </v-col>
        <!-- Location Column -->
        <v-divider inset class="mx-1 d-sm-none" />
        <!-- Find Us Column -->
        <v-col cols="12" sm="4" lg="3">
          <span class="d-flex align-center justify-center text-h5 font-weight-medium mb-3 mb-sm-6">
            <v-icon size="28" class="pr-2">mdi-share-variant</v-icon>FIND US
          </span>
          <v-btn icon large href="https://www.facebook.com/MacSumobots/" target="_blank">
            <v-icon>mdi-facebook</v-icon>
          </v-btn>
          <v-btn icon large href="https://www.instagram.com/mac_sumobot/" target="_blank">
            <v-icon>mdi-instagram</v-icon>
          </v-btn>

          <v-btn icon large href="https://github.com/macsumobot" target="_blank">
            <v-icon>mdi-github</v-icon>
          </v-btn>
          <v-btn
            icon
            large
            href="https://teams.microsoft.com/l/team/19%3ab8cea3145c7547b28582368f44cd6ac7%40thread.tacv2/conversations?groupId=0ccfac0a-7138-44e8-8d9a-209e92c0e3d4&tenantId=44376307-b429-42ad-8c25-28cd496f4772"
            target="_blank"
          >
            <v-icon>mdi-microsoft-teams</v-icon>
          </v-btn>
        </v-col>
        <!-- Find Us Column -->
        <v-divider inset class="mx-1 d-sm-none" />
        <!-- Conatct Column -->
        <v-col cols="12" sm="4" lg="2">
          <span class="d-flex align-center justify-center text-h5 font-weight-medium mb-3 mb-sm-6">
            <v-icon size="28" class="pr-2">mdi-email</v-icon>CONTACT
          </span>
          Email us at:
          <br />
          <a
            href="mailto:cr_sbot@mcmaster.ca"
            target="_blank"
            style="color:white"
          >cr_sbot@mcmaster.ca</a>
        </v-col>
        <!-- Conatct Column -->
      </v-row>
      <v-divider />
      <!-- Copyright Text -->

      <v-card-text class="pa-2 d-flex justify-center align-center pb-10 pb-sm-2">
        <v-icon class="px-1">mdi-copyright</v-icon>
        {{ new Date().getFullYear() }} — McMaster Sumobot
      </v-card-text>
      <!-- Copyright Text -->
    </v-footer>
  </v-container>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      experience: [
        { title: "Events", events: [{}] },
        { title: "Important Courses", events: [{}] },
      ],
      events: [
        {
          title: "Info Session 1",
          date: "15 September",
          rawDate: new Date("September 15, 2020"),
          text:
            "Our first informal info session, click here to watch the recording!",
          link: "https://www.instagram.com/p/CFLE7fXqSVl/",
        },
        {
          title: "Info Session 2",
          date: "25 September",
          rawDate: new Date("September 25, 2020"),
          text:
            "Our first formal info session, with finalised details for the winter!",
          link: "https://sumobot.ca/media/InfoSession.pdf",
        },
        {
          title: "Advanced Info Session",
          date: "10 October",
          rawDate: new Date("October 10, 2020"),
          text:
            "Details about the advanced competition, its rules and more information!",
          link: "https://sumobot.ca/media/Advanced_Competition.pdf",
        },
        {
          title: "Beginner Info Session",
          date: "24 October",
          rawDate: new Date("October 25, 2020"),
          text:
            "More details about the rules and the competition details for the beginner competition",
          link: "https://sumobot.ca/media/Beginner_Competition.pdf",
        },
        {
          title: "Workshop 1",
          date: "November 9, 6:30pm",
          rawDate: new Date("November 9, 2020"),
          text: "Workshop for Arduino and programming",
          link: "https://sumobot.ca/#/workshop",
        },
        {
          title: "Workshop 2",
          date: "November 19, 6:30pm",
          rawDate: new Date("November 19, 2020"),
          text: "Workshop for Motors and Deisgn",
          link: "https://sumobot.ca/#/workshop",
        },
        {
          title: "Workshop 3",
          date: "November 28, 5:30pm",
          rawDate: new Date("November 28, 2020"),
          text: "Workshop for Sensors",
          link: "https://sumobot.ca/#/workshop",
        },
        {
          title: "Final Info Session",
          date: "January 8 (TBD)",
          rawDate: new Date("January 8, 2021"),
          text: "One last info sessions for everyone",
        },
        {
          title: "Workshop 4",
          date: "January 13 (TBD)",
          rawDate: new Date("January 18, 2021"),
          text: "Workshop for CAD and final review",
          link: "https://sumobot.ca/#/workshop",
        },
        {
          title: "Workshop 5",
          date: "January 20 (TBD)",
          rawDate: new Date("January 20, 2021"),
          text: "Final Workshop",
          link: "https://sumobot.ca/#/workshop",
        },
        {
          title: "Showcase",
          date: "February 17-19 (TBD)",
          rawDate: new Date("February 20, 2021"),
          text: "Show off your bot at last!",
        },
      ],
      projects: [{ ii: 55 }, { ii: 66 }],
      colors: ["primary", "secondary", "yellow darken-2", "red", "orange"],
    };
  },
};
</script>

<style scoped>
.arrows {
  position: relative;
  height: 10vh;
  background-image: url("../assets/arrowgroup.png");
  background-size: contain;
  background-repeat: repeat-x;
}
</style>