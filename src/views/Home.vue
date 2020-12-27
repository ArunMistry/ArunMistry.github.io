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
        </v-card>
      </v-col>
      <v-col cols="12" md="5" xl="4">
        <v-card tile outlined flat height="100%">
          <v-card flat class="pa-5 pa-md-8 text-h3 font-weight-medium">Highlights</v-card>
          <v-divider />
          <v-card flat height="90%" class="pa-5">
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
      <v-card tile outlined width="100%" class="arrows elevation-2">
        <v-sheet height="100%" width="15" style="position:absolute; right:0" color="white" />
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
        <v-card
          tile
          outlined
          class="text-md-h1 text-h3 font-weight-medium text-center pt-5 pb-10"
        >Experience</v-card>
        <v-card tile outlined class="pa-5">
          <v-row no-gutters>
            <v-col cols="12">
              <v-card shaped outlined class="elevation-5 ma-5">
                <v-card-title>Co-op</v-card-title>
                <v-divider />
                <v-card-text>efkbk</v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12" md="6" v-for="item in experience" :key="item.title">
              <v-card shaped outlined class="elevation-5 ma-5">
                <v-card-title>{{item.title}}</v-card-title>
                <v-divider />
                <v-card-text>efkbk</v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
      <v-col cols="12">
        <v-card tile outlined>
          <h1>Projects</h1>
          <v-tabs grow :vertical="$vuetify.breakpoint.mdAndUp">
            <v-tab>Professional</v-tab>
            <v-tab>Personal</v-tab>
            <!-- Use v-window or v-carousel -->
            <v-tab-item>dshibferlhwifv</v-tab-item>
            <v-tab-item>wefgteber</v-tab-item>
          </v-tabs>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
  <!-- <v-timeline :dense="$vuetify.breakpoint.xsOnly" scrollable align-top>
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
                <v-card-title class="headline white--text" style="word-break:normal">{{event.title}}</v-card-title>
                <v-card-subtitle class="hidden-sm-and-up white--text">{{event.date}}</v-card-subtitle>
                <v-card-text class="white pt-3">{{event.text}}</v-card-text>
              </v-card>
            </v-timeline-item>
  </v-timeline>-->
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
    };
  },
};
</script>

<style scoped>
.arrows {
  position: relative;
  height: 10vh;
  background-image: url("../assets/Trial1.png");
  background-size: contain;
  background-repeat: repeat-x;
}
</style>