<template>
  <div>
    <v-row class="mt-5">
      <v-col cols="4">
        <v-card flat>
          <v-card-title class="text-h3"> Hi, I'am Ahmed </v-card-title>
          <v-card-subtitle>Ready For Work</v-card-subtitle>
        </v-card>
        <v-btn rounded color="primary" class="mt-5" outlined large>
          <v-icon left size="30" class="mr-4">
            mdi-download-circle-outline
          </v-icon>
          Download Resume
        </v-btn>
      </v-col>
      <v-col cols="8">
        <v-card flat color="transparent">
          <v-card-text>
            <v-img
              src="../assets/programming.svg"
              aspect-ratio="1.7"
              contain
            ></v-img>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" class="ma-0">
        <ProjectsTable />
      </v-col>
    </v-row>
  </div>
</template>

<script>
import ProjectsTable from "../components/ProjectsTable.vue";
export default {
  name: "HomeView",
  components: { ProjectsTable },
};
</script>
