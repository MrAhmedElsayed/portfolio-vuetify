<template>
  <!-- todo: use toolbar -->
  <v-app>
    <NavbarComp />

    <v-main>
      <v-container>
        <v-scale-transition>
          <router-view></router-view>
        </v-scale-transition>
      </v-container>
    </v-main>
    <v-footer padless class="mt-5">
      <v-card class="flex" flat tile>
        <v-card-title class="primary--text tertiary">
          <h5 class="subheader ml-7">
            Get connected with me on social networks!
          </h5>

          <v-spacer></v-spacer>

          <v-btn v-for="icon in icons" :key="icon" class="mx-4" icon>
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-title>

        <v-card-text class="py-2 text-center">
          {{ new Date().getFullYear() }} — <strong>DEVO</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
import NavbarComp from "./components/NavbarComp.vue";
export default {
  name: "App",
  data: () => ({
    icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
  }),
  components: { NavbarComp },
};
</script>
