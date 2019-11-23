<template>
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
</template>

<script>
export default {
  name: "Statistics",
  props: {
    cardStatistics: Array
  },
  data: function() {
    return {};
  }
};
</script>