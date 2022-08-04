<template>
  <!-- todo: use toolbar -->
  <v-app>
    <NavbarComp />

    <v-main>
      <v-container>
        <v-scale-transition>
          <router-view></router-view>
        </v-scale-transition>
        <BackToUp />
      </v-container>
    </v-main>
    <v-footer dark padless class="mt-5">
      <v-card flat tile class="flex tertiary primary--text text-center">
        <v-card-text>
          <v-btn
            v-for="icon in icons"
            :key="icon"
            class="mx-4 primary--text"
            icon
          >
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-card-text class="primary--text pt-0">
          Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet.
          Mauris cursus commodo interdum. Praesent ut risus eget metus luctus
          accumsan id ultrices nunc. Sed at orci sed massa.
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="primary--text">
          {{ new Date().getFullYear() }} — <strong>DEVO</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
import NavbarComp from "./components/NavbarComp.vue";
import BackToUp from "./components/BackToUp.vue";
export default {
  name: "App",
  // add scroll functionality: https://vuetifyjs.com/en/features/scrolling/#usage
  data: () => ({
    icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
  }),
  components: { NavbarComp, BackToUp },
};
</script>
