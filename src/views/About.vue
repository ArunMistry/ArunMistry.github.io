<template>
  <v-row no-gutters>
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
          <p>Hi, my name is Arun Mistry, and I am a Mechatronics Engineering II Student in McMaster Univeristy. I am in my second year, and plan on graduating in 2023-24. My ambition is to work in the field of robotics! Robotics involves building, coding, debugging, problem solving, and a lot more, all of which I find very interesting.</p>
          <p>I would consider myself to be a tinkerer, breaking down things to understand how they work, and then putting them back together. This ties into my interest in robotics. Some of my hobbies include reading, cooking, and hiking!</p>
          <p
            class="ma-0"
          >I thank you for taking the time to check my website out! Please feel free to connect with me or contact me at any time, my contact details are at the bottom of the website!</p>
        </span>
      </v-card>
    </v-col>
    <!-- Add skillset and achievements -->
  </v-row>
</template>

<script>
export default {
  data() {
    return {};
  },
};
</script>
