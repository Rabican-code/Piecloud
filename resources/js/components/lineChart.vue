<script>
import Vue from 'vue';
import Chart from 'chart.js';

export default {
  name: 'LineChart',
  data() {
    return {
      chartData: {
        labels: ['January', 'February', 'March', 'April', 'May'],
        datasets: [
          {
            label: 'Sales',
            data: [100, 200, 300, 400, 500],
            borderColor: '#f87979',
            backgroundColor: '#f87979',
          },
        ],
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
      },
    };
  },
  mounted() {
    new Chart(this.$refs.chart, {
      data: this.chartData,
      options: this.options,
    });
  },
};
</script>

<template>
  <div id="chart"></div>
</template>
