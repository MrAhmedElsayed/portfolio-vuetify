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
              <v-card
                class="my-12 rounded-xl"
                outlined
                style="position: relative"
              >
                <v-img
                  lazy-src="https://picsum.photos/id/11/100/60"
                  height="300"
                  :src="item.image"
                  alt="img"
                >
                  <template v-slot:placeholder>
                    <v-row
                      class="fill-height ma-0"
                      align="center"
                      justify="center"
                    >
                      <v-progress-circular
                        indeterminate
                        color="grey lighten-5"
                      ></v-progress-circular>
                    </v-row>
                  </template>
                </v-img>

                <v-icon
                  size="40"
                  color="secondary light-4"
                  style="position: absolute; top: 10px; right: 10px"
                  >mdi-github</v-icon
                >

                <v-card-title class="d-flex justify-center">
                  <span>{{ item.title }}</span>
                  <v-icon class="mt-1" right size="25" color="secondary"
                    >mdi-chevron-double-right</v-icon
                  >
                </v-card-title>

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
            <v-btn fab small color="accent" class="mr-1" @click="formerPage">
              <v-icon>mdi-chevron-left</v-icon>
            </v-btn>
            <v-btn fab small color="accent" class="ml-3 mr-3" @click="nextPage">
              <v-icon>mdi-chevron-right</v-icon>
            </v-btn>
          </v-row>
        </template>
      </v-data-iterator>
    </v-col>
    <v-col cols="12">
      <v-card max-width="375" class="mx-auto">
        <v-img
          src="https://cdn.vuetifyjs.com/images/lists/ali.png"
          height="300px"
          dark
        >
          <v-row class="fill-height">
            <v-card-title>
              <v-btn dark icon>
                <v-icon>mdi-chevron-left</v-icon>
              </v-btn>

              <v-spacer></v-spacer>

              <v-btn dark icon class="mr-4">
                <v-icon>mdi-pencil</v-icon>
              </v-btn>

              <v-btn dark icon>
                <v-icon>mdi-dots-vertical</v-icon>
              </v-btn>
            </v-card-title>

            <v-spacer></v-spacer>

            <v-card-title class="white--text pl-12 pt-12">
              <div class="text-h4 pl-12 pt-12">Ali Conners</div>
            </v-card-title>
          </v-row>
        </v-img>

        <v-list two-line>
          <v-list-item>
            <v-list-item-icon>
              <v-icon color="indigo"> mdi-phone </v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>(650) 555-1234</v-list-item-title>
              <v-list-item-subtitle>Mobile</v-list-item-subtitle>
            </v-list-item-content>

            <v-list-item-icon>
              <v-icon>mdi-message-text</v-icon>
            </v-list-item-icon>
          </v-list-item>

          <v-list-item>
            <v-list-item-action></v-list-item-action>

            <v-list-item-content>
              <v-list-item-title>(323) 555-6789</v-list-item-title>
              <v-list-item-subtitle>Work</v-list-item-subtitle>
            </v-list-item-content>

            <v-list-item-icon>
              <v-icon>mdi-message-text</v-icon>
            </v-list-item-icon>
          </v-list-item>

          <v-divider inset></v-divider>

          <v-list-item>
            <v-list-item-icon>
              <v-icon color="indigo"> mdi-email </v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>aliconnors@example.com</v-list-item-title>
              <v-list-item-subtitle>Personal</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <v-list-item>
            <v-list-item-action></v-list-item-action>

            <v-list-item-content>
              <v-list-item-title>ali_connors@example.com</v-list-item-title>
              <v-list-item-subtitle>Work</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <v-divider inset></v-divider>

          <v-list-item>
            <v-list-item-icon>
              <v-icon color="indigo"> mdi-map-marker </v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>1400 Main Street</v-list-item-title>
              <v-list-item-subtitle>Orlando, FL 79938</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-card>
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
    items: [
      {
        name: "Frozen Yogurt",
        calories: 159,
        fat: 6.0,
        carbs: 24,
        protein: 4.0,
        sodium: 87,
        calcium: "14%",
        iron: "1%",
      },
      {
        name: "Ice cream sandwich",
        calories: 237,
        fat: 9.0,
        carbs: 37,
        protein: 4.3,
        sodium: 129,
        calcium: "8%",
        iron: "1%",
      },
      {
        name: "Eclair",
        calories: 262,
        fat: 16.0,
        carbs: 23,
        protein: 6.0,
        sodium: 337,
        calcium: "6%",
        iron: "7%",
      },
      {
        name: "Cupcake",
        calories: 305,
        fat: 3.7,
        carbs: 67,
        protein: 4.3,
        sodium: 413,
        calcium: "3%",
        iron: "8%",
      },
    ],
  }),
  computed: {
    numberOfPages() {
      return Math.ceil(this.items.length / this.itemsPerPage);
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
