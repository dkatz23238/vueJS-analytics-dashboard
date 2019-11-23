
<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-contact-mail</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Contact</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="indigo" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>{{appName}}</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container fluid>
        <v-row>
          <v-col v-for="stat in cardStatistics" :key="stat.name" cols="3">
            <v-card>
              <v-list-item three-line>
                <v-list-item-content>
                  <div class="overline mb-1">{{stat.name}}</div>
                  <v-list-item-title class="headline mb-1">{{stat.value | toCurrency}}</v-list-item-title>
                  <v-list-item-subtitle>{{ stat.unit }}</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-card>
          </v-col>
        </v-row>

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
      </v-container>
    </v-content>
    <v-footer color="indigo" app>
      <span class="white--text">&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
import BarChart from "./components/BarChart";
import LineChart from "./components/LineChart";
import DataTable from "./components/DataTable";

export default {
  props: {
    source: String
  },
  components: { BarChart, LineChart, DataTable },
  data: () => ({
    drawer: null,
    appName: "Web Analytics Dashboard",
    cardStatistics: [
      { name: "Total Sales", value: 20000, unit: "Dollars" },
      { name: "Total Expenses", value: 178920, unit: "Dollars" },
      { name: "Avg. Conversion", value: 0.12743, unit: "Percent" },
      { name: "L.C.D", value: 12.89, unit: "Weeks" }
    ],
    valid: false,
    firstname: "",
    lastname: "",
    nameRules: [
      v => !!v || "Name is required",
      v => v.length <= 10 || "Name must be less than 10 characters"
    ],
    email: "",
    emailRules: [
      v => !!v || "E-mail is required",
      v => /.+@.+/.test(v) || "E-mail must be valid"
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
.spacing-playground .v-select .v-input__prepend-outer,
.spacing-playground .v-select .v-input__append-outer {
  margin-top: 0.55rem;
  margin-right: 0.2rem;
}
</style>