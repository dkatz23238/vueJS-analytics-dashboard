<template>
  <v-card>
    <div class="pt-4 pr-4">
      <apexchart ref="barChart" type="bar" height="250" :options="options" :series="series"></apexchart>
    </div>
  </v-card>
</template>

<script>
export default {
  data: function() {
    return {
      options: {
        title: { text: "Bar Chart" },
        chart: {
          id: "barchart"
        },
        xaxis: {
          categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998]
        }
      },
      series: [
        {
          name: "Direct Hits",
          data: [30, 40, 45, 50, 49, 60, 70, 91]
        },
        {
          name: "Email Marketing",
          data: [30, 40, 45, 50, 49, 60, 70, 91].map(i => i + 10)
        }
      ]
    };
  }
};
</script>