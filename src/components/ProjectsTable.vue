<template>
  <v-row>
    <v-col class="mt-4 mb-3" cols="12">
      <h1 class="text-center mb-3 display-2">Projects Portfolio</h1>
      <p class="text-center mb-7">
        Search projects by title or filter by category
      </p>
      <v-data-iterator
        :items="projects"
        :items-per-page.sync="itemsPerPage"
        :page.sync="page"
        :search="search"
        :sort-by="sortBy.toLowerCase()"
        :sort-desc="sortDesc"
        hide-default-footer
        class="mb-4"
      >
        <template v-slot:header>
          <v-toolbar flat class="mb-1">
            <v-text-field
              v-model="search"
              clearable
              hide-details
              prepend-inner-icon="mdi-magnify"
              label="Search"
            ></v-text-field>
            <template v-if="$vuetify.breakpoint.mdAndUp">
              <v-spacer></v-spacer>
              <v-select
                v-model="sortBy"
                hide-details
                :items="keys"
                prepend-inner-icon="mdi-magnify"
                label="Sort by"
              ></v-select>
            </template>
          </v-toolbar>
        </template>

        <template v-slot:default="props">
          <v-row>
            <v-col
              v-for="item in props.items"
              :key="item.id"
              cols="12"
              sm="6"
              md="4"
              lg="4"
            >
              <!-- Replace Card-->
              <v-hover v-slot="{ hover }">
                <v-card
                  class="rounded-xl mt-3"
                  outlined
                  :elevation="hover ? 12 : 0"
                  :class="{ 'on-hover': hover }"
                >
                  <v-img :src="item.image" :alt="item.title" height="300px">
                    <v-row class="fill-height">
                      <v-card-title>
                        <v-btn
                          dark
                          icon
                          class="mr-4"
                          :class="{ 'show-btns': hover }"
                          :color="transparent"
                        >
                          <v-icon
                            :class="{ 'show-btns': hover }"
                            :color="transparent"
                            size="27"
                            >mdi-chevron-double-left</v-icon
                          >
                        </v-btn>

                        <v-spacer></v-spacer>

                        <v-btn
                          icon
                          class="mr-4"
                          :class="{ 'show-btns': hover }"
                          :color="transparent"
                        >
                          <v-icon
                            :class="{ 'show-btns': hover }"
                            :color="transparent"
                            >mdi-heart-plus</v-icon
                          >
                        </v-btn>

                        <v-btn
                          icon
                          :class="{ 'show-btns': hover }"
                          :color="transparent"
                        >
                          <v-icon
                            :class="{ 'show-btns': hover }"
                            :color="transparent"
                            >mdi-github</v-icon
                          >
                        </v-btn>
                      </v-card-title>

                      <v-spacer></v-spacer>

                      <v-card-title
                        class="mx-auto my-auto secondary--text bold"
                      >
                        <div class="font-weight-bold headline">
                          {{ item.title }}
                        </div>
                      </v-card-title>
                    </v-row>
                  </v-img>

                  <v-card-text class="text-center">
                    <p class="my-2 text-subtitle-1">{{ item.type }}</p>
                  </v-card-text>

                  <v-divider class="mx-4"></v-divider>

                  <v-card-text>
                    <v-chip-group active-class="primary--text" column>
                      <v-chip>Vue</v-chip>
                      <v-chip>Django</v-chip>
                      <v-chip>AWS</v-chip>
                      <v-chip>Cookiecutter</v-chip>
                      <v-chip>Django Rest Api</v-chip>
                      <v-chip>Vuetify</v-chip>
                    </v-chip-group>
                  </v-card-text>
                </v-card>
              </v-hover>
              <!-- Replace Card-->
            </v-col>
          </v-row>
        </template>

        <template v-slot:footer>
          <v-row class="mt-2 ml-2" align="center" justify="center">
            <span class="grey--text">Items per page</span>
            <v-menu offset-y>
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  dark
                  text
                  color="primary"
                  class="ml-2"
                  v-bind="attrs"
                  v-on="on"
                >
                  {{ itemsPerPage }}
                  <v-icon>mdi-chevron-down</v-icon>
                </v-btn>
              </template>
              <v-list>
                <v-list-item
                  v-for="(number, index) in itemsPerPageArray"
                  :key="index"
                  @click="updateItemsPerPage(number)"
                >
                  <v-list-item-title>{{ number }}</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-menu>

            <v-spacer></v-spacer>

            <span class="mr-4 grey--text">
              Page {{ page }} of {{ numberOfPages }}
            </span>
            <v-btn
              fab
              small
              color="accent"
              outlined
              class="mr-1"
              @click="formerPage"
            >
              <v-icon>mdi-chevron-left</v-icon>
            </v-btn>
            <v-btn
              fab
              small
              color="accent"
              outlined
              class="ml-3 mr-3"
              @click="nextPage"
            >
              <v-icon>mdi-chevron-right</v-icon>
            </v-btn>
          </v-row>
        </template>
      </v-data-iterator>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "ProjectsTable",
  data: () => ({
    itemsPerPageArray: [3, 4, 8, 12],
    search: "",
    filter: {},
    sortDesc: false,
    page: 1,
    itemsPerPage: 3,
    sortBy: "name",
    keys: ["Title", "Type"],
    projects: [
      {
        id: "1",
        title: "Phoenix Digital Agency",
        image: require("../assets/images/mobile-project-1.jpg"),
        type: "mobile project",
        github: "https://github.com/",
      },
      {
        id: "2",
        title: "Uber Social App",
        image: require("../assets/images/mobile-project-2.jpg"),
        type: "mobile project",
        github: "https://github.com/",
      },
      {
        id: "3",
        title: "Cloud Storage Platform",
        image: require("../assets/images/ui-project-1.jpg"),
        type: "ui project",
        github: "https://github.com/",
      },
      {
        id: "4",
        title: "Project Management UI",
        image: require("../assets/images/ui-project-2.jpg"),
        type: "ui project",
        github: "https://github.com/",
      },
      {
        id: "5",
        title: "Apple Design System",
        image: require("../assets/images/web-project-1.jpg"),
        type: "web project",
        github: "https://github.com/",
      },
      {
        id: "6",
        title: "Google Health Platform",
        image: require("../assets/images/web-project-2.jpg"),
        type: "web project",
        github: "https://github.com/",
      },
    ],
    transparent: "rgba(255, 255, 255, 0)",
  }),
  computed: {
    numberOfPages() {
      return Math.ceil(this.projects.length / this.itemsPerPage);
    },
    filteredKeys() {
      return this.keys.filter((key) => key !== "Name");
    },
  },
  methods: {
    nextPage() {
      if (this.page + 1 <= this.numberOfPages) this.page += 1;
    },
    formerPage() {
      if (this.page - 1 >= 1) this.page -= 1;
    },
    updateItemsPerPage(number) {
      this.itemsPerPage = number;
    },
  },
};
</script>

<style scoped>
.v-card {
  transition: opacity 0.4s ease-in-out;
}

.v-card:not(.on-hover) {
  opacity: 0.6;
}

.show-btns {
  color: rgba(255, 255, 255, 1) !important;
}
</style>
