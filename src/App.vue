<template>
  <v-app>
    <NavbarComp />

    <v-main>
      <v-container>
        <v-scale-transition>
          <router-view></router-view>
        </v-scale-transition>
      </v-container>
    </v-main>
    <v-footer app>
      <!-- -->
    </v-footer>
  </v-app>
</template>

<script>
import NavbarComp from "./components/NavbarComp.vue";
export default {
  name: "App",
  data: () => ({
    //
  }),
  components: { NavbarComp },
};
</script>
