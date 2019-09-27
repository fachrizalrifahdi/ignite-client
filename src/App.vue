<template>
  <v-app>
    <v-content>
      <DataTable />
    </v-content>
  </v-app>
</template>

<script>
import DataTable from "./components/DataTable";

export default {
  name: "App",
  components: {
    DataTable
  },
  data: () => ({
    //
  })
};
</script>
