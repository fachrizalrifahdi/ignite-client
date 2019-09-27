<template>
  <v-container>
    <v-layout text-center wrap>
      <v-flex xs12>
        <v-card>
          <v-card-title>
            Test
            <div class="flex-grow-1"></div>
            <v-text-field
              v-model="search"
              append-icon="search"
              label="Search"
              single-line
              hide-details
            ></v-text-field>
          </v-card-title>
          <v-data-table :headers="headers" :items="ignites" :search="search"></v-data-table>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      search: "",
      headers: [
        {
          text: "Location",
          value: "location"
        },
        { text: "T", value: "t_today" },
        { text: "R", value: "r_today" },
        { text: "A", value: "a_today" },
        { text: "T", value: "t_month" },
        { text: "R", value: "r_month" },
        { text: "A", value: "a_month" },
        { text: "T", value: "t_year" },
        { text: "R", value: "r_year" },
        { text: "A", value: "a_year" },
        {
          text: "Region",
          value: "region"
        }
      ],
      ignites: []
    };
  },
  mounted() {
    axios
      .get("http://127.0.0.1:3333/api/v1/ignites")
      .then(response => {
        this.ignites = response.data;
        this.loading = false;
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>