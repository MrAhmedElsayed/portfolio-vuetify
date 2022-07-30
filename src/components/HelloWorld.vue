<template>
  <v-container>
    <v-card flat>
      <v-card-title class="text-center justify-center py-6">
        <h1 class="font-weight-bold text-h2">BASiL</h1>
      </v-card-title>

      <v-tabs v-model="tab" background-color="transparent" height="50" grow>
        <v-tab v-for="item in items" :key="item">
          {{ item }}
        </v-tab>
      </v-tabs>

      <v-tabs-items v-model="tab">
        <v-tab-item v-for="item in items" :key="item">
          <v-card flat>
            <v-card-text class="lekton-font">{{ text }}</v-card-text>
            <div class="text-center">
              <v-btn
                v-if="!chip1 && !chip2 && !chip3 && !chip4"
                close
                color="primary"
                dark
                @click="
                  (chip1 = true), (chip2 = true), (chip3 = true), (chip4 = true)
                "
              >
                Reset Chips
              </v-btn>

              <v-chip
                v-if="chip1"
                class="ma-2"
                close
                @click:close="chip1 = false"
              >
                Closable
              </v-chip>

              <v-chip
                v-if="chip2"
                class="ma-2"
                close
                color="red"
                text-color="white"
                @click:close="chip2 = false"
              >
                Remove
              </v-chip>

              <v-chip
                v-if="chip3"
                class="ma-2"
                close
                color="green"
                outlined
                @click:close="chip3 = false"
              >
                Success
              </v-chip>

              <v-chip
                v-if="chip4"
                class="ma-2"
                close
                color="orange"
                label
                outlined
                @click:close="chip4 = false"
              >
                Complete
              </v-chip>
            </div>
          </v-card>
        </v-tab-item>
      </v-tabs-items>

      <div class="text-center">
        <v-chip class="ma-2" label color="tertiary"> Label </v-chip>

        <v-chip class="ma-2" color="secondary" label text-color="white">
          <v-icon left> mdi-label </v-icon>
          Tags
        </v-chip>

        <v-chip class="ma-2" color="primary" label>
          <v-icon left> mdi-account-circle-outline </v-icon>
          John Leider
        </v-chip>

        <v-chip class="ma-2" close color="accent" label text-color="white">
          <v-icon left> mdi-twitter </v-icon>
          New Tweets
        </v-chip>
      </div>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({
    chip1: true,
    chip2: true,
    chip3: true,
    chip4: true,
    tab: null,
    items: ["Appetizers", "Entrees", "Deserts", "Cocktails"],
    text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
  }),
};
</script>

<style scoped>
.lekton-font {
  font-family: "Lekton" !important;
  font-weight: 700 !important;
}
</style>
