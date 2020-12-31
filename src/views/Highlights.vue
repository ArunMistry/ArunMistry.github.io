<template>
  <v-row no-gutters id="Highlights">
    <v-col cols="12" md="7" lg="8" xl="9">
      <v-card
        tile
        outlined
        height="100%"
        max-height="100vh"
        class="text-center d-flex flex-column profile"
        style="border: solid thin #e0e0e0"
      >
        <span class="text-h1 font-weight-bold pt-10 pb-3 transparent">Arun Mistry</span>
        <span class="text-h6 font-weight-medium mb-5">Welcome to my website</span>
        <span width="100%" class="d-flex flex-grow-1 align-end justify-center">
          <v-img src="../assets/me.png" contain />
        </span>
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
              Bachelor of Engineering (Co-op)
              <ul>
                <li>McMaster Univeristy</li>

                <li>Mechatronics Engineering II</li>
                <li>Expected Graduation: 2023</li>
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
          <v-btn
            x-large
            dark
            class="red darken-4 my-5 mx-2"
            href="/ArunMistryResume.pdf"
            target="_blank"
          >Resume</v-btn>
        </v-card>
      </v-card>
    </v-col>
  </v-row>
</template>

<style scoped>
.profile {
  background-image: linear-gradient(#fff 0%, rgba(0, 0, 0, 0) 100%),
    url("../assets/Circuit.png");
  background-repeat: repeat;
  background-size: 150px;
}
</style>