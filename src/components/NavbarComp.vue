<template>
  <!-- todo: use toolbar -->
  <v-app-bar app color="transparent" flat height="80px">
    <v-img
      class="ml-10"
      width="100"
      src="../assets/devo.png"
      alt="DEVO LOGO"
    ></v-img>

    <v-tabs class="d-flex justify-space-around">
      <v-tab to="/hello">Projects</v-tab>
      <v-tab>About Me</v-tab>
      <v-tab>Contact</v-tab>
    </v-tabs>

    <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
      transition="dialog-top-transition"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          rounded
          color="primary"
          outlined
          class="mr-10 d-flex justify-end"
          v-bind="attrs"
          v-on="on"
        >
          <v-icon
            :color="$vuetify.theme.dark ? 'orange' : 'secondary'"
            class="mr-2 pulse"
            >mdi-pac-man</v-icon
          >
          Hire Me
        </v-btn>
      </template>
      <v-card color="primary lighten-5" outlined>
        <v-card-title>
          <span class="text-h5">User Profile</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="6" md="4">
                <v-text-field label="Legal One*" required></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  label="Legal Two"
                  hint="example of helper text only on focus"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  label="Legal Three*"
                  hint="example of persistent helper text"
                  persistent-hint
                  required
                >
                </v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field label="Day*" required></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Night*"
                  type="text"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
          <small>*indicates required field</small>
        </v-card-text>
        <v-card-actions class="d-flex justify-space-around mb-4">
          <v-btn color="secondary darken-1" text @click="dialog = false">
            Close
          </v-btn>
          <v-btn color="primary darken-1" text @click="dialog = false">
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

    <v-checkbox
      ripple
      class="mt-4 mr-10"
      v-model="$vuetify.theme.dark"
      :color="$vuetify.theme.light ? 'accent' : 'orange'"
      off-icon="mdi-weather-night"
      on-icon="mdi-lightbulb-on"
    >
    </v-checkbox>
  </v-app-bar>
</template>

<script>
export default {
  name: "NavbarComp",
  data: () => ({
    dialog: false,
  }),
};
</script>

<style scoped>
.pulse {
  animation: heart-pulse 3s infinite;
}

@keyframes heart-pulse {
  0% {
    transform: scale(0);
  }

  50% {
    transform: scale(1.2);
  }

  70% {
    transform: scale(0.65);
  }

  100% {
    transform: scale(0);
  }
}
</style>
