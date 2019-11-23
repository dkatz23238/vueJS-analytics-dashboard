
<template>
  <v-app id="inspire">
    <Navigation :appName="appName"></Navigation>

    <v-content>
      <v-container fluid>
        <Statistics :cardStatistics="cardStatistics"></Statistics>
        <v-row>
          <v-col col="6">
            <BarChart></BarChart>
          </v-col>
          <v-col col="6">
            <LineChart></LineChart>
          </v-col>
        </v-row>

        <v-row>
          <v-col>
            <DataTable></DataTable>
          </v-col>
        </v-row>

        <Footer></Footer>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import BarChart from "./components/BarChart";
import LineChart from "./components/LineChart";
import DataTable from "./components/DataTable";
import Navigation from "./components/Navigation";
import Footer from "./components/Footer";
import Statistics from "./components/Statistics";
export default {
  props: {
    source: String
  },
  components: {
    BarChart,
    LineChart,
    DataTable,
    Navigation,
    Statistics,
    Footer
  },
  data: () => ({
    drawer: null,
    appName: "Web Analytics Dashboard",
    cardStatistics: [
      { name: "Total Sales", value: 20000, unit: "Dollars" },
      { name: "Total Expenses", value: 178920, unit: "Dollars" },
      { name: "Avg. Conversion", value: 0.12743, unit: "Percent" },
      { name: "L.C.D", value: 12.89, unit: "Weeks" }
    ]
  }),
  filters: {
    toCurrency: value => {
      return Number(value.toFixed(2)).toLocaleString();
    }
  }
};
</script>

<style scoped>
</style>