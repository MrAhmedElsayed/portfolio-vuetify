<template>
  <v-fab-transition>
    <v-btn dark fab outlined fixed bottom right color="secondary lighten-4">
      <v-progress-circular
        :rotate="360"
        :size="69"
        :width="5"
        :value="70"
        color="teal"
      >
        <v-icon color="secondary" size="32">mdi-chevron-double-up</v-icon>
      </v-progress-circular>
    </v-btn>
  </v-fab-transition>
</template>

<script>
export default {
  name: "BackToUp",
  data: () => ({
    scrollValue: 0,
  }),
};
</script>

<style></style>
